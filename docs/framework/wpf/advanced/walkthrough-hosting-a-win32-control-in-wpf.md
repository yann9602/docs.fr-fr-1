---
title: "Procédure pas à pas : hébergement d'un contrôle Win32 dans WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0795875b4d5f1a91b7c570320acb078b845ae712
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Procédure pas à pas : hébergement d'un contrôle Win32 dans WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, lorsque vous avez beaucoup investi [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] code, il peut être plus efficace de réutiliser au moins certains de ce code dans votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application plutôt que de le réécrire complètement. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit un mécanisme simple pour héberger un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre, dans un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.  
  
 Cette rubrique vous explique comment une application, [hébergement d’un contrôle de zone de liste Win32 dans l’exemple WPF](http://go.microsoft.com/fwlink/?LinkID=159998), qui héberge un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contrôle zone de liste. Cette procédure générale peut être étendue à l’hébergement de toute [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre.  
  
  
<a name="requirements"></a>   
## <a name="requirements"></a>Configuration requise  
 Cette rubrique suppose une connaissance de base à la fois avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de programmation. Pour une introduction à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de programmation, consultez [mise en route](../../../../docs/framework/wpf/getting-started/index.md). Pour obtenir une présentation [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de programmation, vous devez référencer un des nombreux livres sur l’objet, en particulier *programmation Windows* de Charles Petzold.  
  
 Étant donné que l’exemple qui accompagne cette rubrique est implémenté dans [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], il utilise les [!INCLUDE[TLA#tla_pinvoke](../../../../includes/tlasharptla-pinvoke-md.md)] pour accéder à la [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. Se familiariser avec [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] est utile, mais n’est pas indispensable.  
  
> [!NOTE]
>  Cette rubrique comprend plusieurs exemples de code tirés de l'exemple associé. Cependant, pour une meilleure lecture, il n'inclut pas la totalité de l'exemple de code. Vous pouvez obtenir ou consulter le code complet de [hébergement d’un contrôle de zone de liste Win32 dans WPF, exemple](http://go.microsoft.com/fwlink/?LinkID=159998).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Procédure de base  
 Cette section décrit la procédure de base pour héberger une [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre sur un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page. Les sections restantes décrivent chaque étape en détails.  
  
 La procédure d’hébergement de base est la suivante :  
  
1.  Implémentez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page pour héberger la fenêtre. Une technique consiste à créer un <xref:System.Windows.Controls.Border> élément pour réserver une section de la page de la fenêtre hébergée.  
  
2.  Implémenter une classe pour héberger le contrôle qui hérite de <xref:System.Windows.Interop.HwndHost>.  
  
3.  Dans cette classe, substituez le <xref:System.Windows.Interop.HwndHost> membre de la classe <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>.  
  
4.  Créer la fenêtre hébergée en tant qu’enfant de la fenêtre qui contienne le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page. Bien que les conventionnelle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programmation n’a pas besoin d’effectuer explicitement utiliser, la page d’hébergement est une fenêtre avec un handle (HWND). Vous recevez la page HWND via le `hwndParent` paramètre de la <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> (méthode). La fenêtre hébergée doit être créée comme un enfant de ce HWND.  
  
5.  Une fois que vous avez créé la fenêtre hôte, retournez le HWND de la fenêtre hébergée. Si vous souhaitez héberger un ou plusieurs [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contrôles, vous généralement créer une fenêtre hôte en tant qu’enfant du HWND et rendre les contrôles enfants de cette fenêtre d’hôte. Encapsulation des contrôles dans une fenêtre hôte offre un moyen simple pour votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page pour recevoir des notifications des contrôles, qui traitent de certains particulier [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] problèmes liés aux notifications à travers la limite HWND.  
  
6.  Gérez les messages sélectionnés envoyés à la fenêtre hôte, comme les notifications des contrôles enfants. Il existe deux manières de procéder.  
  
    -   Si vous préférez traiter les messages dans votre classe d’hébergement, substituez le <xref:System.Windows.Interop.HwndHost.WndProc%2A> méthode de la <xref:System.Windows.Interop.HwndHost> classe.  
  
    -   Si vous préférez que les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gèrent les messages, gérez le <xref:System.Windows.Interop.HwndHost> classe <xref:System.Windows.Interop.HwndHost.MessageHook> événements dans votre code-behind. Cet événement se produit pour chaque message reçu par la fenêtre hébergée. Si vous choisissez cette option, vous devez quand même substituer <xref:System.Windows.Interop.HwndHost.WndProc%2A>, mais vous n’avez besoin que d’une implémentation minimale.  
  
7.  Remplacer la <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> et <xref:System.Windows.Interop.HwndHost.WndProc%2A> méthodes de <xref:System.Windows.Interop.HwndHost>. Vous devez substituer ces méthodes pour répondre à la <xref:System.Windows.Interop.HwndHost> contrat, mais vous devrez peut-être uniquement fournir une implémentation minimale.  
  
8.  Dans votre fichier code-behind, créez une instance de la classe d’hébergement de contrôle et le rendre un enfant de le <xref:System.Windows.Controls.Border> élément est destiné à héberger la fenêtre.  
  
9. Communiquer avec la fenêtre hébergée en l’envoyant [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] messages et la gestion des messages à partir de ses fenêtres enfants, tels que les notifications envoyées par les contrôles.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Implémenter la disposition de la page  
 La mise en page pour le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page qui héberge le contrôle de zone de liste se compose de deux régions. Le côté gauche de la page héberge plusieurs [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des contrôles qui fournissent un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] qui vous permet de manipuler le [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contrôle. Le coin en haut à droite de la page contient une zone carrée pour le contrôle ListBox hébergé.  
  
 Le code pour implémenter cette disposition est très simple. L’élément racine est un <xref:System.Windows.Controls.DockPanel> qui a deux éléments enfants. Le premier est un <xref:System.Windows.Controls.Border> qui héberge le contrôle ListBox. Il occupe un carré de 200 x 200 en haut à droite de la page. Le deuxième est un <xref:System.Windows.Controls.StackPanel> élément qui contient un ensemble de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôles qui affichent des informations et vous permettent de manipuler le contrôle ListBox en définissant des propriétés d’interopérabilité exposées. Pour chacun des éléments qui sont des enfants de le <xref:System.Windows.Controls.StackPanel>, consultez la documentation de référence pour les différents éléments utilisés pour plus d’informations sur quelles sont ces éléments ou ce qu’elles font, celles-ci sont répertoriées dans l’exemple de code ci-dessous, mais ne seront pas expliqués ici (base modèle d’interopérabilité ne requiert pas un d'entre eux, ils sont fournis pour ajouter une certaine interactivité à l’exemple).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implémenter une classe pour héberger le contrôle Microsoft Win32  
 Le cœur de cet exemple est la classe qui héberge réellement le contrôle, ControlHost.cs. Il hérite de <xref:System.Windows.Interop.HwndHost>. Le constructeur accepte deux paramètres, hauteur et largeur, qui correspondent à la hauteur et la largeur de la <xref:System.Windows.Controls.Border> qui héberge le contrôle ListBox. Ces valeurs sont utilisées ultérieurement pour vous assurer que la taille du contrôle correspond à la <xref:System.Windows.Controls.Border> élément.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Il existe également un ensemble de constantes. Ces constantes sont prises en grande partie de Winuser.h et vous permettent d’utiliser des noms conventionnels lors de l’appel [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fonctions.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Substituer BuildWindowCore pour créer la fenêtre Microsoft Win32  
 Vous substituez cette méthode pour créer la [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre qui sera hébergée par la page et établir la connexion entre la fenêtre et la page. Comme cet exemple implique l’hébergement d’un contrôle ListBox, deux fenêtres sont créées. La première est la fenêtre qui est effectivement hébergée par le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page. Le contrôle ListBox est créé comme un enfant de cette fenêtre.  
  
 Cette approche a pour but de simplifier le processus de réception des notifications du contrôle. La <xref:System.Windows.Interop.HwndHost> classe vous permet de traiter les messages envoyés à la fenêtre qu’elle héberge. Si vous hébergez un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contrôler directement, vous recevez les messages envoyés à la boucle de messages interne du contrôle. Vous pouvez afficher le contrôle et lui envoyer des messages, mais vous ne recevez pas les notifications que le contrôle envoie à sa fenêtre parente. Cela signifie, entre autres, que vous n’avez aucun moyen de détecter quand l’utilisateur interagit avec le contrôle. Au lieu de cela, créez une fenêtre hôte et définissez le contrôle comme un enfant de cette fenêtre. Cela vous permet de traiter les messages de la fenêtre hôte, y compris les notifications que le contrôle lui envoie. Pour des raisons pratiques, comme la fenêtre hôte n’est guère plus qu’un simple wrapper pour le contrôle, le package est un contrôle ListBox.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Créer la fenêtre hôte et un contrôle ListBox  
 Vous pouvez utiliser [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] pour créer une fenêtre hôte pour le contrôle en créant et en enregistrant une classe de fenêtre et ainsi de suite. Toutefois, vous pouvez, beaucoup plus simplement, créer une fenêtre avec la classe de fenêtre « statique » prédéfinie. Cela vous fournit la procédure de fenêtre dont vous avez besoin pour recevoir les notifications du contrôle et nécessite un minimum de codage.  
  
 Le HWND du contrôle est exposé au moyen d’une propriété en lecture seule, de sorte que la page hôte peut l’utiliser pour envoyer des messages au contrôle.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 Le contrôle ListBox est créé comme un enfant de la fenêtre hébergée. La hauteur et la largeur des deux fenêtres sont définies sur les valeurs passées au constructeur, comme décrit ci-dessus. Cela garantit que la taille de la fenêtre hôte et du contrôle est identique à la zone réservée dans la page.  Après avoir créé les fenêtres, l’exemple retourne un <xref:System.Runtime.InteropServices.HandleRef> objet qui contient le HWND de la fenêtre hôte.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Implémenter DestroyWindow et WndProc  
 En plus de <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, vous devez également substituer la <xref:System.Windows.Interop.HwndHost.WndProc%2A> et <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> méthodes de la <xref:System.Windows.Interop.HwndHost>. Dans cet exemple, les messages pour le contrôle sont gérés par le <xref:System.Windows.Interop.HwndHost.MessageHook> gestionnaire, par conséquent, l’implémentation de <xref:System.Windows.Interop.HwndHost.WndProc%2A> et <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> est minime. Dans le cas de <xref:System.Windows.Interop.HwndHost.WndProc%2A>, définissez `handled` à `false` pour indiquer que le message n’a pas été géré et retourne 0. Pour <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, détruisez simplement la fenêtre.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Héberger le contrôle dans la page  
 Pour héberger le contrôle sur la page, vous créez d’abord une nouvelle instance de la `ControlHost` classe. Passez la hauteur et la largeur de l’élément de bordure qui contient le contrôle (`ControlHostElement`) pour le `ControlHost` constructeur. Cela garantit que la taille du ListBox est correcte. Vous hébergez le contrôle sur la page en assignant le `ControlHost` de l’objet à la <xref:System.Windows.Controls.Decorator.Child%2A> propriété de l’hôte <xref:System.Windows.Controls.Border>.  
  
 L’exemple attache un gestionnaire à la <xref:System.Windows.Interop.HwndHost.MessageHook> l’événement de la `ControlHost` pour recevoir des messages à partir du contrôle. Cet événement est déclenché pour chaque message envoyé à la fenêtre hébergée. Dans ce cas, il s’agit des messages envoyés à la fenêtre qui encapsule le contrôle ListBox réel, y compris les notifications du contrôle. L’exemple appelle SendMessage pour obtenir des informations du contrôle et modifier son contenu. Les détails sur la façon dont la page communique avec le contrôle sont décrits dans la section suivante.  
  
> [!NOTE]
>  Notez qu’il existe deux [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] déclarations pour SendMessage. Cela est nécessaire car un utilise le `wParam` paramètre à passer une chaîne et l’autre utilise pour passer un entier. Vous avez besoin d’une déclaration distincte pour chaque signature afin de garantir que les données sont correctement marshalées.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Implémenter une communication entre le contrôle et la page  
 Vous manipulez le contrôle en l’envoyant [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)] messages. Le contrôle vous notifie quand l’utilisateur interagit avec lui en envoyant des notifications à sa fenêtre hôte. Le [hébergement d’un contrôle de zone de liste Win32 dans l’exemple WPF](http://go.microsoft.com/fwlink/?LinkID=159998) exemple inclut une interface utilisateur qui fournit plusieurs exemples montrant comment cela fonctionne :  
  
-   Ajouter un élément à la liste.  
  
-   Supprimez l'élément sélectionné de la liste.  
  
-   Afficher le texte de l'élément actuellement sélectionné.  
  
-   Afficher le nombre d’éléments de la liste.  
  
 L’utilisateur peut également sélectionner un élément dans la zone de liste en cliquant dessus, tout comme ils le feraient pour un conventionnelle [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application. Les données affichées sont mises à jour chaque fois que l’utilisateur change l’état de la zone de liste en sélectionnant ou ajoutant un élément.  
  
 Pour ajouter des éléments, envoyez un message LB_ADDSTRING à la zone de liste. Pour supprimer des éléments, envoyez LB_GETCURSEL pour obtenir l’index de la sélection actuelle, puis LB_DELETESTRING pour supprimer l’élément. L’exemple envoie aussi LB_GETCOUNT et utilise la valeur retournée pour mettre à jour l’affichage du nombre d’éléments. Ces deux instances de SendMessage utilisent une de le [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] déclarations décrites dans la section précédente.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Lorsque l’utilisateur sélectionne un élément ou modifie sa sélection, le contrôle avertit la fenêtre hôte en l’envoyant un message WM_COMMAND, qui déclenche le <xref:System.Windows.Interop.HwndHost.MessageHook> événement pour la page. Le gestionnaire reçoit les mêmes informations que la procédure de fenêtre principale de la fenêtre hôte. Il passe également une référence à une valeur booléenne, `handled`. Vous définissez `handled` à `true` pour indiquer que vous avez géré le message et aucun traitement supplémentaire n’est nécessaire.  
  
 WM_COMMAND est envoyé pour diverses raisons, vous devez donc examiner l’ID de notification pour déterminer s’il s’agit d’un événement que vous voulez gérer. L’ID est contenu dans le mot de poids fort du `wParam` paramètre. Étant donné que [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] est n’a pas de macro HIWORD, l’exemple utilise des opérateurs au niveau du bit pour extraire l’ID. Si l’utilisateur a effectué ou changé sa sélection, l’ID est LBN_SELCHANGE.  
  
 Quand LBN_SELCHANGE est reçu, l’exemple obtient l’index de l’élément sélectionné en envoyant un message LB_GETCURSEL au contrôle. Pour obtenir le texte, vous créez tout d’abord un <xref:System.Text.StringBuilder>. Vous envoyez ensuite au contrôle un message LB_GETTEXT. Passez le vide <xref:System.Text.StringBuilder> de l’objet en tant que le `wParam` paramètre. Lorsque SendMessage est retourné, le <xref:System.Text.StringBuilder> contient le texte de l’élément sélectionné. Cette utilisation de SendMessage requiert encore une autre [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] déclaration.  
  
 Enfin, définissez `handled` à `true` pour indiquer que le message a été géré.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Interop.HwndHost>  
 [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Procédure pas à pas : ma première application de bureau WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)
