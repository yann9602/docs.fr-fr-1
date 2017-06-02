---
title: "Comment&#160;: animer la taille d&#39;un FrameworkElement | Microsoft Docs"
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
  - "animation, FrameworkElement (taille)"
  - "FrameworkElement, animer la taille de"
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: animer la taille d&#39;un FrameworkElement
Pour animer la taille d'un <xref:System.Windows.FrameworkElement>, vous pouvez animer ses propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> ou utiliser un <xref:System.Windows.Media.ScaleTransform> animé.  
  
 L'exemple suivant anime la taille de deux boutons à l'aide de ces deux approches.  Un bouton est redimensionné en animant sa propriété <xref:System.Windows.FrameworkElement.Width%2A> et l'autre est redimensionné en animant un <xref:System.Windows.Media.ScaleTransform> appliqué à sa propriété <xref:System.Windows.UIElement.RenderTransform%2A>.  Chaque bouton contient du texte.  Au début, le texte apparaît de la même manière dans les deux boutons, mais lorsque les boutons sont redimensionnés, le texte du second bouton est déformé.  
  
## Exemple  
 [!code-xml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 Lorsque vous transformez un élément, tout l'élément et son contenu sont transformés.  Lorsque vous modifiez directement la taille d'un élément, comme dans le cas du premier bouton, le contenu de l'élément n'est pas redimensionné sauf si sa taille et sa position dépendent de la taille de l'élément parent.  
  
 L'animation de la taille d'un élément en appliquant une transformation animée à sa propriété <xref:System.Windows.UIElement.RenderTransform%2A> fournit de meilleures performances que si vous animez directement <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>, parce que la propriété <xref:System.Windows.UIElement.RenderTransform%2A> ne déclenche pas de passe de disposition.  
  
 Pour plus d'informations sur l'animation de propriétés, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  Pour plus d'informations sur les transformations, consultez [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).