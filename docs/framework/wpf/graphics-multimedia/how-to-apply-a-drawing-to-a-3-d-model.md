---
title: "Comment&#160;: appliquer un dessin &#224; un mod&#232;le 3D | Microsoft Docs"
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
  - "modèles 3D, appliquer des dessins à"
  - "dessins, appliquer à des modèles 3D"
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: appliquer un dessin &#224; un mod&#232;le 3D
Cet exemple montre comment utiliser un <xref:System.Windows.Media.DrawingBrush> comme <xref:System.Windows.Media.Media3D.Material> appliqué à un modèle [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)].  
  
 Le code suivant définit un <xref:System.Windows.Media.DrawingGroup> comme contenu d'un <xref:System.Windows.Media.DrawingBrush>.  Le <xref:System.Windows.Media.DrawingBrush> est défini comme la propriété <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> du <xref:System.Windows.Media.Media3D.DiffuseMaterial> appliqué à un plan [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)].  
  
 **Remarque :** il est souvent souhaitable de définir des objets et valeurs complexes comme le dessin ci\-dessous comme des ressources pouvant être réutilisées et simplifiant votre code.  Pour plus d'informations, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 [!code-xml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## Exemple  
 Le code suivant montre l'exemple complet.  
  
 [!code-xml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## Voir aussi  
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [Créer une scène 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)