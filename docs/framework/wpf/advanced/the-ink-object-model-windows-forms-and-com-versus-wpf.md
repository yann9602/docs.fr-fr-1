---
title: "Mod&#232;le objet encre&#160;: Windows Forms et COM ou WPF | Microsoft Docs"
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
  - "activer l'encre"
  - "événements, stylet"
  - "encre (modèle objet)"
  - "encre, activer"
  - "InkCanvas (contrôle)"
  - "stylet, événements"
ms.assetid: 577835be-b145-4226-8570-1d309e9b3901
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Mod&#232;le objet encre&#160;: Windows Forms et COM ou WPF
Il existe essentiellement trois plateformes qui prennent en charge l'encre numérique : la plateforme Tablet PC Windows Forms, la plateforme Tablet PC COM et la plateforme [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  Les plateformes Windows Forms et COM partagent un modèle objet semblable, mais le modèle objet de la plateforme [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est relativement différent.  Cette rubrique étudie les différences à un haut niveau pour que les développeurs qui ont travaillé avec un modèle objet puissent mieux comprendre les autres.  
  
## Activation d'encre dans une application  
 Les trois plateformes fournissent des objets et des contrôles qui permettent à une application de recevoir l'entrée d'un stylet.  Les plateformes Windows Forms et COM sont fournies avec les classes <xref:Microsoft.Ink.InkPicture>, <xref:Microsoft.Ink.InkEdit>, <xref:Microsoft.Ink.InkOverlay> et <xref:Microsoft.Ink.InkCollector>.  <xref:Microsoft.Ink.InkPicture> et <xref:Microsoft.Ink.InkEdit> sont des contrôles que vous pouvez ajouter à une application pour collecter de l'encre.  <xref:Microsoft.Ink.InkOverlay> et <xref:Microsoft.Ink.InkCollector> peuvent être attachés à une fenêtre existante pour permettre aux fenêtres et aux contrôles personnalisés de prendre en charge l'écriture manuscrite.  
  
 La plateforme WPF inclut le contrôle <xref:System.Windows.Controls.InkCanvas>.  Vous pouvez ajouter un <xref:System.Windows.Controls.InkCanvas> à votre application et commencer à collecter l'encre immédiatement.  Avec le <xref:System.Windows.Controls.InkCanvas>, l'utilisateur peut copier, sélectionner et redimensionner l'encre.  Vous pouvez ajouter d'autres contrôles au <xref:System.Windows.Controls.InkCanvas> et l'utilisateur peut écrire à la main sur ces contrôles.  Vous pouvez créer un contrôle personnalisé prenant en charge l'écriture manuscrite en lui ajoutant un <xref:System.Windows.Controls.InkPresenter> et en collectant ses points de stylet.  
  
 Le tableau suivant indique comment en apprendre davantage sur l'activation de l'encre dans une application :  
  
|Pour…|Sur la plateforme WPF...|Sur les plateformes Windows Forms\/COM…|  
|-----------|------------------------------|---------------------------------------------|  
|Ajouter un contrôle prenant en charge l'écriture manuscrite à une application|Consultez [Débuter avec l'encre](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md).|Consultez [Auto Claims Form Sample](http://msdn.microsoft.com/fr-fr/bec4333a-62ca-4254-a39b-04bc2c556992)|  
|Activer l'encre sur un contrôle personnalisé|Consultez [Création d'un contrôle d'entrée d'encre](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).|Consultez [Ink Clipboard Sample](http://msdn.microsoft.com/fr-fr/a0c42f1c-543d-44f8-83d9-fe810de410ff).|  
  
## Données de l'encre  
 Sur les plateformes Windows Forms et COM, <xref:Microsoft.Ink.InkCollector>, <xref:Microsoft.Ink.InkOverlay>, <xref:Microsoft.Ink.InkEdit> et <xref:Microsoft.Ink.InkPicture> exposent chacun un objet <xref:Microsoft.Ink.Ink?displayProperty=fullName>.  L'objet <xref:Microsoft.Ink.Ink> contient les données pour un ou plusieurs objets <xref:Microsoft.Ink.Stroke?displayProperty=fullName> et expose des méthodes et des propriétés communes pour gérer et manipuler ces traits.  L'objet <xref:Microsoft.Ink.Ink> gère la durée de vie des traits qu'il contient ; l'objet <xref:Microsoft.Ink.Ink> crée et supprime les traits qu'il possède.  Chaque <xref:Microsoft.Ink.Stroke> a un identificateur qui est unique dans son objet <xref:Microsoft.Ink.Ink> parent.  
  
 Sur la plateforme WPF, la classe <xref:System.Windows.Ink.Stroke?displayProperty=fullName> possède et gère sa propre durée de vie.  Un groupe d'objets <xref:System.Windows.Ink.Stroke> peut être collecté dans un <xref:System.Windows.Ink.StrokeCollection> qui fournit des méthodes pour les opérations de gestion des données de l'encre communes telles que le test d'atteinte, l'effacement, la transformation et la sérialisation de l'encre.  Un <xref:System.Windows.Ink.Stroke> peut appartenir à aucun, un ou plusieurs objets <xref:System.Windows.Ink.StrokeCollection> à un moment donné.  Au lieu d'avoir un objet <xref:Microsoft.Ink.Ink?displayProperty=fullName>, <xref:System.Windows.Controls.InkCanvas> et <xref:System.Windows.Controls.InkPresenter> contiennent un <xref:System.Windows.Ink.StrokeCollection?displayProperty=fullName>.  
  
 Les illustrations suivantes comparent les modèles objet des données de l'encre.  Sur les plateformes Windows Forms et COM, l'objet <xref:Microsoft.Ink.Ink?displayProperty=fullName> contraint la durée de vie des objets <xref:Microsoft.Ink.Stroke?displayProperty=fullName>, et les paquets de stylet appartiennent aux traits individuels.  Deux ou plusieurs traits peuvent référencer le même objet <xref:Microsoft.Ink.DrawingAttributes?displayProperty=fullName>, comme indiqué dans l'illustration suivante.  
  
 ![Diagramme du Modèle d'objet manuscrit pour COM&#47;Winforms.](../../../../docs/framework/wpf/advanced/media/ink-inkownsstrokes.png "Ink\_InkOwnsStrokes")  
  
 Sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], chaque <xref:System.Windows.Ink.Stroke?displayProperty=fullName> est un objet Common Language Runtime qui existe tant que quelque chose lui est référencé.  Chaque <xref:System.Windows.Ink.Stroke> référence des objets <xref:System.Windows.Input.StylusPointCollection> et <xref:System.Windows.Ink.DrawingAttributes?displayProperty=fullName> qui sont également des objets Common Language Runtime.  
  
 ![Diagramme du Modèle d'objet manuscrit pour WPF.](../../../../docs/framework/wpf/advanced/media/ink-wpfinkobjectmodel.png "Ink\_WPFInkObjectModel")  
  
 Le tableau suivant compare l'exécution des tâches courantes sur la plateforme [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] et les plateformes Windows Forms et COM.  
  
|Tâche|Windows Presentation Foundation|Windows Forms et COM|  
|-----------|-------------------------------------|--------------------------|  
|Enregistrer l'encre|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|<xref:Microsoft.Ink.Ink.Save%2A>|  
|Charger l'encre|Créer un <xref:System.Windows.Ink.StrokeCollection> avec le constructeur <xref:System.Windows.Ink.StrokeCollection.%23ctor%28System.IO.Stream%29?displayProperty=fullName>.|[M:Microsoft.Ink.Ink.Load\(System.Byte\<xref:Microsoft.Ink.Ink.Load%2A>|  
|Test d'atteinte|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|<xref:Microsoft.Ink.Ink.HitTest%2A>|  
|Copier l'encre|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|<xref:Microsoft.Ink.Ink.ClipboardCopy%2A>|  
|Coller l'encre|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|<xref:Microsoft.Ink.Ink.ClipboardPaste%2A>|  
|Accéder aux propriétés personnalisées sur une collection de traits|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> \(les propriétés sont stockées en interne et accessibles via <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A> et <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>\)|Utiliser <xref:Microsoft.Ink.Ink.ExtendedProperties%2A>|  
  
### Partage d'encre entre les plateformes  
 Bien que les plateformes aient des modèles objet différents pour les données de l'encre, le partage des données entre les plateformes est très facile.  Les exemples suivants enregistrent l'encre d'une application Windows Forms et chargent l'encre dans une application Windows Presentation Foundation.  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 Les exemples suivants enregistrent l'encre d'une application Windows Presentation Foundation et chargent l'encre dans une application Windows Forms.  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]  
  
## Événements du stylet  
 <xref:Microsoft.Ink.InkOverlay>, <xref:Microsoft.Ink.InkCollector> et <xref:Microsoft.Ink.InkPicture>, sur les plateformes Windows Forms et COM, reçoivent des événements lorsque l'utilisateur entre les données du stylet.  <xref:Microsoft.Ink.InkOverlay> ou <xref:Microsoft.Ink.InkCollector> est attaché à une fenêtre ou à un contrôle et peut s'abonner aux événements déclenchés par les données d'entrée de tablette.  Le thread sur lequel ces événements se produisent varie selon que les événements sont déclenchés avec un stylet, une souris ou un programme.  Pour plus d'informations sur les threads liés à ces événements, consultez [General Threading Considerations](http://msdn.microsoft.com/fr-fr/cf35724f-5f80-4b3e-992a-a9d5ea99aae9) et [Threads on Which an Event Can Fire](http://msdn.microsoft.com/fr-fr/d1a5ab9b-d474-4ed7-9aa8-b5bdb771934f).  
  
 Sur la plateforme Windows Presentation Foundation, la classe <xref:System.Windows.UIElement> dispose d'événements pour la saisie effectuée à l'aide du stylet.  Cela signifie que chaque contrôle expose le jeu complet d'événements de stylet.  Les événements de stylet ont des paires d'événements de tunneling\/propagation et se produisent toujours sur le thread d'application.  Pour plus d'informations, consultez [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Le diagramme suivant compare les modèles objet pour les classes qui déclenchent des événements de stylet.  Le modèle objet Windows Presentation Foundation affiche uniquement les événements de propagation, pas les équivalents d'événements de tunneling.  
  
 ![Diagramme des événements de stylet dans WPF par rapport à Winforms.](../../../../docs/framework/wpf/advanced/media/ink-stylusevents.png "Ink\_StylusEvents")  
  
## Données de stylet  
 Les trois plateformes fournissent des méthodes pour intercepter et manipuler les données issues d'un stylet.  Sur les plateformes Windows Forms et COM, il convient de créer un <xref:Microsoft.StylusInput.RealTimeStylus>, d'y attacher une fenêtre ou un contrôle et de créer une classe qui implémente l'interface <xref:Microsoft.StylusInput.IStylusSyncPlugin> ou <xref:Microsoft.StylusInput.IStylusAsyncPlugin>.  Puis, le plug\-in personnalisé est ajouté à la collection de plug\-in du <xref:Microsoft.StylusInput.RealTimeStylus>.  Pour plus d'informations sur ce modèle objet, consultez [Architecture of the StylusInput APIs](http://msdn.microsoft.com/fr-fr/88bab0ab-df9f-4813-9a9f-9a137813f0b4).  
  
 Sur la plateforme [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], la classe <xref:System.Windows.UIElement> expose une collection de plug\-in, dont la conception est semblable au <xref:Microsoft.StylusInput.RealTimeStylus>.  Pour intercepter les données de stylet, créez une classe qui hérite de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> et ajoutez l'objet à la collection <xref:System.Windows.UIElement.StylusPlugIns%2A> du <xref:System.Windows.UIElement>.  Pour plus d'informations sur cette interaction, consultez [Interception d'entrée à partir du stylet](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md).  
  
 Sur toutes les plateformes, un pool de threads reçoit les données de l'encre via des événements de stylet et les envoie au thread d'application.  Pour plus d'informations concernant les threads sur les plateformes COM et Windows, consultez [Threading Considerations for the StylusInput APIs](http://msdn.microsoft.com/fr-fr/5d98768a-c60b-4bb0-8640-9bf38254d41f).  Pour plus d'informations concernant les threads sur Windows Presentation Software, consultez [Modèle de thread de l'encre](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).  
  
 L'illustration suivante compare les modèles objet pour les classes qui reçoivent les données de stylet sur le pool de threads de stylet.  
  
 ![Diagramme du modèle StylusPlugin dans WPF par rapport à Winforms.](../../../../docs/framework/wpf/advanced/media/ink-stylusplugins.png "Ink\_StylusPlugins")