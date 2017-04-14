---
title: "Comment&#160;: retourner un UIElement horizontalement ou verticalement | Microsoft Docs"
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
  - "retourner des UIElements"
  - "UIElements, retourner"
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: retourner un UIElement horizontalement ou verticalement
Cet exemple explique comment utiliser <xref:System.Windows.Media.ScaleTransform> pour retourner un <xref:System.Windows.UIElement> horizontalement ou verticalement.  Dans cet exemple, un contrôle <xref:System.Windows.Controls.Button> \(un type de <xref:System.Windows.UIElement>\) est retourné en appliquant un <xref:System.Windows.Media.ScaleTransform> à sa propriété <xref:System.Windows.UIElement.RenderTransform%2A>.  
  
## Exemple  
 L'illustration suivante indique le bouton à retourner.  
  
 ![Bouton sans transformation](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.png "graphicsmm\_buttonflipbeforeflip")  
UIElement à retourner  
  
 Le code ci\-dessous permet de créer le bouton.  
  
 [!code-xml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## Exemple  
 Pour retourner le bouton horizontalement, créez un <xref:System.Windows.Media.ScaleTransform> et affectez la valeur \-1 à sa propriété <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>.  Appliquez <xref:System.Windows.Media.ScaleTransform> à la propriété <xref:System.Windows.UIElement.RenderTransform%2A> du bouton.  
  
 [!code-xml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![Bouton renvoyé horizontalement autour de &#40;0,0&#41;](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.png "graphicsmm\_buttonfliphorizontalflip\_displaced")  
Bouton après l'application de ScaleTransform  
  
## Exemple  
 Comme vous pouvez le constater dans l'illustration ci\-dessus, le bouton a été retourné, mais il a également été déplacé,  car il a été retourné à partir de son coin supérieur gauche.  Pour retourner le bouton, vous souhaitez appliquer <xref:System.Windows.Media.ScaleTransform> à son centre plutôt qu'à son coin.  Pour appliquer <xref:System.Windows.Media.ScaleTransform> au centre du bouton, la méthode la plus simple consiste à définir la propriété <xref:System.Windows.UIElement.RenderTransformOrigin%2A> du bouton sur 0.5, 0.5.  
  
 [!code-xml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![Bouton renvoyé horizontalement autour de son centre](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.png "graphicsmm\_buttonfliphorizontalflip\_inplace")  
Bouton avec un RenderTransformOrigin de 0.5, 0.5  
  
## Exemple  
 Pour retourner le bouton verticalement, définissez la propriété <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> de l'objet <xref:System.Windows.Media.ScaleTransform> au lieu de sa propriété <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>.  
  
 [!code-xml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![Bouton renvoyé verticalement autour de son centre](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.png "graphicsmm\_buttonflipverticalflip\_inplace")  
Bouton retourné verticalement  
  
## Voir aussi  
 [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)