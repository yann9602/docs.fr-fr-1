---
title: "Comment : retourner un UIElement horizontalement ou verticalement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 84d1360246141cfa565d669fff108e3e4db3ce33
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a>Comment : retourner un UIElement horizontalement ou verticalement
Cet exemple montre comment utiliser un <xref:System.Windows.Media.ScaleTransform> pour retourner un <xref:System.Windows.UIElement> horizontalement ou verticalement. Dans cet exemple, un <xref:System.Windows.Controls.Button> contrôle (un type de <xref:System.Windows.UIElement>) est retourné en appliquant un <xref:System.Windows.Media.ScaleTransform> à son <xref:System.Windows.UIElement.RenderTransform%2A> propriété.  
  
## <a name="example"></a>Exemple  
 L’illustration suivante montre le bouton à retourner.  
  
 ![Un bouton sans transformation](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")  
UIElement à retourner  
  
 Voici le code qui crée le bouton.  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a>Exemple  
 Pour retourner le bouton horizontalement, créez un <xref:System.Windows.Media.ScaleTransform> et définir son <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> propriété sur -1. Appliquer le <xref:System.Windows.Media.ScaleTransform> au bouton <xref:System.Windows.UIElement.RenderTransform%2A> propriété.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![Un bouton renvoyé horizontalement autour de &#40; 0,0 &#41; ] (../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")  
Bouton après l’application de ScaleTransform  
  
## <a name="example"></a>Exemple  
 Comme vous pouvez le voir dans l’illustration précédente, le bouton a été retourné, mais il a également été déplacé. C’est parce que le bouton a été retourné à partir de son coin supérieur gauche. Pour retourner le bouton, vous souhaitez appliquer le <xref:System.Windows.Media.ScaleTransform> à son centre, pas son coin. Un moyen simple pour appliquer la <xref:System.Windows.Media.ScaleTransform> aux boutons center consiste à définir du bouton <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriété 0,5, 0,5.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![Bouton renvoyé horizontalement autour de son centre](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")  
Le bouton avec un RenderTransformOrigin de 0,5, 0,5  
  
## <a name="example"></a>Exemple  
 Pour retourner le bouton verticalement, définissez la <xref:System.Windows.Media.ScaleTransform> l’objet <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriété à la place de son <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> propriété.  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![Bouton renvoyé verticalement autour de son centre](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")  
Bouton retourné verticalement  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
