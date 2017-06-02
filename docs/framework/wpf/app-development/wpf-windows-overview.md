---
title: "Vue d&#39;ensemble des fen&#234;tres WPF | Microsoft Docs"
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
  - "applications, hébergement"
  - "contenu, afficher"
  - "contenu, afficher via du code procédural"
  - "contenu, afficher via XAML"
  - "créer, fenêtres"
  - "boîtes de dialogue"
  - "afficher un contenu"
  - "afficher un contenu via du code procédural"
  - "afficher des pages XAML"
  - "événements"
  - "hébergement, applications"
  - "gérer les fenêtres"
  - "boîtes de dialogue modales"
  - "fenêtres modales"
  - "objets NavigationWindow"
  - "Page (objet)"
  - "code procédural, afficher un contenu via"
  - "événements de fenêtre"
  - "gestion des fenêtres"
  - "objets fenêtres"
  - "fenêtres"
  - "pages XAML, afficher"
  - "XAML, afficher un contenu via"
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
caps.latest.revision: 65
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 60
---
# Vue d&#39;ensemble des fen&#234;tres WPF
Les utilisateurs interagissent avec les applications autonomes [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] par le biais de fenêtres.  L'objectif principal d'une fenêtre est d'héberger le contenu hôte qui affiche des données et permet aux utilisateurs d'interagir avec les données. Les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] autonomes fournissent leurs propres fenêtres à l'aide de la classe <xref:System.Windows.Window>.  Cette rubrique introduit <xref:System.Windows.Window> avant de couvrir les notions de base de création et de gestion de fenêtres dans des applications autonomes.  
  
> [!NOTE]
>  Les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hébergées par navigateur, y compris les [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] et les pages libres [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], ne fournissent pas leurs propres fenêtres.  À la place, elles sont hébergées dans des fenêtres fournies par [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)].  Consultez [Vue d'ensemble des applications de navigateur XAML](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
   
  
<a name="TheWindowClass"></a>   
## La classe Window  
 L'illustration suivante montre les parties constituantes d'une fenêtre.  
  
 ![Éléments de fenêtre](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure1.PNG "WindowOverviewFigure1")  
  
 Une fenêtre est divisée en deux zones : la zone non cliente et la zone cliente.  
  
 La *zone non cliente* d'une fenêtre est implémentée par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] et inclut les parties d'une fenêtre qui sont communes à la plupart des fenêtres, y compris les éléments suivants :  
  
-   Une bordure.  
  
-   Une barre de titre.  
  
-   Une icône.  
  
-   Les boutons Réduire, Agrandir et Restaurer.  
  
-   Un bouton Fermer.  
  
-   Menu système avec des éléments de menu qui permettent aux utilisateurs de réduire, agrandir, restaurer, déplacer, redimensionner et fermer une fenêtre.  
  
 La *zone cliente* d'une fenêtre est la zone dans la zone non cliente d'une fenêtre, utilisée par les développeurs pour ajouter des contenus spécifiques à une application, tels que barres de menus, barres d'outils et contrôles.  
  
 Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], une fenêtre est encapsulée par la classe <xref:System.Windows.Window> que vous utilisez pour effectuer les opérations suivantes :  
  
-   Afficher une fenêtre.  
  
-   Configurer la taille, la position et l'apparence d'une fenêtre.  
  
-   Héberger un contenu spécifique à une application.  
  
-   Gérer la durée de vie d'une fenêtre.  
  
<a name="DefiningAWindow"></a>   
## Implémentation d'une fenêtre  
 L'implémentation d'une fenêtre typique comprend à la fois son apparence et son comportement, où l'*apparence* définit à quoi ressemble une fenêtre pour les utilisateurs et le *comportement* définit le mode de fonctionnement d'une fenêtre lorsque les utilisateurs interagissent avec elle.  Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vous pouvez implémenter l'apparence et le comportement d'une fenêtre à l'aide du code ou du balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 En général, toutefois, l'apparence d'une fenêtre est implémentée à l'aide du balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et son comportement est implémenté à l'aide de code\-behind, comme représenté dans l'exemple suivant.  
  
 [!code-xml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Pour permettre à un fichier de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et à un fichier code\-behind de fonctionner ensemble, les éléments suivants sont requis :  
  
-   Dans les balises, l'élément `Window` doit inclure l'attribut `x:Class`.  Lorsque l'application est générée, l'existence de `x:Class` dans le fichier de balisage amène [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] à créer une classe `partial` qui dérive de <xref:System.Windows.Window> et qui porte le nom spécifié par l'attribut `x:Class`.  Cela requiert l'ajout d'une déclaration d'espace de noms [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pour le schéma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] \(`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`\).  La classe `partial` générée implémente la méthode `InitializeComponent`, appelée pour enregistrer les événements et définir les propriétés implémentées dans la balise.  
  
-   Dans code\-behind, la classe doit être une classe `partial` avec le même nom spécifié par l'attribut `x:Class` dans la balise et elle doit dériver de <xref:System.Windows.Window>.  Cela permet au fichier code\-behind d'être associé à la classe `partial` générée pour le fichier de balisage lorsque l'application est générée \(consultez [Génération d'une application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)\).  
  
-   Dans le code\-behind, la classe <xref:System.Windows.Window> doit implémenter un constructeur qui appelle la méthode `InitializeComponent`.  `InitializeComponent` est implémenté par la classe `partial` générée du fichier de balisage pour enregistrer les événements et configurer les propriétés définies dans le balisage.  
  
> [!NOTE]
>  Lorsque vous ajoutez un nouveau <xref:System.Windows.Window> à votre projet en utilisant [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Window> est implémenté à l'aide du balisage et du code\-behind et il inclut la configuration nécessaire pour créer l'association entre les fichiers de balisage et les fichiers code\-behind comme décrit ici.  
  
 Une fois cette configuration en place, vous pouvez vous concentrer sur la définition de l'apparence de la fenêtre dans le balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et l'implémentation de son comportement dans code\-behind.  L'exemple suivant montre une fenêtre avec un bouton, implémentée dans le balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et un gestionnaire d'événements pour l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> du bouton, implémenté dans code\-behind.  
  
 [!code-xml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## Configuration d'une définition de fenêtre pour MSBuild  
 La manière dont vous implémentez votre fenêtre détermine comment elle est configurée pour [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)].  Pour une fenêtre définie à l'aide du balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et du code\-behind :  
  
-   Les fichiers de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sont configurés comme éléments `Page` [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)].  
  
-   Les fichiers code\-behind sont configurés comme éléments `Compile` [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)].  
  
 Cela est indiqué dans le fichier projet [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] suivant.  
  
```  
<Project ... xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Pour plus d'informations sur la génération d'applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consultez [Génération d'une application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>   
## Durée de vie d'une fenêtre  
 Comme avec toute classe, une fenêtre a une durée de vie qui commence lors de sa première instanciation, après quoi elle est ouverte, activée et désactivée et finalement fermée.  
  
   
  
<a name="Opening_a_Window"></a>   
### Ouverture d'une fenêtre  
 Pour ouvrir une fenêtre, vous commencez par en créer une instance, comme montré dans l'exemple suivant.  
  
 [!code-xml[WindowsOverviewStartupEventSnippets#AppMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 Dans cet exemple, le `MarkupAndCodeBehindWindow` est instancié lorsque l'application démarre, ce qui se produit lorsque l'événement <xref:System.Windows.Application.Startup> est déclenché.  
  
 Lorsqu'une fenêtre est instanciée, une référence à celle\-ci est ajoutée automatiquement à une liste de fenêtres gérée par l'objet <xref:System.Windows.Application> \(consultez <xref:System.Windows.Application.Windows%2A?displayProperty=fullName>\).  En outre, la première fenêtre à être instanciée est, par défaut, définie par <xref:System.Windows.Application> comme fenêtre d'application principale \(consultez <xref:System.Windows.Application.MainWindow%2A?displayProperty=fullName>\).  
  
 Pour finir, la fenêtre est ouverte en appelant la méthode <xref:System.Windows.Window.Show%2A> ; le résultat est indiqué dans l'illustration suivante.  
  
 ![Fenêtre ouverte en appelant Window.Show](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure8.png "WindowOverviewFigure8")  
  
 Une fenêtre ouverte en appelant <xref:System.Windows.Window.Show%2A> est une fenêtre non modale, ce qui signifie que l'application fonctionne selon un mode permettant aux utilisateurs d'activer d'autres fenêtres dans la même application.  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A> est appelé pour ouvrir en mode modal des fenêtres telles que des boîtes de dialogue.  Pour plus d'informations, consultez [Vue d'ensemble des boîtes de dialogue](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
 Lorsque <xref:System.Windows.Window.Show%2A> est appelé, une fenêtre exécute un travail d'initialisation avant qu'elle ne soit affichée afin d'établir une infrastructure lui permettant de recevoir des entrées d'utilisateur.  Lorsque la fenêtre est initialisée, l'événement <xref:System.Windows.Window.SourceInitialized> est déclenché et la fenêtre est affichée.  
  
 Comme raccourci, <xref:System.Windows.Application.StartupUri%2A> peut être configuré pour spécifier la première fenêtre ouverte automatiquement lorsqu'une application démarre.  
  
 [!code-xml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Lorsque l'application démarre, la fenêtre spécifiée par la valeur de <xref:System.Windows.Application.StartupUri%2A> est ouverte de façon non modale ; en interne, la fenêtre est ouverte en appelant sa méthode <xref:System.Windows.Window.Show%2A>.  
  
<a name="Ownership"></a>   
#### Propriété de fenêtre  
 Une fenêtre ouverte à l'aide de la méthode <xref:System.Windows.Window.Show%2A> ne possède pas de relation implicite avec la fenêtre qui l'a créée ; les utilisateurs peuvent interagir indépendamment avec l'une ou l'autre fenêtre, ce qui signifie que l'une ou l'autre fenêtre peut effectuer les opérations suivantes :  
  
-   Recouvrir l'autre fenêtre \(à moins que la propriété <xref:System.Windows.Window.Topmost%2A> d'une des fenêtres ait la valeur `true`\).  
  
-   Être réduite, agrandie et restaurée sans affecter l'autre fenêtre.  
  
 Certaines fenêtres requièrent une relation avec la fenêtre qui les ouvre.  Par exemple, une application d'[!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] peut ouvrir des fenêtres de propriété et des fenêtres Outil dont le comportement typique est de couvrir la fenêtre qui les crée.  En outre, ces fenêtres doivent toujours se fermer, se réduire, s'agrandir et se restaurer de concert avec la fenêtre qui les a créées.  Une telle relation peut être établie en faisant de sorte qu'une fenêtre en *possède* une autre ; ceci est accompli en affectant à la propriété <xref:System.Windows.Window.Owner%2A> de la *fenêtre possédée* une référence à la *fenêtre propriétaire*.  L'exemple suivant le démontre.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Après établissement de la propriété :  
  
-   La fenêtre possédée peut référencer sa fenêtre propriétaire en consultant la valeur de sa propriété <xref:System.Windows.Window.Owner%2A>.  
  
-   La fenêtre propriétaire peut découvrir toutes les fenêtres qu'elle possède en consultant la valeur de sa propriété <xref:System.Windows.Window.OwnedWindows%2A>.  
  
<a name="Preventing"></a>   
#### Empêcher l'activation de fenêtres  
 Dans certains scénarios, les fenêtres ne doivent pas être activées lorsque qu'elles sont affichées \(fenêtres de conversation d'une application de style Messenger sur Internet ou fenêtres de notification d'une application de messagerie, par exemple\).  
  
 Si votre application possède une fenêtre qui ne doit pas être activée lorsque qu'elle est affichée, vous pouvez affecter à sa propriété <xref:System.Windows.Window.ShowActivated%2A> la valeur `false` avant d'appeler la méthode <xref:System.Windows.Window.Show%2A> pour la première fois.  En conséquence :  
  
-   La fenêtre n'est pas activée.  
  
-   L'événement <xref:System.Windows.Window.Activated> de la fenêtre n'est pas déclenché.  
  
-   La fenêtre actuellement activée reste activée.  
  
 La fenêtre sera toutefois activée dès que l'utilisateur l'activera en cliquant sur la zone cliente ou non cliente.  Dans ce cas :  
  
-   La fenêtre est activée.  
  
-   L'événement <xref:System.Windows.Window.Activated> de la fenêtre est déclenché.  
  
-   La fenêtre précédemment activée est désactivée.  
  
-   Les événements <xref:System.Windows.Window.Deactivated> et <xref:System.Windows.Window.Activated> de la fenêtre sont ensuite déclenchés comme prévu, en réponse à des actions de l'utilisateur.  
  
<a name="Window_Activation"></a>   
### Activation de fenêtre  
 Lors de la première ouverture d'une fenêtre, elle devient la fenêtre active \(sauf si elle est affichée avec <xref:System.Windows.Window.ShowActivated%2A> ayant la valeur `false`\).  La *fenêtre active* est la fenêtre qui capture actuellement les entrées d'utilisateur, telles les séquences de touches et les clics de souris.  Lorsqu'une fenêtre devient active, elle déclenche l'événement <xref:System.Windows.Window.Activated>.  
  
> [!NOTE]
>  Lorsqu'une fenêtre est ouverte initialement, les événements <xref:System.Windows.FrameworkElement.Loaded> et <xref:System.Windows.Window.ContentRendered> ne sont déclenchés qu'après après le déclenchement de l'événement <xref:System.Windows.Window.Activated>.  Il s'ensuit qu'une fenêtre peut effectivement être considérée ouverte lorsque <xref:System.Windows.Window.ContentRendered> est déclenché.  
  
 Après qu'une fenêtre soit devenue active, un utilisateur peut activer une autre fenêtre dans la même application ou activer une autre application.  Lorsque cela se produit, la fenêtre actuellement active est désactivée et déclenche l'événement <xref:System.Windows.Window.Deactivated>.  De même, lorsque l'utilisateur sélectionne une fenêtre actuellement désactivée, celle\-ci redevient active et <xref:System.Windows.Window.Activated> est déclenché.  
  
 Une raison commune de gérer <xref:System.Windows.Window.Activated> et <xref:System.Windows.Window.Deactivated> est d'activer et de désactiver une fonctionnalité qui ne peut s'exécuter que lorsqu'une fenêtre est active.  Par exemple, certaines fenêtres affichent un contenu interactif qui requiert en permanence l'attention de l'utilisateur ou des entrées de sa part, notamment les jeux vidéo et les lecteurs de vidéo.  L'exemple suivant est un lecteur de vidéo simplifié qui montre comment gérer <xref:System.Windows.Window.Activated> et <xref:System.Windows.Window.Deactivated> pour implémenter ce comportement.  
  
 [!code-xml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 D'autres types d'applications peuvent encore exécuter du code en arrière\-plan lorsqu'une fenêtre est désactivée.  Par exemple, un client de messagerie peut continuer à interroger le serveur de messagerie pendant que l'utilisateur utilise d'autres applications.  Des applications de ce type fournissent souvent un comportement différent ou supplémentaire pendant que la fenêtre principale est désactivée.  En ce qui concerne le programme de messagerie, cela peut signifier l'ajout du nouvel élément de messagerie à la boîte de réception ainsi que celui d'une icône de notification dans la barre d'état système.  Une icône de notification n'a besoin d'être affichée que lorsque la fenêtre de courrier n'est pas active, ce qui peut être déterminé en examinant la propriété <xref:System.Windows.Window.IsActive%2A>.  
  
 Si une tâche en arrière\-plan se termine, une fenêtre peut souhaiter notifier plus rapidement l'utilisateur en appelant la méthode <xref:System.Windows.Window.Activate%2A>.  Si l'utilisateur interagit avec une autre application activée lorsque <xref:System.Windows.Window.Activate%2A> est appelé, le bouton de la barre des tâches de la fenêtre clignote.  Si un utilisateur interagit avec l'application actuelle, l'appel de <xref:System.Windows.Window.Activate%2A> ramènera la fenêtre au premier plan.  
  
> [!NOTE]
>  Vous pouvez gérer l'activation de la portée application à l'aide des événements <xref:System.Windows.Application.Activated?displayProperty=fullName> et <xref:System.Windows.Application.Deactivated?displayProperty=fullName>.  
  
<a name="Closing_a_Window"></a>   
### Fermeture d'une fenêtre  
 La durée de vie d'une fenêtre est proche de sa fin lorsqu'un utilisateur la ferme.  Une fenêtre peut être fermée à l'aide d'éléments dans la zone non cliente, y compris les suivants :  
  
-   L'élément **Fermer** du menu **Système**.  
  
-   Appuyer sur la touche ALT\+F4.  
  
-   Appuyer sur le bouton **Fermer**.  
  
 Vous pouvez fournir des mécanismes supplémentaires à la zone cliente pour fermer une fenêtre, dont les plus communs incluent les suivants :  
  
-   Un élément **Quitter** dans le menu **Fichier**, généralement pour les fenêtres d'application principales.  
  
-   Un élément **Fermer** dans le menu **Fichier**, généralement sur une fenêtre d'application secondaire.  
  
-   Un bouton **Annuler**, généralement sur une boîte de dialogue modale.  
  
-   Un bouton **Fermer**, généralement sur une boîte de dialogue non modale.  
  
 Pour fermer une fenêtre en réponse à l'un de ces mécanismes personnalisés, vous devez appeler la méthode <xref:System.Windows.Window.Close%2A>.  L'exemple suivant implémente la capacité de fermer une fenêtre en choisissant **Quitter** dans le menu **Fichier**.  
  
 [!code-xml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Lorsqu'une fenêtre se ferme, elle déclenche deux événements : <xref:System.Windows.Window.Closing> et <xref:System.Windows.Window.Closed>.  
  
 <xref:System.Windows.Window.Closing> est déclenché avant que la fenêtre ne se ferme et il fournit un mécanisme grâce auquel la fermeture de la fenêtre peut être empêchée.  Une raison commune d'empêcher la fermeture d'une fenêtre est lorsque son contenu a été modifié.  Dans cette situation, l'événement <xref:System.Windows.Window.Closing> peut être géré pour déterminer si les données sont modifiées et, dans ce cas, demander à l'utilisateur s'il faut continuer à fermer la fenêtre sans enregistrer les données ou annuler la fermeture.  L'exemple suivant montre les aspects clés de la gestion de <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets#WindowClosingCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs#windowclosingcodebehind1)]
 [!code-vb[WindowClosingSnippets#WindowClosingCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb#windowclosingcodebehind1)]  
[!code-csharp[WindowClosingSnippets#WindowClosingCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs#windowclosingcodebehind2)]
[!code-vb[WindowClosingSnippets#WindowClosingCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb#windowclosingcodebehind2)]  
  
 Le gestionnaire d'événements <xref:System.ComponentModel.CancelEventArgs> reçoit un <xref:System.Windows.Window.Closing> qui implémente la propriété `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> à laquelle vous affectez la valeur `true` pour empêcher une fenêtre de se fermer.  
  
 Si <xref:System.Windows.Window.Closing> n'est pas géré, ou géré mais non annulé, la fenêtre se fermera.  Juste avant qu'une fenêtre ne se ferme réellement, <xref:System.Windows.Window.Closed> est déclenché.  À ce stade, on ne peut pas empêcher une fenêtre de se fermer.  
  
> [!NOTE]
>  Une application peut être configurée pour se fermer automatiquement lors de la fermeture de la fenêtre d'application principale \(consultez <xref:System.Windows.Application.MainWindow%2A>\) ou lors de la fermeture de la dernière fenêtre.  Pour plus d'informations, consultez <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Bien qu'une fenêtre puisse être fermée explicitement par le biais de mécanismes fournis dans les zones clientes et non\-clientes, une fenêtre peut également être fermée implicitement par suite du comportement dans d'autres parties de l'application ou de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], y compris les éléments suivants :  
  
-   Un utilisateur se déconnecte ou arrête [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)].  
  
-   Le propriétaire d'une fenêtre se ferme \(consultez <xref:System.Windows.Window.Owner%2A>\).  
  
-   La fenêtre d'application principale est fermée et <xref:System.Windows.Application.ShutdownMode%2A> est <xref:System.Windows.ShutdownMode>.  
  
-   <xref:System.Windows.Application.Shutdown%2A> est appelé.  
  
> [!NOTE]
>  Une fenêtre ne peut pas être rouverte après sa fermeture.  
  
<a name="Window_Lifetime_Events"></a>   
### Événements de la durée de vie de la fenêtre  
 L'illustration suivante montre la séquence des événements principaux de la durée de vie d'une fenêtre.  
  
 ![Durée de vie d'une fenêtre](../../../../docs/framework/wpf/app-development/media/windowlifetimeevents.png "WindowLifetimeEvents")  
  
 L'illustration suivante montre la séquence des principaux événements de la durée de vie d'une fenêtre affichée sans activation \(<xref:System.Windows.Window.ShowActivated%2A> a la valeur `false` avant l'affichage de la fenêtre\).  
  
 ![Durée de vie d'une fenêtre &#40;Window.ShowActivated &#61; False&#41;](../../../../docs/framework/wpf/app-development/media/windowlifetimenoact.png "WindowLifetimeNoAct")  
  
<a name="WindowLocation"></a>   
## Emplacement de la fenêtre  
 Lorsqu'une fenêtre est ouverte, elle dispose d'un emplacement dans les dimensions x et y du Bureau.  Cet emplacement peut être déterminé en consultant les propriétés <xref:System.Windows.Window.Left%2A> et <xref:System.Windows.Window.Top%2A>, respectivement.  Vous pouvez définir ces propriétés pour modifier l'emplacement de la fenêtre.  
  
 Vous pouvez également spécifier l'emplacement initial d'un <xref:System.Windows.Window> lorsqu'il apparaît pour la première fois en définissant la propriété <xref:System.Windows.Window.WindowStartupLocation%2A> avec l'une des valeurs d'énumération <xref:System.Windows.WindowStartupLocation> suivantes :  
  
-   <xref:System.Windows.WindowStartupLocation> \(par défaut\)  
  
-   <xref:System.Windows.WindowStartupLocation>  
  
-   <xref:System.Windows.WindowStartupLocation>  
  
 Si l'emplacement de démarrage est spécifié comme <xref:System.Windows.WindowStartupLocation> et que les propriétés <xref:System.Windows.Window.Left%2A> et <xref:System.Windows.Window.Top%2A> n'ont pas été définies, <xref:System.Windows.Window> demandera [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] un emplacement dans lequel apparaître.  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### Fenêtres au premier plan et ordre de plan  
 Outre un emplacement dans les dimensions X et Y, une fenêtre possède également un emplacement dans la dimension Z, qui détermine sa position verticale par rapport à d'autres fenêtres.  Ceci est connu comme l'ordre de plan de la fenêtre, et il existe deux types : l'ordre de plan normal et l'ordre de plan le plus haut.  L'emplacement d'une fenêtre dans l' *ordre de plan normal* est déterminé par le fait qu'elle est actuellement active ou non.  Par défaut, une fenêtre est située dans l'ordre de plan normal.  L'emplacement d'une fenêtre dans l' *ordre de plan le plus haut* est également déterminé par le fait qu'elle est active ou non.  En outre, les fenêtres dans l'ordre de plan le plus haut sont toujours situées au\-dessus des fenêtres précitées dans l'ordre de plan normal.  Une fenêtre est située dans l'ordre de plan le plus haut en affectant à sa propriété <xref:System.Windows.Window.Topmost%2A> la valeur `true`.  
  
 [!code-xml[WindowsOverviewSnippets#TopmostWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#TopmostWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup2)]  
  
 Dans chaque ordre de plan, la fenêtre active apparaît au\-dessus de toutes les autres fenêtres dans le même ordre de plan.  
  
<a name="WindowSize"></a>   
## Taille de la fenêtre  
 Outre le fait d'avoir un emplacement sur le bureau, une fenêtre a une taille déterminée par plusieurs propriétés, notamment diverses propriétés de largeur et de hauteur et <xref:System.Windows.Window.SizeToContent%2A>.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.MaxWidth%2A> sont utilisés pour gérer la plage des largeurs qu'une fenêtre peut avoir pendant sa durée de vie et sont configurés comme indiqué dans l'exemple suivant.  
  
 [!code-xml[WindowsOverviewSnippets#WidthWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#WidthWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup2)]  
  
 La hauteur de fenêtre est gérée par <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.MaxHeight%2A> et est configurée comme indiqué dans l'exemple suivant.  
  
 [!code-xml[WindowsOverviewSnippets#HeightWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#HeightWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup2)]  
  
 Comme les diverses valeurs de largeur et de hauteur spécifient chacune une plage, il est possible pour la largeur et la hauteur d'une fenêtre redimensionnable de se situer n'importe où dans la plage spécifiée pour la dimension respective.  Pour détecter sa largeur et sa hauteur actuelle, consultez <xref:System.Windows.FrameworkElement.ActualWidth%2A> et <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectivement.  
  
 Si vous souhaitez que la largeur et la hauteur de votre fenêtre correspondent à la taille du contenu de la fenêtre, vous pouvez utiliser la propriété <xref:System.Windows.Window.SizeToContent%2A>, qui possède les valeurs suivantes :  
  
-   <xref:System.Windows.SizeToContent>.  Aucun effet \(valeur par défaut\).  
  
-   <xref:System.Windows.SizeToContent>.  Ajuster à la largeur du contenu, qui a le même effet qu'affecter <xref:System.Windows.FrameworkElement.MinWidth%2A> et <xref:System.Windows.FrameworkElement.MaxWidth%2A> à la largeur du contenu.  
  
-   <xref:System.Windows.SizeToContent>.  Ajuster à la hauteur du contenu, qui a le même effet qu'affecter <xref:System.Windows.FrameworkElement.MinHeight%2A> et <xref:System.Windows.FrameworkElement.MaxHeight%2A> à la hauteur du contenu.  
  
-   <xref:System.Windows.SizeToContent>.  Ajuster à la largeur et à la hauteur du contenu, qui a le même effet qu'affecter <xref:System.Windows.FrameworkElement.MinHeight%2A> et <xref:System.Windows.FrameworkElement.MaxHeight%2A> à la hauteur du contenu et qu'affecter <xref:System.Windows.FrameworkElement.MinWidth%2A> et <xref:System.Windows.FrameworkElement.MaxWidth%2A> à la largeur du contenu.  
  
 L'exemple suivant montre une fenêtre qui s'ajuste automatiquement en fonction de son contenu, verticalement et horizontalement, lors de son affichage initial.  
  
 [!code-xml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#SizeToContentWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup2)]  
  
 L'exemple suivant montre comment définir la propriété d' <xref:System.Windows.Window.SizeToContent%2A> dans le code pour spécifier comment une fenêtre se redimensionne en fonction de son contenu.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## Ordre de priorité des propriétés de dimensionnement  
 Pour l'essentiel, les diverses propriétés de dimensionnement d'une fenêtre se combinent pour définir la plage de largeur et de hauteur pour une fenêtre redimensionnable.  Afin d'assurer une plage valide, <xref:System.Windows.Window> évalue les valeurs des propriétés de taille en fonction des ordres de priorité suivants.  
  
 **Pour les propriétés de hauteur :**  
  
1.  <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=fullName> \>  
  
2.  <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=fullName> \>  
  
3.  <xref:System.Windows.SizeToContent?displayProperty=fullName>\/<xref:System.Windows.SizeToContent?displayProperty=fullName> \>  
  
4.  <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=fullName>  
  
 **Pour les propriétés de largeur :**  
  
1.  <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=fullName> \>  
  
2.  <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=fullName> \>  
  
3.  <xref:System.Windows.SizeToContent?displayProperty=fullName>\/<xref:System.Windows.SizeToContent?displayProperty=fullName> \>  
  
4.  <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=fullName>  
  
 L'ordre de priorité peut également déterminer la taille d'une fenêtre lorsqu'elle est agrandie, à l'aide de la propriété <xref:System.Windows.Window.WindowState%2A>.  
  
<a name="WindowState"></a>   
## État de la fenêtre  
 Pendant la durée de vie d'une fenêtre redimensionnable, celle\-ci peut posséder trois états : normal, réduit et agrandi.  L'état par défaut d'une fenêtre est l'état *normal*.  Une fenêtre possédant cet état permet à un utilisateur de la déplacer et de la redimensionner à l'aide d'une poignée de dimensionnement ou de la bordure, pour autant qu'elle soit redimensionnable.  
  
 Une fenêtre dont l'état est *réduit* est réduite à son bouton de la barre des tâches si <xref:System.Windows.Window.ShowInTaskbar%2A> a la valeur `true` ; sinon, elle est réduite à la plus petite taille possible qu'elle peut avoir et se place dans le coin inférieur gauche du bureau.  Aucun type de fenêtre réduite ne peut être redimensionné à l'aide d'une bordure ou d'une poignée de dimensionnement, bien qu'une fenêtre réduite qui n'est pas affichée dans la barre des tâches puisse être déplacée en tout point du bureau.  
  
 Une fenêtre dont l'état est *agrandi* se développe à la taille maximale possible, laquelle ne peut être supérieure à ce qui est déterminé par ses propriétés <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A> et <xref:System.Windows.Window.SizeToContent%2A>.  Comme une fenêtre réduite, une fenêtre agrandie ne peut pas être redimensionnée à l'aide d'une poignée de dimensionnement ou en faisant glisser sa bordure.  
  
> [!NOTE]
>  Les valeurs des propriétés <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>et <xref:System.Windows.FrameworkElement.Height%2A> d'une fenêtre représentent toujours les valeurs pour l'état normal, même quand la fenêtre est actuellement agrandie ou réduite.  
  
 L'état d'une fenêtre peut être configuré en définissant sa propriété <xref:System.Windows.Window.WindowState%2A> qui peut avoir l'une des valeurs d'énumération <xref:System.Windows.WindowState> suivantes :  
  
-   <xref:System.Windows.WindowState> \(par défaut\)  
  
-   <xref:System.Windows.WindowState>  
  
-   <xref:System.Windows.WindowState>  
  
 L'exemple suivant montre comment créer une fenêtre qui sera agrandie lors de son ouverture.  
  
 [!code-xml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#WindowStateWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup2)]  
  
 En général, vous devez définir <xref:System.Windows.Window.WindowState%2A> pour configurer l'état initial d'une fenêtre.  Une fois qu'une fenêtre redimensionnable est affichée, les utilisateurs peuvent cliquer sur les boutons de réduction, d'agrandissement et de restauration dans la barre de titre de la fenêtre pour modifier son état.  
  
<a name="WindowAppearance"></a>   
## Apparence de la fenêtre  
 Vous modifiez l'apparence de la zone cliente d'une fenêtre en lui ajoutant un contenu qui lui est spécifique, tel que des boutons, des étiquettes et des zones de texte.  Pour configurer la zone non cliente, <xref:System.Windows.Window> fournit plusieurs propriétés, qui incluent <xref:System.Windows.Window.Icon%2A> pour définir l'icône d'une fenêtre et <xref:System.Windows.Window.Title%2A> pour définir son titre.  
  
 Vous pouvez également modifier l'apparence et le comportement d'une bordure de zone non cliente en configurant le mode de redimensionnement d'une fenêtre, le style de fenêtre, et si celle\-ci apparaît sous forme d'un bouton dans la barre des tâches du bureau.  
  
   
  
<a name="Resize_Mode"></a>   
### Mode redimensionnement  
 Selon la propriété <xref:System.Windows.Window.WindowStyle%2A>, vous pouvez contrôler comment \(et si\) les utilisateurs peuvent redimensionner la fenêtre.  Le choix de style de fenêtre détermine si un utilisateur peut redimensionner la fenêtre en faisant glisser sa bordure avec la souris, si les boutons **Réduire**, **Agrandir** et **Redimensionner** apparaissent sur la zone non cliente et, dans ce cas, s'ils sont activés.  
  
 Vous pouvez configurer la manière dont une fenêtre se redimensionne en définissant sa propriété <xref:System.Windows.Window.ResizeMode%2A> qui peut avoir l'une des valeurs d'énumération <xref:System.Windows.ResizeMode> suivantes :  
  
-   <xref:System.Windows.ResizeMode>  
  
-   <xref:System.Windows.ResizeMode>  
  
-   <xref:System.Windows.ResizeMode> \(par défaut\)  
  
-   <xref:System.Windows.ResizeMode>  
  
 Comme avec <xref:System.Windows.Window.WindowStyle%2A>, il est improbable que le mode de redimensionnement d'une fenêtre change pendant sa durée de vie, ce qui signifie que vous le définirez très probablement à partir du balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#ResizeModeWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup2)]  
  
 Notez que vous pouvez détecter si une fenêtre est agrandie, réduite ou restaurée en consultant la propriété <xref:System.Windows.Window.WindowState%2A>.  
  
<a name="Window_Style"></a>   
### Style de fenêtre  
 La bordure exposée à partir de la zone non cliente d'une fenêtre est appropriée pour la plupart des applications.  Toutefois, il arrive que dans certaines circonstances des types de bordures différents soient requis, voire qu'aucune bordure ne soit requise, selon le type de fenêtre.  
  
 Pour contrôler quel type de bordure une fenêtre récupère, vous définissez sa propriété <xref:System.Windows.Window.WindowStyle%2A> avec l'une des valeurs suivantes de l'énumération <xref:System.Windows.WindowStyle> :  
  
-   <xref:System.Windows.WindowStyle>  
  
-   <xref:System.Windows.WindowStyle> \(par défaut\)  
  
-   <xref:System.Windows.WindowStyle>  
  
-   <xref:System.Windows.WindowStyle>  
  
 L'effet de ces styles de fenêtre est représenté dans l'illustration suivante.  
  
 ![Styles de fenêtre](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure6.png "WindowOverviewFigure6")  
  
 Vous pouvez définir <xref:System.Windows.Window.WindowStyle%2A> à l'aide du balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou du code ; comme il est improbable que cela change pendant la durée de vie d'une fenêtre, vous le configurerez très probablement à l'aide du balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#WindowStyleWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup2)]  
  
#### Style de fenêtre non rectangulaire  
 Il existe également des situations où les styles de bordure que <xref:System.Windows.Window.WindowStyle%2A> vous permet d'obtenir ne suffisent pas.  Par exemple, vous pouvez souhaiter créer une application avec une bordure non rectangulaire, semblable à celle du [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)].  
  
 Considérons, par exemple, la fenêtre de la bulle de commentaire représentée dans l'illustration suivante.  
  
 ![Fenêtre non rectangulaire](../../../../docs/framework/wpf/app-development/media/nonrectangularwindowfigure.PNG "NonRectangularWindowFigure")  
  
 Ce type de fenêtre peut être créé en affectant à la propriété <xref:System.Windows.Window.WindowStyle%2A> la valeur <xref:System.Windows.WindowStyle>, et en utilisant un support spécial que <xref:System.Windows.Window> a pour transparence.  
  
 [!code-xml[WindowsOverviewSnippets#TransparentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#TransparentWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup2)]  
  
 Cette combinaison de valeurs indique à la fenêtre de restituer un rendu totalement transparent.  Dans cet état, les ornements de la zone non cliente \(le menu Fermer, les boutons Réduire, Agrandir et Restaurer, etc.\) de la fenêtre ne peuvent pas être utilisés.  Par conséquent, vous devez fournir vos propres ornements.  
  
<a name="Task_Bar_Presence"></a>   
### Présence de la barre des tâches  
 L'apparence par défaut d'une fenêtre inclut un bouton de barre des tâches, comme celui représenté dans l'illustration suivante.  
  
 ![Fenêtre avec un bouton de barre des tâches](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure7.png "WindowOverviewFigure7")  
  
 Certains types de fenêtres ne possèdent pas de bouton de barre des tâches, telles que les boîtes de messages et de dialogue \(consultez [Vue d'ensemble des boîtes de dialogue](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)\).  Vous pouvez contrôler si le bouton de barre des tâches pour une fenêtre est affiché en définissant la propriété <xref:System.Windows.Window.ShowInTaskbar%2A> \(`true` par défaut\).  
  
 [!code-xml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
[!code-xml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup2)]  
  
<a name="SecurityConsiderations"></a>   
## Considérations sur la sécurité  
 <xref:System.Windows.Window> requiert l'autorisation de sécurité `UnmanagedCode` pour être instancié.  Pour les applications installées sur l'ordinateur local et lancées à partir de celui\-ci, cela fait partie du jeu des autorisations accordées à l'application.  
  
 Cela ne fait toutefois pas partie du jeu d'autorisations accordé aux applications lancées à partir de la zone Internet ou de la zone d'intranet local à l'aide de [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)].  Par conséquent, les utilisateurs recevront un avertissement de sécurité [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] et devront élever le jeu d'autorisations pour l'application à Confiance totale.  
  
 En outre, les applications [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ne peuvent pas afficher par défaut de fenêtres ni de boîtes de dialogue.  Pour une discussion sur les considérations relatives à la sécurité des applications autonomes, consultez [Stratégie de sécurité de WPF \- ingénierie de la plateforme](../../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>   
## Autres types de fenêtres  
 <xref:System.Windows.Navigation.NavigationWindow> est une fenêtre conçue pour héberger un contenu navigable.  Pour plus d'informations, consultez [Vue d'ensemble de la navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 Les boîtes de dialogue sont des fenêtres qui sont souvent utilisées pour rassembler des informations d'un utilisateur pour compléter une fonction.  Par exemple, lorsqu'un utilisateur souhaite ouvrir un fichier, la boîte de dialogue **Ouvrir un fichier** est généralement affichée par une application pour obtenir le nom de fichier auprès de l'utilisateur.  Pour plus d'informations, consultez [Vue d'ensemble des boîtes de dialogue](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Window>   
 <xref:System.Windows.MessageBox>   
 <xref:System.Windows.Navigation.NavigationWindow>   
 <xref:System.Windows.Application>   
 [Vue d'ensemble des boîtes de dialogue](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)   
 [Génération d'une application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)