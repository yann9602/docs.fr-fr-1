---
title: "Comment&#160;: appliquer une transformation &#224; un &#233;l&#233;ment lorsqu&#39;un &#233;v&#233;nement se produit | Microsoft Docs"
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
  - "graphiques, transformations en tant que réponses à des événements"
  - "LayoutTransform (propriété)"
  - "propriétés, LayoutTransform"
  - "propriétés, RenderTransform"
  - "RenderTransform (propriété)"
  - "transformations en tant que réponses à des événements"
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: appliquer une transformation &#224; un &#233;l&#233;ment lorsqu&#39;un &#233;v&#233;nement se produit
Cet exemple montre comment appliquer un <xref:System.Windows.Media.ScaleTransform> lorsqu'un événement se produit.  Le concept présenté ici est le même que vous utilisez pour l'application d'autres types de transformations.  Pour plus d'informations sur les types de transformations disponibles, consultez la classe <xref:System.Windows.Media.Transform> ou [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
 Voici deux manières d'appliquer une transformation à un élément :  
  
-   Si vous *ne* voulez *pas* que la transformation affecte la disposition, utilisez la propriété <xref:System.Windows.UIElement.RenderTransform%2A> de l'élément.  
  
-   Si vous voulez que la transformation affecte la disposition, utilisez la propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A> de l'élément.  
  
 L'exemple suivant applique un <xref:System.Windows.Media.ScaleTransform> à la propriété <xref:System.Windows.UIElement.RenderTransform%2A> d'un bouton.  Lorsque la souris est placé sur le bouton, les propriétés <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> de <xref:System.Windows.Media.ScaleTransform> ont la valeur `2`, ce qui rend le bouton plus grand.  Lorsque la souris s'éloigne du bouton, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> ont la valeur `1`, ce qui permet au bouton de retrouver sa taille initiale.  
  
## Exemple  
 [!code-xml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## Voir aussi  
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.ScaleTransform>   
 [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)   
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)