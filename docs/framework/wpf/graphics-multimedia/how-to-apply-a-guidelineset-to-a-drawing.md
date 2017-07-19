---
title: "Comment&#160;: appliquer un GuidelineSet &#224; un dessin | Microsoft Docs"
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
  - "graphiques (WPF), GuidelineSet (propriété)"
  - "GuidelineSet (propriété), appliquer à des dessins"
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: appliquer un GuidelineSet &#224; un dessin
Cet exemple montre comment appliquer un <xref:System.Windows.Media.GuidelineSet> à un <xref:System.Windows.Media.DrawingGroup>.  
  
 La classe <xref:System.Windows.Media.DrawingGroup> est le seul type de <xref:System.Windows.Media.Drawing> ayant une propriété <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>.  Pour appliquer un <xref:System.Windows.Media.GuidelineSet> à un autre type de <xref:System.Windows.Media.Drawing>, ajoutez\-le à un <xref:System.Windows.Media.DrawingGroup>, puis appliquez le <xref:System.Windows.Media.GuidelineSet> à votre <xref:System.Windows.Media.DrawingGroup>.  
  
## Exemple  
 L'exemple suivant crée deux objets <xref:System.Windows.Media.DrawingGroup> quasiment identiques ; la seule différence étant que le deuxième <xref:System.Windows.Media.DrawingGroup> a un <xref:System.Windows.Media.GuidelineSet> et que le premier n'en a pas.  
  
 L'illustration suivante indique la sortie de l'exemple.  La différence de rendu entre les deux objets <xref:System.Windows.Media.DrawingGroup> étant très subtile, certaines parties des dessins sont agrandies.  
  
 ![DrawingGroup avec et sans GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm\_drawinggroup\_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## Voir aussi  
 <xref:System.Windows.Media.DrawingGroup>   
 <xref:System.Windows.Media.GuidelineSet>   
 [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)