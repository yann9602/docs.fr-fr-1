---
title: "Comment&#160;: animer une propri&#233;t&#233; sans utiliser de storyboard | Microsoft Docs"
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
  - "animation, autre que l'animation de storyboard (locale)"
  - "animation locale"
  - "animation autre que l'animation de storyboard"
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: animer une propri&#233;t&#233; sans utiliser de storyboard
Cet exemple montre une façon d'appliquer une animation à une propriété sans utiliser de <xref:System.Windows.Media.Animation.Storyboard>.  
  
> [!NOTE]
>  Ces fonctionnalités ne sont pas disponibles en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Pour plus d'informations sur l'animation d'une propriété en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consultez [Animer une propriété à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Pour appliquer une animation locale à une propriété, utilisez la méthode <xref:System.Windows.UIElement.BeginAnimation%2A>.  Cette méthode accepte deux paramètres : un <xref:System.Windows.DependencyProperty> qui spécifie la propriété à animer, et l'animation à appliquer à cette propriété.  
  
## Exemple  
 L'exemple suivant montre comment animer la largeur et la couleur d'arrière\-plan d'un <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Il existe diverses classes d'animation dans l'espace de noms <xref:System.Windows.Media.Animation> pour animer différents types de propriétés.  Pour plus d'informations sur l'animation des propriétés, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  Pour plus d'informations sur les [propriétés de dépendance](GTMT) \(le type de propriétés présentées dans ces exemples\) et leurs fonctionnalités, consultez [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 Il existe d'autres façons d'animer sans utiliser d'objets <xref:System.Windows.Media.Animation.Storyboard> ; pour plus d'informations, consultez [Vue d'ensemble des techniques d'animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.AnimationTimeline>   
 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>   
 <xref:System.Windows.Media.Animation>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 [Vue d'ensemble des techniques d'animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)