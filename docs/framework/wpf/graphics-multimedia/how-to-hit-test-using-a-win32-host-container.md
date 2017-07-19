---
title: "Comment&#160;: effectuer un test de positionnement &#224; l&#39;aide d&#39;un conteneur h&#244;te Win32 | Microsoft Docs"
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
  - "tests de positionnement, utiliser des conteneurs hôtes Win32"
  - "objets visuels, tests de positionnement sur"
  - "conteneurs hôtes Win32, tests de positionnement en utilisant"
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: effectuer un test de positionnement &#224; l&#39;aide d&#39;un conteneur h&#244;te Win32
Vous pouvez créer des objets visuels dans une fenêtre [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] en fournissant un conteneur de fenêtre hôte pour les objets visuels.  Pour assurer la gestion des événements pour les objets visuels contenus, vous devez traiter les messages passés à la boucle de filtre de messages du conteneur de fenêtre hôte.  Consultez [Didacticiel : hébergement d'objets visuels dans une application Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) pour plus d'informations sur l'hébergement d'objets visuels dans une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
## Exemple  
 Le code suivant montre comment configurer des gestionnaires d'événement de souris pour une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] utilisée en tant que conteneur hôte pour des objets visuels.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 L'exemple suivant montre comment configurer un [test de positionnement](GTMT) en réponse à l'interception d'événements de souris spécifiques.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 L'objet <xref:System.Windows.Interop.HwndSource> présente le contenu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dans une fenêtre [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]. La valeur de la propriété <xref:System.Windows.Interop.HwndSource.RootVisual%2A> de l'objet <xref:System.Windows.Interop.HwndSource> représente le nœud supérieur de la hiérarchie de l'[arborescence d'éléments visuels](GTMT).  
  
 Pour obtenir l'exemple complet relatif aux objets de test de positionnement à l'aide d'un conteneur hôte Win32, consultez [Test de positionnement avec interopérabilité Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
## Voir aussi  
 <xref:System.Windows.Interop.HwndSource>   
 [Test de positionnement dans la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)   
 [Didacticiel : hébergement d'objets visuels dans une application Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)