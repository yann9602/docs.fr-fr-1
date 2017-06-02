---
title: "Comment&#160;: cr&#233;er une sc&#232;ne 3D | Microsoft Docs"
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
  - "scènes 3D"
  - "créer, scènes 3D"
  - "scènes, 3D"
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er une sc&#232;ne 3D
Cet exemple montre comment créer un objet 3D qui ressemble à une feuille de papier ayant subi une rotation.  Un élément <xref:System.Windows.Controls.Viewport3D> associé aux composants suivants permettent de créer cette scène 3D simple :  
  
-   Une caméra est créée à l'aide d'une <xref:System.Windows.Media.Media3D.PerspectiveCamera>.  Elle spécifie quelle partie de la scène 3D est visible.  
  
-   Un maillage est créé pour spécifier la forme de l'objet 3D \(feuille de papier\) au moyen de la propriété <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> de <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Une matière à afficher sur la surface de l'objet \(dégradé linéaire dans cet exemple\) est spécifiée au moyen de la propriété <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> du <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Un éclairage destiné à se refléter sur l'objet est créé à l'aide de <xref:System.Windows.Media.Media3D.DirectionalLight>.  
  
## Exemple  
 L'exemple suivant indique comment créer une scène 3D en XAML.  
  
 [!code-xml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## Exemple  
 L'exemple suivant montre comment créer la même scène 3D en code procédural.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## Voir aussi  
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)