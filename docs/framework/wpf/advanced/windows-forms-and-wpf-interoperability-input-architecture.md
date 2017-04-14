---
title: "Architecture d&#39;entr&#233;e pour l&#39;interop&#233;rabilit&#233; entre Windows Forms et WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ElementHost (clavier et messages)"
  - "architecture d'entrée (interopérabilité WPF)"
  - "interopérabilité (WPF), Windows Forms"
  - "interopérabilité du clavier (WPF)"
  - "messages (WPF)"
  - "boîtes de dialogue non modales (WPF)"
  - "formulaires sans mode"
  - "Windows Forms (WPF), interopérabilité avec"
  - "Windows Forms, interopérabilité WPF"
  - "WindowsFormsHost (clavier et messages)"
ms.assetid: 0eb6f137-f088-4c5e-9e37-f96afd28f235
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Architecture d&#39;entr&#233;e pour l&#39;interop&#233;rabilit&#233; entre Windows Forms et WPF
L'interopérabilité entre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] requiert que les deux technologies disposent du traitement d'entrée au clavier approprié.  Cette rubrique décrit comment ces technologies implémentent le traitement de message et d'entrée au clavier pour permettre l'interopérabilité régulière dans des applications hybrides.  
  
 Cette rubrique contient les sous\-sections suivantes :  
  
-   Formulaires et boîtes de dialogue non modaux  
  
-   Clavier WindowsFormsHost et traitement des messages  
  
-   Clavier ElementHost et traitement des messages  
  
## Formulaires et boîtes de dialogue non modaux  
 Appelez la méthode <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> sur l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> pour ouvrir une boîte de dialogue ou un formulaire non modal à partir d'une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Appelez la méthode <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> sur le contrôle <xref:System.Windows.Forms.Integration.ElementHost> pour ouvrir une page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] non modale dans une application [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## Clavier WindowsFormsHost et traitement des messages  
 Lorsqu'il est hébergé par une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], clavier [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et le traitement des messages est composé des éléments suivants :  
  
-   La classe <xref:System.Windows.Forms.Integration.WindowsFormsHost> acquiert des messages à partir de la boucle de message [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], implémentée par la classe <xref:System.Windows.Interop.ComponentDispatcher>.  
  
-   La classe <xref:System.Windows.Forms.Integration.WindowsFormsHost> crée une boucle de message [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] de remplacement pour s'assurer que le traitement de clavier [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ordinaire se produit.  
  
-   La classe <xref:System.Windows.Forms.Integration.WindowsFormsHost> implémente l'interface <xref:System.Windows.Interop.IKeyboardInputSink> pour coordonner la gestion du focus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Les contrôles <xref:System.Windows.Forms.Integration.WindowsFormsHost> s'inscrivent et démarrent leurs boucles de messages.  
  
 Les sections suivantes décrivent ces parties du processus de façon approfondie.  
  
### Acquisition de messages à partir de la boucle de messages WPF  
 La classe <xref:System.Windows.Interop.ComponentDispatcher> implémente le gestionnaire de boucle de message pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  La classe <xref:System.Windows.Interop.ComponentDispatcher> fournit des raccordements pour permettre aux clients externes de filtrer des messages avant que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les traite.  
  
 L'implémentation d'interopérabilité gère l'événement <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=fullName>, qui permet aux contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] de traiter des messages avant les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### Boucle de message Windows Forms de remplacement  
 Par défaut, la classe <xref:System.Windows.Forms.Application?displayProperty=fullName> contient la boucle de message principale pour les applications [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  Pendant l'interopérabilité, la boucle de message [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne traite pas de messages.  Par conséquent, cette logique doit être reproduite.  Le gestionnaire pour l'événement <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=fullName> exécute les étapes suivantes :  
  
1.  Filtre le message à l'aide de l'interface <xref:System.Windows.Forms.IMessageFilter>.  
  
2.  Appelle la méthode <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=fullName>.  
  
3.  Traduit et distribue le message, si nécessaire.  
  
4.  Passe le message au contrôle d'hébergement, si aucun autre contrôle ne traite le message.  
  
### Implémentation IKeyboardInputSink  
 La boucle de message de remplacement gère la gestion du clavier.  Par conséquent, la méthode <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=fullName> est le seul membre <xref:System.Windows.Interop.IKeyboardInputSink> qui nécessite une implémentation dans la classe <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
 Par défaut, la classe <xref:System.Windows.Interop.HwndHost> retourne `false` pour son implémentation <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>.  Cela empêche la tabulation à partir d'un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vers un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 L'implémentation <xref:System.Windows.Forms.Integration.WindowsFormsHost> de la méthode <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=fullName> exécute les étapes suivantes :  
  
1.  Recherche le premier ou dernier contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contenu par le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> et qui peut recevoir le focus.  Le choix du contrôle dépend des informations de parcours.  
  
2.  Définit le focus sur le contrôle et retourne `true`.  
  
3.  Si aucun contrôle ne peut recevoir le focus, retourne `false`.  
  
### Inscription WindowsFormsHost  
 Lorsque le handle de fenêtre sur un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> est créé, le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> appelle une méthode statique interne qui enregistre sa présence pour la boucle de message.  
  
 Pendant l'inscription, le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> examine la boucle de message.  Si la boucle de message n'a pas été démarrée, le gestionnaire d'événements <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=fullName> est créé.  La boucle de message est considérée être exécutée lorsque le gestionnaire d'événements <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=fullName> est attaché.  
  
 Lorsque le handle de fenêtre est détruit, le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> s'élimine lui\-même de l'inscription.  
  
## Clavier ElementHost et traitement des messages  
 Lorsqu'il est hébergé par une application [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], clavier [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et le traitement des messages est composé des éléments suivants :  
  
-   <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink> et <xref:System.Windows.Interop.IKeyboardInputSite> des implémentations d'interface.  
  
-   Tabulation et touches de direction.  
  
-   Touches de commande et touches de boîte de dialogue.  
  
-   Traitement d'accélérateur [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 Les sections suivantes décrivent ces parties de façon approfondie.  
  
### Implémentations d'interface  
 Dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], les messages du clavier sont routés vers le handle de la fenêtre du contrôle qui a le focus.  Dans le contrôle <xref:System.Windows.Forms.Integration.ElementHost>, ces messages sont routés vers l'élément hébergé.  Pour ce faire, le contrôle <xref:System.Windows.Forms.Integration.ElementHost> fournit une instance de <xref:System.Windows.Interop.HwndSource>.  Si le contrôle <xref:System.Windows.Forms.Integration.ElementHost> a le focus, l'instance de <xref:System.Windows.Interop.HwndSource> route la plupart des entrées au clavier afin qu'elles puissent être traitées par la classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Input.InputManager>.  
  
 La classe <xref:System.Windows.Interop.HwndSource> implémente les interfaces <xref:System.Windows.Interop.IKeyboardInputSink> et <xref:System.Windows.Interop.IKeyboardInputSite>.  
  
 L'interopérabilité de clavier s'appuie sur l'implémentation de la méthode <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> pour gérer la touche TAB et l'entrée de la touche de direction qui déplace le focus en dehors des éléments hébergés.  
  
### Tabulation et touches de direction  
 La logique de sélection [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] est mappée aux méthodes <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> et <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> pour implémenter la navigation avec les touches de direction et la navigation TAB.  La substitution de la méthode <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> réalise ce mappage.  
  
### Touches de commande et touches de boîte de dialogue  
 Pour donner à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la première possibilité de traiter les touches de commande et les touches de boîte de dialogue, le prétraitement de commande [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] est connecté à la méthode <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>.  La substitution de la méthode <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=fullName> connecte les deux technologies.  
  
 Avec la méthode <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>, les éléments hébergés peuvent gérer tout message clé, tel que WM\_KEYDOWN, WM\_KEYUP, WM\_SYSKEYDOWN ou WM\_SYSKEYUP, y compris les touches de commande telles que TABULATION, ENTRÉE, ÉCHAP et les touches de direction.  Si un message clé n'est pas géré, il est renvoyé en haut de la hiérarchie ancêtre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à des fins de gestion.  
  
### Traitement d'accélérateur  
 Pour traiter des accélérateurs correctement, le traitement d'accélérateur [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] doit être connecté à la classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager>.  En outre, tous les messages WM\_CHAR doivent être routés correctement aux éléments hébergés.  
  
 Parce que l'implémentation <xref:System.Windows.Interop.HwndSource> par défaut de la méthode <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> retourne `false`, les messages WM\_CHAR sont traités à l'aide de la logique suivante :  
  
-   La méthode <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=fullName> est substituée pour garantir que tous les messages WM\_CHAR sont envoyés aux éléments hébergés.  
  
-   Si l'utilisateur appuie sur la touche Alt, le message est WM\_SYSCHAR.  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne prétraite pas ce message via la méthode <xref:System.Windows.Forms.Control.IsInputChar%2A>.  Par conséquent, la méthode <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> est substituée pour interroger le <xref:System.Windows.Input.AccessKeyManager> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] afin d'obtenir un accélérateur inscrit.  Si un accélérateur enregistré est trouvé, <xref:System.Windows.Input.AccessKeyManager> le traite.  
  
-   Si l'utilisateur n'appuie pas sur la touche Alt, la classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Input.InputManager> traite l'entrée non gérée.  Si l'entrée est un accélérateur, <xref:System.Windows.Input.AccessKeyManager> le traite.  L'événement <xref:System.Windows.Input.InputManager.PostProcessInput> est géré pour les messages WM\_CHAR qui n'ont pas été traités.  
  
 Lorsque l'utilisateur appuie sur la touche ALT, des aides visuelles de l'accélérateur s'affichent sur l'intégralité du formulaire.  Pour prendre en charge ce comportement, tous les contrôles <xref:System.Windows.Forms.Integration.ElementHost> sur le formulaire actif reçoivent des messages WM\_SYSKEYDOWN, quel que soit le contrôle qui a le focus.  
  
 Les messages sont envoyés uniquement aux contrôles <xref:System.Windows.Forms.Integration.ElementHost> dans le formulaire actif.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>   
 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>   
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)   
 [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)