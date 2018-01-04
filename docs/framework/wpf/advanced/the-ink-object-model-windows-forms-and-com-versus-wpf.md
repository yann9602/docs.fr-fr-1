---
title: "Modèle objet encre : Windows Forms et COM ou WPF"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling ink [WPF]
- InkCanvas control [WPF]
- ink object model [WPF]
- tablet pen [WPF], events [WPF]
- ink [WPF], enabling
- events [WPF], tablet pen
ms.assetid: 577835be-b145-4226-8570-1d309e9b3901
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38c7692d433fb91584718984ef2ad81e563517db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>Modèle objet encre : Windows Forms et COM ou WPF

Il existe essentiellement trois plateformes qui prennent en charge de l’encre numérique : la plateforme Tablet PC Windows Forms, la plateforme Tablet PC COM et le [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] plateforme.  Le partage de plateformes Windows Forms et COM, un modèle objet semblable, mais le modèle objet pour la [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plate-forme est très différente.  Cette rubrique explique les différences à un niveau élevé pour que les développeurs qui ont travaillé avec un modèle objet peuvent de mieux comprendre l’autre.  
  
## <a name="enabling-ink-in-an-application"></a>Activation d’encre dans une Application  
 Les trois plateformes fournissent des objets et des contrôles qui permettent à une application recevoir une entrée d’un stylet.  Les plateformes de COM et Windows Forms sont fournis avec [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) et [ Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) classes.  [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) et [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx) sont des contrôles que vous pouvez ajouter à une application pour collecter de l’encre.  Le [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) et [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) peuvent être attachés à une fenêtre existante pour activer la prise en charge windows et des contrôles personnalisés.  
  
 La plateforme WPF inclut le <xref:System.Windows.Controls.InkCanvas> contrôle.  Vous pouvez ajouter un <xref:System.Windows.Controls.InkCanvas> à votre application et commencer à collecter l’encre immédiatement. Avec la <xref:System.Windows.Controls.InkCanvas>, l’utilisateur peut copier, sélectionner et redimensionner l’encre.  Vous pouvez ajouter d’autres contrôles à le <xref:System.Windows.Controls.InkCanvas>, et l’utilisateur peut écrire à la main sur ces contrôles.  Vous pouvez créer un contrôle personnalisé d’encre compatible en ajoutant une <xref:System.Windows.Controls.InkPresenter> et en collectant ses points de stylet.  
  
 Le tableau suivant répertorie les emplacements pour en savoir plus sur l’activation d’encre dans une application :  
  
|Pour ce faire...|Sur la plateforme WPF...|Sur les plateformes Windows Forms/COM chargées...|  
|-----------------|--------------------------|------------------------------------------|  
|Ajouter un contrôle manuscrite à une application|Consultez [prise en main d’encre](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md).|Consultez [automatique revendications forment l’exemple](http://msdn.microsoft.com/bec4333a-62ca-4254-a39b-04bc2c556992)|  
|Activer l’encre sur un contrôle personnalisé|Consultez [création d’une prise en charge d’entrée de contrôle](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).|Consultez [d’encre Presse-papiers exemple](http://msdn.microsoft.com/a0c42f1c-543d-44f8-83d9-fe810de410ff).|  
  
## <a name="ink-data"></a>Données d’entrée manuscrite  
 Sur les plateformes de COM et Windows Forms [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), et [ Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) chaque exposent un [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) objet. Le [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objet contient les données pour un ou plusieurs [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) des objets et expose des méthodes et des propriétés pour gérer et manipuler ces traits communes.  Le [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objet gère la durée de vie des traits qu’elle contient ; le [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objet crée et supprime les traits qu’il détient.  Chaque [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx) a un identificateur qui est unique au sein de son parent [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) objet.  
  
 Sur la plateforme WPF, la <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> classe possède et gère son propre durée de vie. Un groupe de <xref:System.Windows.Ink.Stroke> objets peuvent être regroupés dans un <xref:System.Windows.Ink.StrokeCollection>, qui fournit des opérations de gestion des données méthodes pour encre communes telles qu’atteint test, de suppression, de transformation et de sérialisation de l’encre. A <xref:System.Windows.Ink.Stroke> peut appartenir à zéro, une ou plusieurs <xref:System.Windows.Ink.StrokeCollection> tous les objets que le temps.  Au lieu d’avoir un [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) objet, le <xref:System.Windows.Controls.InkCanvas> et <xref:System.Windows.Controls.InkPresenter> contiennent un <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>.  
  
 La paire d’illustrations suivante compare les modèles d’objet de données d’encre.  Sur les Windows Forms et les plateformes de COM, le [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) objet contraint la durée de vie de la [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) objets et les paquets de stylet appartiennent aux traits individuels.  Deux ou plusieurs traits peuvent référencer le même [Microsoft.Ink.DrawingAttributes](https://msdn.microsoft.com/library/ms837931.aspx?displayProperty=nameWithType) de l’objet, comme indiqué dans l’illustration suivante.  
  
 ![Diagramme du modèle d’objet manuscrit pour COM &#47; WinForms. ] (../../../../docs/framework/wpf/advanced/media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 Sur le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], chaque <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> est un objet du common language runtime qui existe tant que quelque chose a une référence à celui-ci.  Chaque <xref:System.Windows.Ink.Stroke> références un <xref:System.Windows.Input.StylusPointCollection> et <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType> objet, qui sont également des objets common language runtime.  
  
 ![Diagramme du modèle d’objet manuscrit pour WPF. ] (../../../../docs/framework/wpf/advanced/media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 Le tableau suivant compare la façon d’accomplir certaines tâches courantes sur les [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plate-forme et les plateformes COM et Windows Forms.  
  
|Tâche|Windows Presentation Foundation|COM et Windows Forms|  
|----------|-------------------------------------|---------------------------|  
|Économiser de l’encre|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft.Ink.Ink.Save](https://technet.microsoft.com/library/security/microsoft.ink.ink.save(v=vs.90))|  
|Prise en charge de la charge|Créer un <xref:System.Windows.Ink.StrokeCollection> avec la <xref:System.Windows.Ink.StrokeCollection.%23ctor%2A> constructeur.|[Microsoft.Ink.Ink.Load](https://msdn.microsoft.com/library/microsoft.ink.ink.load(v=vs.90).aspx)|  
|Test de positionnement|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft.Ink.Ink.HitTest](https://msdn.microsoft.com/library/aa515934.aspx)|  
|Copier l’entrée manuscrite|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft.Ink.Ink.ClipboardCopy](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardcopy(v=vs.100).aspx)|  
|Collez une entrée manuscrite|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft.Ink.Ink.ClipboardPaste](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardpaste(v=vs.100).aspx)|  
|Propriétés personnalisées de l’accès sur une collection de traits|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>(les propriétés sont stockées en interne et accessibles via <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>, et <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>)|Utilisez [Microsoft.Ink.Ink.ExtendedProperties](https://msdn.microsoft.com/library/microsoft.ink.ink.extendedproperties(v=vs.100).aspx)|  
  
### <a name="sharing-ink-between-platforms"></a>Partage d’encre entre les plateformes  
 Bien que les plateformes aient des modèles objet différents pour les données de l’encre, il est très facile de partager les données entre les plateformes. Les exemples suivants enregistrent l’encre d’une application Windows Forms et chargent l’encre dans une application Windows Presentation Foundation.  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 Les exemples suivants enregistrent l’encre d’une application Windows Presentation Foundation et chargent l’encre dans une application Windows Forms.  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>Événements du stylet  
 Le [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), et [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) sur les Windows Forms et COM plateformes recevoir des événements lorsque l’utilisateur entrées de stylet de données.  Le [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) ou [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) est attaché à une fenêtre ou un contrôle et peuvent s’abonner aux événements déclenchés par les données d’entrée de tablette.  Le thread sur lequel ces événements se produit dépend si les événements sont déclenchés avec un stylet, une souris, ou par programme.  Pour plus d’informations sur les threads par rapport à ces événements, consultez [considérations générales de Threading](http://msdn.microsoft.com/cf35724f-5f80-4b3e-992a-a9d5ea99aae9) et [Threads sur ce qui peut déclencher un événement](http://msdn.microsoft.com/d1a5ab9b-d474-4ed7-9aa8-b5bdb771934f).  
  
 Sur la plateforme Windows Presentation Foundation, la <xref:System.Windows.UIElement> classe a des événements pour l’entrée de stylet. Cela signifie que chaque contrôle expose l’ensemble des événements de stylet.  Les événements de stylet ont des événements de tunneling/propagation paires et sont toujours effectuées sur le thread d’application.  Pour plus d’informations, consultez [vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Le schéma suivant compare les modèles objet pour les classes qui déclenchent des événements de stylet. Le modèle objet Windows Presentation Foundation affiche uniquement les événements de propagation, pas les équivalents d’événements de tunneling.  
  
 ![Diagramme des événements de stylet dans WPF par rapport à Winforms. ] (../../../../docs/framework/wpf/advanced/media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>Données du stylet  
 Les trois plateformes vous permettent d’intercepter et de manipuler les données qui proviennent du stylet.  Sur les plateformes Windows Forms et COM, ceci est obtenue en créant un [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx), l’attachement d’une fenêtre ou un contrôle à ce dernier et création d’une classe qui implémente le [ Microsoft.StylusInput.IStylusSyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylussyncplugin(v=vs.100).aspx) ou [Microsoft.StylusInput.IStylusAsyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylusasyncplugin(v=vs.100).aspx) interface. Le plug-in personnalisé est ensuite ajouté à la collection de plug-in de la [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx). Pour plus d’informations sur ce modèle objet, consultez [Architecture de the StylusInput APIs](http://msdn.microsoft.com/88bab0ab-df9f-4813-9a9f-9a137813f0b4).  
  
 Sur le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plateforme, le <xref:System.Windows.UIElement> classe expose une collection de plug-ins similaires dans la conception pour le [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx).  Pour intercepter les données de stylet, créez une classe qui hérite de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> et ajouter cet objet à la <xref:System.Windows.UIElement.StylusPlugIns%2A> collection de la <xref:System.Windows.UIElement>. Pour plus d’informations sur cette interaction, consultez [interceptant l’entrée du stylet](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md).  
  
 Sur toutes les plateformes, un pool de threads reçoit les données de l’encre via des événements de stylet et l’envoie au thread d’application.  Pour plus d’informations concernant les threads sur les plateformes COM et Windows, consultez [Threading Considerations for the StylusInput APIs](http://msdn.microsoft.com/5d98768a-c60b-4bb0-8640-9bf38254d41f).  Pour plus d’informations concernant les threads sur le logiciel de présentation de Windows, consultez [le modèle de thread d’encre](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).  
  
 L’illustration suivante compare les modèles objet pour les classes qui reçoivent des données de stylet sur le pool de threads de stylet.  
  
 ![Diagramme de la StylusPlugIn dans modèle WPF par rapport à Winforms. ] (../../../../docs/framework/wpf/advanced/media/ink-stylusplugins.png "Ink_StylusPlugins")
