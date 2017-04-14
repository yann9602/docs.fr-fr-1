---
title: "Comment&#160;: animer la couleur ou l&#39;opacit&#233; d&#39;un SolidColorBrush | Microsoft Docs"
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
  - "animation, couleur de SolidColorBrush"
  - "animation, opacité de SolidColorBrush"
  - "couleurs, animer"
  - "opacité, animer"
  - "SolidColorBrush, animer la couleur de"
  - "SolidColorBrush, animer l'opacité de"
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: animer la couleur ou l&#39;opacit&#233; d&#39;un SolidColorBrush
Cet exemple indique comment animer les <xref:System.Windows.Media.SolidColorBrush.Color%2A> et <xref:System.Windows.Media.Brush.Opacity%2A> d'un <xref:System.Windows.Media.SolidColorBrush>.  
  
## Exemple  
 L'exemple suivant utilise trois animations pour animer les <xref:System.Windows.Media.SolidColorBrush.Color%2A> et <xref:System.Windows.Media.Brush.Opacity%2A> d'un <xref:System.Windows.Media.SolidColorBrush>.  
  
-   La première animation, une <xref:System.Windows.Media.Animation.ColorAnimation>, modifie la couleur du pinceau en <xref:System.Windows.Media.Colors.Gray%2A> lorsque la souris entre dans le rectangle.  
  
-   L'animation suivante, une autre <xref:System.Windows.Media.Animation.ColorAnimation>, modifie la couleur du pinceau en <xref:System.Windows.Media.Colors.Orange%2A> lorsque la souris quitte le rectangle.  
  
-   La dernière animation, une <xref:System.Windows.Media.Animation.DoubleAnimation>, modifie l'opacité du pinceau en 0.0 lorsque l'utilisateur clique sur le bouton gauche de la souris.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Pour obtenir un exemple plus complet qui montre comment animer les différents types de pinceaux, consultez [Pinceaux, exemple](http://go.microsoft.com/fwlink/?LinkID=159973).  Pour plus d'informations sur l'animation, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Pour des raisons de cohérence avec d'autres exemples d'animation, les versions de code de cet exemple utilisent un objet <xref:System.Windows.Media.Animation.Storyboard> pour appliquer leurs animations.  Toutefois, lors de l'application d'une seule animation dans le code, il est plus simple d'utiliser la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> qu'un <xref:System.Windows.Media.Animation.Storyboard>.  Pour obtenir un exemple, consultez [Animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## Voir aussi  
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [Pinceaux, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159973)