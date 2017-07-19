---
title: "Comment&#160;: animer la position et la direction d&#39;une cam&#233;ra dans une sc&#232;ne&#160;3D | Microsoft Docs"
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
  - "scènes 3D, animer la direction d'une caméra"
  - "scènes 3D, animer la position d'une caméra"
  - "animation, direction d'une caméra dans les scènes 3D"
  - "animation, position d'une caméra dans les scènes 3D"
  - "direction d'une caméra, animer dans des scènes 3D"
  - "position d'une caméra, animer dans des scènes 3D"
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: animer la position et la direction d&#39;une cam&#233;ra dans une sc&#232;ne&#160;3D
L'exemple suivant indique comment animer la position d'une caméra et animer la direction dans laquelle elle pointe dans une scène 3D.  Cette opération s'effectue à l'aide de <xref:System.Windows.Media.Animation.Point3DAnimation> et de <xref:System.Windows.Media.Animation.Vector3DAnimation> pour animer respectivement les propriétés <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> et <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> de la <xref:System.Windows.Media.Media3D.PerspectiveCamera>.  Vous pouvez utiliser une animation comme ceci pour modifier la vue du spectateur d'une scène en réponse à un événement.  
  
## Exemple  
 [!code-xml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.Vector3DAnimation>   
 <xref:System.Windows.Media.Animation.Point3DAnimation>   
 [Animer la position et la direction d'une caméra à l'aide d'images clés](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)   
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)