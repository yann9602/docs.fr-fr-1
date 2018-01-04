---
title: "Architecture d'entrée pour l'interopérabilité entre Windows Forms et WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- input architecture [WPF interoperability]
- messages [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- modeless forms [WPF]
- ElementHost keyboard and messages [WPF]
- keyboard interoperation [WPF]
- WindowsFormsHost keyboard and messages [WPF]
- modeless dialog boxes [WPF]
ms.assetid: 0eb6f137-f088-4c5e-9e37-f96afd28f235
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a246a3297d212eabc31bf2ac9d000aeb56329d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Architecture d'entrée pour l'interopérabilité entre Windows Forms et WPF
Interopérabilité entre le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] requiert que les deux technologies disposent du traitement d’entrée au clavier approprié. Cette rubrique décrit comment ces technologies implémentent le clavier et traitement pour permettre l’interopérabilité régulière dans des applications hybrides de messages.  
  
 Cette rubrique contient les sous-sections suivantes :  
  
-   Les boîtes de dialogue et les formulaires non modales  
  
-   Clavier WindowsFormsHost et traitement des messages  
  
-   Clavier ElementHost et traitement des messages  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Les boîtes de dialogue et les formulaires non modales  
 Appelez le <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> méthode sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément pour ouvrir une zone de formulaire ou de la boîte de dialogue non modale à partir un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-application basée sur.  
  
 Appelez le <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> méthode sur le <xref:System.Windows.Forms.Integration.ElementHost> contrôle à ouvrir un non modal [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page dans un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-application basée sur.  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>Clavier WindowsFormsHost et traitement des messages  
 Lorsqu’il est hébergé par un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-en fonction de l’application, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] clavier et le message de traitement se compose des éléments suivants :  
  
-   Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> classe acquiert des messages à partir de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] boucle de message, qui est implémentée par la <xref:System.Windows.Interop.ComponentDispatcher> classe.  
  
-   Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> classe crée un substitut [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] boucle de message pour vous assurer qu’ordinaire [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] clavier traitement se produit.  
  
-   Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> la classe implémente le <xref:System.Windows.Interop.IKeyboardInputSink> interface pour coordonner la gestion du focus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôles s’inscrivent et démarrent leurs boucles de messages.  
  
 Les sections suivantes décrivent ces parties du processus plus en détail.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>Acquisition de Messages à partir de la boucle de messages WPF  
 Le <xref:System.Windows.Interop.ComponentDispatcher> classe implémente le Gestionnaire de boucle de message pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le <xref:System.Windows.Interop.ComponentDispatcher> classe fournissant des connexions pour activer les clients externes pour filtrer les messages avant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les traite.  
  
 L’implémentation d’interopérabilité gère le <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> événement, ce qui permet de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] permettant de traiter des messages avant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôles.  
  
### <a name="surrogate-windows-forms-message-loop"></a>Boucle de Message de remplacement Windows Forms  
 Par défaut, le <xref:System.Windows.Forms.Application?displayProperty=nameWithType> classe contient la boucle de messages principale pour [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] applications. Lors de l’interopérabilité, la [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] message boucle ne traite pas les messages. Par conséquent, cette logique doit être reproduite. Le gestionnaire pour le <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> événement effectue les étapes suivantes :  
  
1.  Filtres de message à l’aide du <xref:System.Windows.Forms.IMessageFilter> interface.  
  
2.  Appelle le <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> (méthode).  
  
3.  Traduit et distribue le message, si nécessaire.  
  
4.  Transmet le message au contrôle d’hébergement, si aucun autre contrôle ne traite le message.  
  
### <a name="ikeyboardinputsink-implementation"></a>Implémentation IKeyboardInputSink  
 La boucle de message de remplacement gère la gestion du clavier. Par conséquent, le <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> (méthode) est le seul <xref:System.Windows.Interop.IKeyboardInputSink> membre qui nécessite une implémentation dans la <xref:System.Windows.Forms.Integration.WindowsFormsHost> classe.  
  
 Par défaut, le <xref:System.Windows.Interop.HwndHost> classe retourne `false` pour son <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> implémentation. Cela empêche la tabulation à partir d’un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le contrôle à un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle.  
  
 Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> mise en oeuvre de la <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> méthode effectue les étapes suivantes :  
  
1.  Recherche le premier ou dernier [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle contenu dans le <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle et qui peut recevoir le focus. Le choix du contrôle dépend des informations de parcours.  
  
2.  Définit le focus au contrôle et renvoie `true`.  
  
3.  Si aucun contrôle ne peut recevoir le focus, retourne `false`.  
  
### <a name="windowsformshost-registration"></a>Inscription WindowsFormsHost  
 Lorsque le handle de fenêtre à un <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle est créé, le <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle appelle une méthode statique interne qui enregistre sa présence pour la boucle de messages.  
  
 Pendant l’inscription, le <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle examine la boucle de messages. Si la boucle de message n’a pas été démarrée, le <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> Gestionnaire d’événements est créé. La boucle de messages est considérée être exécutée lorsque la <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> Gestionnaire d’événements est attaché.  
  
 Quand le handle de fenêtre est détruit, la <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle lui-même supprime l’inscription.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>Clavier ElementHost et traitement des messages  
 Lorsqu’il est hébergé par un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clavier et le message de traitement se compose des éléments suivants :  
  
-   <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>, et <xref:System.Windows.Interop.IKeyboardInputSite> implémentations d’interface.  
  
-   Touches de direction et de tabulation.  
  
-   Touches de commande et les touches de boîte de dialogue.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]traitement d’accélérateur.  
  
 Les sections suivantes décrivent ces parties plus en détail.  
  
### <a name="interface-implementations"></a>Implémentations d’interface  
 Dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], les messages de clavier sont routés vers le handle de fenêtre du contrôle qui a le focus. Dans la <xref:System.Windows.Forms.Integration.ElementHost> contrôle, ces messages sont routés vers l’élément hébergé. Pour ce faire, le <xref:System.Windows.Forms.Integration.ElementHost> contrôle fournit une <xref:System.Windows.Interop.HwndSource> instance. Si le <xref:System.Windows.Forms.Integration.ElementHost> contrôle a le focus, le <xref:System.Windows.Interop.HwndSource> instance achemine la plupart des entrées au clavier afin qu’elles puissent être traitées par le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> classe.  
  
 Le <xref:System.Windows.Interop.HwndSource> la classe implémente le <xref:System.Windows.Interop.IKeyboardInputSink> et <xref:System.Windows.Interop.IKeyboardInputSite> interfaces.  
  
 Interopérabilité de clavier s’appuie sur l’implémentation de la <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> méthode pour gérer la touche TAB et une flèche de clé d’entrée qui déplace le focus en dehors des éléments hébergés.  
  
### <a name="tabbing-and-arrow-keys"></a>TAB et les touches de direction  
 Le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] une logique de sélection est mappée à la <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> et <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> navigation de clé de méthodes à implémenter la tabulation et flèche. Substitution de la <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> méthode réalise ce mappage.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Touches de commande et des touches de boîte de dialogue  
 Pour permettre à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’offre la possibilité de traiter les touches de commande et les clés de la boîte de dialogue, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] prétraitement de commande est connecté à la <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> (méthode). Substitution de la <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> méthode connecte les deux technologies.  
  
 Avec la <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> méthode, les éléments hébergés peuvent gérer tout message clé, tel que WM_KEYDOWN, WM_KEYUP, WM_SYSKEYDOWN ou WM_SYSKEYUP, y compris des touches de commande, telles que les touches de tabulation, entrée, ÉCHAP et flèche. Si un message de touche n’est pas géré, il est envoyé le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hiérarchie ancêtre pour la gestion.  
  
### <a name="accelerator-processing"></a>Traitement d’accélérateur  
 Pour traiter des accélérateurs correctement, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] traitement d’accélérateur doit être connecté à la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> classe. En outre, tous les messages WM_CHAR doivent être routés correctement aux éléments hébergés.  
  
 Étant donné que la valeur par défaut <xref:System.Windows.Interop.HwndSource> implémentation de la <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> méthode retourne `false`, les messages WM_CHAR sont traités à l’aide de la logique suivante :  
  
-   Le <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> méthode est substituée pour garantir que tous les messages WM_CHAR sont envoyés aux éléments hébergés.  
  
-   Si la touche ALT est enfoncée, le message est WM_SYSCHAR. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ne prétraite pas ce message via le <xref:System.Windows.Forms.Control.IsInputChar%2A> (méthode). Par conséquent, le <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> méthode est substituée pour interroger le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> pour un accélérateur enregistré. Si un accélérateur enregistré est trouvé, <xref:System.Windows.Input.AccessKeyManager> traite.  
  
-   Si la touche ALT n’est pas activée, le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> classe traite l’entrée non gérée. Si l’entrée est un accélérateur, la <xref:System.Windows.Input.AccessKeyManager> traite. Le <xref:System.Windows.Input.InputManager.PostProcessInput> l’événement est géré pour les messages WM_CHAR qui n’ont pas été traités.  
  
 Lorsque l’utilisateur appuie sur la touche ALT, les signaux visuels accélérateur sont affichent sur l’intégralité du formulaire. Pour prendre en charge ce comportement, tous les <xref:System.Windows.Forms.Integration.ElementHost> contrôles sur le formulaire actif reçoivent des messages WM_SYSKEYDOWN, quel contrôle a le focus.  
  
 Les messages sont envoyés uniquement à <xref:System.Windows.Forms.Integration.ElementHost> contrôles dans le formulaire actif.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>  
 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
