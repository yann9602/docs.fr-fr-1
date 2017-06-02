---
title: "Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un contr&#244;le&#160;Win32 dans&#160;WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "héberger un contrôle Win32 dans WPF"
  - "code Win32, interopérabilité WPF"
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un contr&#244;le&#160;Win32 dans&#160;WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un environnement riche pour créer des applications.  Toutefois, lorsque vous vous appuyez massivement sur du code [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], il peut être plus efficace de réutiliser au moins une partie de ce code dans votre application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], plutôt que de le réécrire entièrement.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un mécanisme simple pour l'hébergement d'une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dans une page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Cette rubrique, [Hébergement d'un contrôle ListBox Win32 dans Windows Presentation Foundation, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159998), vous présente une application qui héberge un contrôle de zone de liste [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  Cette procédure générale peut être étendue à l'hébergement de toute fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
   
  
<a name="requirements"></a>   
## Configuration requise  
 Cette rubrique suppose que vous avez des connaissances de base en matière de programmation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  Pour une présentation générale de la programmation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Mise en route](../../../../docs/framework/wpf/getting-started/index.md).  Pour une présentation de la programmation [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], consultez les divers manuels qui traitent de ce sujet, notamment *La programmation Windows* de Charles Petzold.  
  
 Comme l'exemple qui accompagne cette rubrique est implémenté dans [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], il utilise [!INCLUDE[TLA#tla_pinvoke](../../../../includes/tlasharptla-pinvoke-md.md)] pour accéder à l'[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  Une certaine familiarisation avec [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] est utile, mais pas essentielle.  
  
> [!NOTE]
>  Cette rubrique inclut des exemples de code de l'exemple associé.  Toutefois, il n'inclut pas l'exemple de code complet pour une meilleure lisibilité.  Vous pouvez obtenir ou consulter le code complet de [Hébergement d'un contrôle ListBox Win32 dans Windows Presentation Foundation, exemple](http://go.microsoft.com/fwlink/?LinkID=159998).  
  
<a name="basic_procedure"></a>   
## La procédure de base :  
 Cette section décrit la procédure de base pour héberger une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] sur une page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Les sections restantes reprennent chaque étape en détail.  
  
 La procédure d'hébergement de base est :  
  
1.  Implémenter une page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour héberger la fenêtre.  Une technique consiste à créer un élément <xref:System.Windows.Controls.Border> pour réserver une section de la page pour la fenêtre hébergée.  
  
2.  Implémenter une classe pour héberger le contrôle qui hérite de <xref:System.Windows.Interop.HwndHost>.  
  
3.  Dans cette classe hôte, substituez le membre de classe <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> <xref:System.Windows.Interop.HwndHost>.  
  
4.  Créer la fenêtre hébergée comme un enfant de la fenêtre qui contient la page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Bien que la programmation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conventionnelle n'ait pas besoin de l'utiliser explicitement, la page d'hébergement est une fenêtre avec un handle \(HWND\).  Vous recevez la page HWND via le paramètre `hwndParent` de la méthode <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>.  La fenêtre hébergée doit être créée comme un enfant de ce HWND.  
  
5.  Une fois que vous avez créé la fenêtre hôte, retournez le HWND de la fenêtre hébergée.  Si vous souhaitez héberger un ou plusieurs contrôles [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], vous créez en général une fenêtre hôte comme un enfant du HWND et faites des contrôles les enfants de cette fenêtre d'hôte.  L'encapsulation des contrôles dans une fenêtre hôte offre un moyen simple permettant à votre page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de recevoir des notifications des contrôles, qui traitent de quelques problèmes [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] particuliers avec les notifications à travers la limite HWND.  
  
6.  Gérer les messages sélectionnés envoyés à la fenêtre hôte, telles que les notifications des contrôles enfants.  Il y a deux manières pour effectuer cette opération :  
  
    -   Si vous préférez gérer des messages dans votre classe d'hébergement, substituez la méthode <xref:System.Windows.Interop.HwndHost.WndProc%2A> de la classe <xref:System.Windows.Interop.HwndHost>.  
  
    -   Si vous préférez que le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gère les messages, gérez la classe <xref:System.Windows.Interop.HwndHost> d'événement <xref:System.Windows.Interop.HwndHost.MessageHook> dans votre code\-behind.  Cet événement se produit pour chaque message reçu par la fenêtre hébergée.  Si vous choisissez cette option, vous devez quand même substituer <xref:System.Windows.Interop.HwndHost.WndProc%2A>, mais vous n'avez besoin que d'une implémentation minime.  
  
7.  Substituez les méthodes <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> et <xref:System.Windows.Interop.HwndHost.WndProc%2A> de <xref:System.Windows.Interop.HwndHost>.  Vous devez substituer ces méthodes pour satisfaire le contrat <xref:System.Windows.Interop.HwndHost>, mais vous pouvez ne devoir fournir qu'une implémentation minime.  
  
8.  Dans votre fichier code\-behind, créez une instance de la classe d'hébergement de contrôle et faites\-en un enfant de l'élément <xref:System.Windows.Controls.Border> prévu pour héberger la fenêtre.  
  
9. Communiquez avec la fenêtre hébergée en lui envoyant des messages [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] et en gérant des messages à partir de ses fenêtres enfants, telles que les notifications envoyées par des contrôles.  
  
<a name="page_layout"></a>   
## Implémenter la Présentation Page  
 La présentation pour la page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui héberge le contrôle ListBox se compose de deux régions.  Le côté gauche de la page héberge plusieurs contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui fournissent une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] vous permettant de manipuler le contrôle [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  Le coin supérieur droit de la page comporte une zone carrée pour le contrôle ListBox hébergé.  
  
 Le code pour implémenter cette présentation est assez simple.  L'élément racine est un <xref:System.Windows.Controls.DockPanel> qui a deux éléments enfants.  Le premier est un élément <xref:System.Windows.Controls.Border> qui héberge le contrôle ListBox.  Il occupe un carré de 200x200 dans le coin supérieur droit de la page.  Le second est un élément <xref:System.Windows.Controls.StackPanel> qui contient un jeu de contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui affichent des informations et vous permettent de manipuler le contrôle ListBox en définissant des propriétés d'interopérabilité exposées.  Pour chacun des éléments qui sont enfants du <xref:System.Windows.Controls.StackPanel>, consultez les documents de référence pour les divers éléments utilisés pour plus d'informations sur ce que sont ou font ces éléments, ceux\-ci sont répertoriés dans l'exemple de code ci\-dessous mais ne seront pas expliqués ici \(le modèle d'interopérabilité de base n'a besoin d'aucun d'entre eux, ils sont fournis pour ajouter un peu d'interactivité à l'exemple\).  
  
 [!code-xml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## Implémenter une classe pour héberger le contrôle Microsoft Win32  
 Le cœur de cet exemple est la classe qui héberge effectivement le contrôle, ControlHost.cs.  Il hérite de <xref:System.Windows.Interop.HwndHost>.  Le constructeur prend deux paramètres, hauteur et largeur, qui correspondent à la hauteur et à la largeur de l'élément <xref:System.Windows.Controls.Border> qui héberge le contrôle ListBox.  Ces valeurs sont utilisées ultérieurement pour garantir que la taille du contrôle correspond à l'élément <xref:System.Windows.Controls.Border>.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Il y a également un jeu de constantes.  Ces constantes proviennent pour l'essentiel de Winuser.h, et vous permettent d'utiliser des noms conventionnels lors de l'appel de fonctions [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### Substituer BuildWindowCore pour créer la fenêtre Microsoft Win32  
 Vous substituez cette méthode pour créer la fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] qui sera hébergée par la page et qui établira la connexion entre la fenêtre et la page.  Comme cet exemple implique l'hébergement d'un contrôle ListBox, deux fenêtres sont créées.  La première est la fenêtre hébergée effectivement par la page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Le contrôle ListBox est créé comme un enfant de cette fenêtre.  
  
 La raison pour cette approche est de simplifier le processus de réception des notifications du contrôle.  La classe <xref:System.Windows.Interop.HwndHost> vous permet de traiter des messages envoyés à la fenêtre qu'elle héberge.  Si vous hébergez un contrôle [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] directement, vous recevez les messages envoyés à la boucle de messages interne du contrôle.  Vous pouvez afficher le contrôle et lui envoyer des messages, mais vous ne recevez pas les notifications que le contrôle envoie à sa fenêtre parente.  Cela signifie, entre autres choses, que vous n'avez aucun moyen de détecter quand l'utilisateur interagit avec le contrôle.  Créez à la place une fenêtre hôte et faites du contrôle un enfant de cette fenêtre.  Cela vous permet de traiter les messages pour la fenêtre hôte y compris les notifications qui lui sont envoyées par le contrôle.  Par souci de commodité, comme la fenêtre hôte n'est guère plus qu'un simple wrapper pour le contrôle, le package sera connu sous le nom de contrôle ListBox.  
  
<a name="create_the_window_and_listbox"></a>   
#### Créer la fenêtre hôte et le contrôle ListBox  
 Vous pouvez utiliser [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] pour créer une fenêtre hôte pour le contrôle en créant et en enregistrant une classe de fenêtres, etc.  Toutefois, une approche beaucoup plus simple consiste à créer une fenêtre avec la classe de fenêtres "static" prédéfinie.  Cela vous fournit la procédure de fenêtre dont vous avez besoin pour recevoir des notifications du contrôle et requiert un codage minime.  
  
 Le HWND du contrôle est exposé via une propriété en lecture seule, afin que la page hôte puisse l'utiliser pour envoyer des messages au contrôle.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 Le contrôle ListBox est créé comme un enfant de la fenêtre hôte.  Les valeurs de hauteur et de largeur des deux fenêtres sont celles valeurs passées au constructeur, traité ci\-dessus.  Cela garantit que la taille de la fenêtre hôte et du contrôle est identique à la zone réservée sur la page.  Après avoir créé les fenêtres, l'exemple retourne un objet <xref:System.Runtime.InteropServices.HandleRef> qui contient le HWND de la fenêtre hôte.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### Implémenter DestroyWindow et WndProc  
 En plus de <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, vous devez substituer les méthodes <xref:System.Windows.Interop.HwndHost.WndProc%2A> et <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> du <xref:System.Windows.Interop.HwndHost>.  Dans cet exemple, les messages pour le contrôle sont gérés par le gestionnaire <xref:System.Windows.Interop.HwndHost.MessageHook>, de sorte que l'implémentation de <xref:System.Windows.Interop.HwndHost.WndProc%2A> et <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> est minime.  Dans le cas de <xref:System.Windows.Interop.HwndHost.WndProc%2A>, affectez à `handled` la valeur `false` pour indiquer que le message n'a pas été géré et retourner 0.  Pour <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, détruisez simplement la fenêtre.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## Héberger le contrôle dans la page  
 Pour héberger le contrôle dans la page, vous créez tout d'abord une nouvelle instance de la classe `ControlHost`.  Passez la hauteur et la largeur de l'élément de bordure qui contient le contrôle \(`ControlHostElement`\) au constructeur `ControlHost`.  Cela garantit que la Zone de liste est dimensionnée correctement.  Vous hébergez ensuite le contrôle dans la page en assignant l'objet `ControlHost` à la propriété <xref:System.Windows.Controls.Decorator.Child%2A> de l'hôte <xref:System.Windows.Controls.Border>.  
  
 L'exemple joint un gestionnaire à l'événement <xref:System.Windows.Interop.HwndHost.MessageHook> du `ControlHost` pour recevoir des messages du contrôle.  Cet événement est déclenché pour chaque message envoyé à la fenêtre hébergée.  Dans ce cas, ce sont les messages envoyés à la fenêtre qui encapsulent le contrôle ListBox réel, y compris les notifications du contrôle.  L'exemple appelle SendMessage pour obtenir des informations du contrôle et modifier son contenu.  Les détails de la façon dont la page communique avec le contrôle sont traités dans la section suivante.  
  
> [!NOTE]
>  Remarquez qu'il existe deux déclarations [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] pour SendMessage.  Ceci est nécessaire parce que l'un utilise le paramètre `wParam` pour passer une chaîne et que l'autre l'utilise pour passer un entier.  Vous avez besoin d'une déclaration séparée pour chaque signature afin de garantir que les données sont canalisées correctement.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## Implémenter la communication entre le contrôle et la page  
 Vous manipulez le contrôle en lui envoyant des messages [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)].  Le contrôle vous notifie lorsque l'utilisateur interagit avec lui en envoyant des notifications à sa fenêtre hôte.  L'exemple [Hébergement d'un contrôle ListBox Win32 dans Windows Presentation Foundation, exemplehttp:\/\/go.microsoft.com\/fwlink\/?LinkID\=159998](http://go.microsoft.com/fwlink/?LinkID=159998) inclut une interface utilisateur qui fournit plusieurs exemples montrant comment effectuer les opérations suivantes :  
  
-   Ajouter un élément à la liste.  
  
-   Supprimer l'élément sélectionné dans la liste  
  
-   Afficher le texte de l'élément actuellement sélectionné.  
  
-   Afficher le nombre d'éléments de la liste.  
  
 L'utilisateur peut également sélectionner un élément dans la zone de liste en cliquant dessus, tout comme il le ferait pour une application [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] conventionnelle.  Les données affichées sont mises à jour chaque fois que l'utilisateur modifie l'état de la zone de liste en sélectionnant, en ajoutant, ou en rajoutant un élément.  
  
 Pour rajouter des éléments, envoyez un message LB\_ADDSTRING à la zone de liste.  Pour supprimer des éléments, envoyez LB\_GETCURSEL pour obtenir l'index de la sélection actuelle, puis LB\_DELETESTRING pour supprimer l'élément.  L'exemple envoie également LB\_GETCOUNT et utilise la valeur retournée pour mettre à jour l'affichage qui montre le nombre d'éléments.  Ces deux instances de SendMessage utilisent l'une des déclarations [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] traitées dans la section précédente.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Lorsque l'utilisateur sélectionne un élément ou modifie sa sélection, le contrôle notifie la fenêtre hôte en lui envoyant un message WM\_COMMAND, qui déclenche l'événement <xref:System.Windows.Interop.HwndHost.MessageHook> pour la page.  Le gestionnaire reçoit les mêmes informations que la procédure de fenêtre principale de la fenêtre hôte.  Il passe également une référence à une valeur booléenne, `handled`.  Vous définissez `handled` à `true` pour indiquer que vous avez géré le message et qu'aucun traitement supplémentaire n'est requis.  
  
 WM\_COMMAND est envoyé pour diverses raisons, de sorte que vous devez examiner l'ID de notification pour déterminer s'il s'agit d'un événement que vous souhaitez gérer.  L'ID est contenu dans le mot de poids fort du paramètre `wParam`.  Comme [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] n'a pas de macro HIWORD, l'exemple utilise des opérateurs au niveau du bit pour extraire l'ID.  Si l'utilisateur a fait ou modifié sa sélection, l'ID sera LBN\_SELCHANGE.  
  
 Lorsque LBN\_SELCHANGE est reçu, l'exemple récupère l'index de l'élément sélectionné en envoyant un message LB\_GETCURSEL au contrôle.  Pour obtenir le texte, vous devez d'abord créer un <xref:System.Text.StringBuilder>.  Vous envoyez ensuite un message LB\_GETTEXT au contrôle.  Passez l'objet <xref:System.Text.StringBuilder> vide comme paramètre `wParam`.  Lorsque SendMessage est retourné, le <xref:System.Text.StringBuilder> contiendra le texte de l'élément sélectionné.  Cette utilisation de SendMessage requiert encore une autre déclaration [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)].  
  
 Pour finir, affectez à `handled` la valeur `true` pour indiquer que le message a été géré.  
  
## Voir aussi  
 <xref:System.Windows.Interop.HwndHost>   
 [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [Procédure pas à pas : mise en route de WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)