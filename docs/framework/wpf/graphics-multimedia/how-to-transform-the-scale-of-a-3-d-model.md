---
title: "Comment&#160;: transformer l&#39;&#233;chelle d&#39;un mod&#232;le&#160;3D | Microsoft Docs"
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
  - "objets 3D, mettre à l'échelle"
  - "mettre à l'échelle, objets 3D"
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# Comment&#160;: transformer l&#39;&#233;chelle d&#39;un mod&#232;le&#160;3D
Cet exemple montre comment mettre à l'échelle un objet 3D.  Pour mettre à l'échelle un objet 3D, utilisez <xref:System.Windows.Media.Media3D.ScaleTransform3D>.  Les propriétés <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> et <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> redimensionnent l'élément selon le facteur spécifié.  Par exemple, une valeur <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> de 1.5 étire un objet de 150 pour cent par rapport à sa largeur d'origine.  Une valeur <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> de 0.5 réduit la hauteur d'un objet de 50 pour cent.  Le code ci\-dessous montre l'utilisation de <xref:System.Windows.Media.Media3D.ScaleTransform3D> pour transformer l'échelle de <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## Exemple  
 Le code suivant montre l'exemple complet.  
  
 [!code-xml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## Voir aussi  
 [Animer des translations 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)   
 [Créer une scène 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)