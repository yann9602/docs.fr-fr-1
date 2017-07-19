---
title: "Comment&#160;: animer des propri&#233;t&#233;s de mat&#233;riel dans une sc&#232;ne 3D | Microsoft Docs"
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
  - "scènes 3D, animer des propriétés de matériel"
  - "animation, propriétés de matériel dans une scènes 3D"
  - "propriétés de matériel, animer dans des scènes 3D"
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: animer des propri&#233;t&#233;s de mat&#233;riel dans une sc&#232;ne 3D
Cet exemple montre comment animer la propriété <xref:System.Windows.Media.Brush.Opacity%2A> du <xref:System.Windows.Media.Media3D.Material> appliquée à un modèle [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)].  
  
 L'exemple de code suivant définit le <xref:System.Windows.Media.LinearGradientBrush> utilisé comme <xref:System.Windows.Media.Media3D.Material> appliqué à l'objet 3D.  
  
 [!code-xml[Animation3DGallery_snip#AnimateMaterialExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 La propriété <xref:System.Windows.Media.Brush.Opacity%2A> de ce <xref:System.Windows.Media.LinearGradientBrush> est animée à l'aide de l'exemple de code ci\-dessous.  
  
 [!code-xml[Animation3DGallery_snip#AnimateMaterialExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## Exemple  
 Le code suivant montre l'exemple complet.  
  
 [!code-xml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## Voir aussi  
 [Créer une scène 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)