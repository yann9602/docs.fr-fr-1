---
title: "Comment&#160;: appliquer un mat&#233;riau &#224; l&#39;avant et &#224; l&#39;arri&#232;re d&#39;un objet&#160;3D | Microsoft Docs"
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
  - "objets 3D, appliquer la classe Material"
  - "classes, Matériau"
  - "Material (classe), appliquer aux deux côtés d'un objet 3D"
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: appliquer un mat&#233;riau &#224; l&#39;avant et &#224; l&#39;arri&#232;re d&#39;un objet&#160;3D
L'exemple suivant indique comment appliquer un <xref:System.Windows.Media.Media3D.Material> à l'avant et à l'arrière d'un objet 3D et comment animer cet objet pour afficher ses deux côtés.  La propriété <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> d'un <xref:System.Windows.Media.Media3D.GeometryModel3D> est utilisée pour appliquer un <xref:System.Windows.Media.Brush> rouge à la face avant de l'objet et la propriété <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> du <xref:System.Windows.Media.Media3D.GeometryModel3D> est utilisée pour appliquer un <xref:System.Windows.Media.Brush> bleu à la face arrière de l'objet.  Le code suivant montre l'application des matériaux sur l'objet :  
  
 [!code-xml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## Exemple  
 Le code suivant montre l'exemple complet.  
  
 [!code-xml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## Voir aussi  
 [Créer une scène 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [Animer des propriétés de matériel dans une scène 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)   
 [Appliquer un matériau émissif à un objet 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)