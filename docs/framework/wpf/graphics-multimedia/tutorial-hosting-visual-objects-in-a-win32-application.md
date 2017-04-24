---
title: "Didacticiel&#160;: h&#233;bergement d&#39;objets visuels dans une application Win32 | Microsoft Docs"
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
  - "hébergement, objets visuels dans du code Win32"
  - "objets visuels dans du code Win32"
  - "code Win32, objets visuels dans"
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Didacticiel&#160;: h&#233;bergement d&#39;objets visuels dans une application Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un environnement riche pour créer des applications.  Toutefois, lorsque vous avez écrit une bonne partie du [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], il peut être plus efficace d'ajouter la fonctionnalité [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à votre application plutôt que de réécrire le code.  Pour fournir le support pour des sous\-systèmes [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisés concurremment dans une application, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un mécanisme pour héberger des objets dans une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
 Ce didacticiel décrit comment écrire une application d'exemple, [Test de  positionnement avec interopérabilité Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=159995), qui héberge des objets visuels [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
   
  
<a name="requirements"></a>   
## Configuration requise  
 Ce didacticiel suppose que avez des connaissances de base en matière de programmation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  Pour une présentation générale de la programmation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Procédure pas à pas : mise en route de WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  Pour une présentation de la programmation [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], consultez les divers manuels qui s'y rapportent, notamment à *La programmation Windows* de Charles Petzold.  
  
> [!NOTE]
>  Ce didacticiel inclut des exemples de code de l'exemple associé.  Toutefois, il n'inclut pas l'exemple de code complet pour une meilleure lisibilité.  Pour l'exemple de code complet, consultez [Test de positionnement avec interopérabilité Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## Création de la fenêtre Win32 hôte  
 La clé d'hébergement d'objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] est la classe <xref:System.Windows.Interop.HwndSource>.  Cette classe encapsule les objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] en leur permettant d'être incorporés dans votre [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] sous la forme d'une fenêtre enfant.  
  
 L'exemple suivant montre le code permettant de créer l'objet <xref:System.Windows.Interop.HwndSource> sous la forme d'une fenêtre de conteneur [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pour les objets visuels.  Pour définir le style, la position et d'autres paramètres de la [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], utilisez l'objet <xref:System.Windows.Interop.HwndSourceParameters>.  
  
 [!code-csharp[VisualsHitTesting#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  La valeur de la propriété <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> ne peut pas être WS\_EX\_TRANSPARENT.  Cela signifie que la fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hôte ne peut pas être transparente.  Pour cette raison, la couleur d'arrière\-plan de la fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hôte a pour valeur la même couleur d'arrière\-plan que sa fenêtre parente.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## Ajout d'objets visuels à la fenêtre Win32 hôte  
 Une fois que vous avez créé une fenêtre de conteneur [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hôte pour les objets visuels, vous pouvez y ajouter des objets visuels.  L'objectif est de veiller à ce que les transformations des objets visuels, telles que les animations, ne s'étendent pas au delà des limites du rectangle englobant de la fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hôte.  
  
 L'exemple suivant montre le code permettant de créer l'objet <xref:System.Windows.Interop.HwndSource> et d'y ajouter des objets visuels.  
  
> [!NOTE]
>  La propriété <xref:System.Windows.Interop.HwndSource.RootVisual%2A> de l'objet <xref:System.Windows.Interop.HwndSource> a pour valeur le premier objet visuel ajouté à la fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hôte.  L'objet visuel racine définit le premier nœud de l'arborescence d'objets visuels.  Tous les objets visuels suivants ajoutés à la fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hôte sont ajoutés comme objets enfants.  
  
 [!code-csharp[VisualsHitTesting#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## Implémentation du filtre de messages Win32  
 La fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hôte des objets visuels nécessite une procédure de filtrage des messages de fenêtre pour gérer les messages envoyés à la fenêtre par la file d'attente d'application.  La procédure de fenêtre reçoit des messages du système [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  Il peut s'agir de messages d'entrée ou de messages de gestion de fenêtre.  Vous pouvez gérer éventuellement un message dans votre procédure de fenêtre ou passer le message au système pour un traitement par défaut.  
  
 L'objet <xref:System.Windows.Interop.HwndSource> que vous avez défini comme parent pour les objets visuels doit faire référence à la procédure de filtre de messages de fenêtre que vous fournissez.  Lorsque vous créez l'objet <xref:System.Windows.Interop.HwndSource>, définissez la propriété <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> pour faire référence à la procédure de fenêtre.  
  
 [!code-csharp[VisualsHitTesting#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 L'exemple suivant montre le code permettant de gérer les messages de relâchement du bouton gauche et du bouton droit de la souris.  La valeur de coordonnée de la position de la souris se trouve dans la valeur du paramètre `lParam`.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## Traitement des messages Win32  
 Le code dans l'exemple suivant montre comment un test de positionnement est effectué par rapport à la hiérarchie d'objets visuels contenue dans la fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hôte.  Vous pouvez déterminer si un point se trouve dans la géométrie d'un objet visuel en utilisant la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> pour spécifier l'objet visuel racine et la valeur de coordonnée à utiliser pour le test de positionnement.  Dans ce cas, l'objet visuel racine est la valeur de la propriété <xref:System.Windows.Interop.HwndSource.RootVisual%2A> de l'objet <xref:System.Windows.Interop.HwndSource>.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Pour plus d'informations sur le test de positionnement par rapport aux objets visuels, consultez [Test de positionnement dans la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
## Voir aussi  
 <xref:System.Windows.Interop.HwndSource>   
 [Test de positionnement avec interopérabilité Win32, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159995)   
 [Test de positionnement dans la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)