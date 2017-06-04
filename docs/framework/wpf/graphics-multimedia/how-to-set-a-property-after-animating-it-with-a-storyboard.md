---
title: "Comment&#160;: d&#233;finir une propri&#233;t&#233; apr&#232;s l&#39;avoir anim&#233;e avec un storyboard | Microsoft Docs"
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
  - "animation, modifier des valeurs de propriété après"
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: d&#233;finir une propri&#233;t&#233; apr&#232;s l&#39;avoir anim&#233;e avec un storyboard
Dans certains cas, il peut arriver que vous ne puissiez pas modifier la valeur d'une propriété qui a été animée.  
  
## Exemple  
 Dans l'exemple suivant, une <xref:System.Windows.Media.Animation.Storyboard> est utilisée pour animer la couleur d'un <xref:System.Windows.Media.SolidColorBrush>.  La table de montage séquentiel est déclenchée lorsque vous cliquez sur le bouton.  L'événement <xref:System.Windows.Media.Animation.Timeline.Completed> est géré de telle sorte le programme est informé de la fin de l'<xref:System.Windows.Media.Animation.ColorAnimation>.  
  
 [!code-xml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## Exemple  
 Une fois l'<xref:System.Windows.Media.Animation.ColorAnimation> terminée, le programme essaie de remplacer la couleur du pinceau par du bleu.  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 Le code ci\-dessus semble sans effet : le pinceau reste jaune, qui est la valeur fournie par l'<xref:System.Windows.Media.Animation.ColorAnimation> qui a animé le pinceau.  La valeur de propriété sous\-jacente \(valeur de base\) a en fait été remplacée par le bleu.  La valeur effective, ou actuelle, reste toutefois le jaune car l'<xref:System.Windows.Media.Animation.ColorAnimation> continue de substituer la valeur de base.  Si vous souhaitez que la valeur de base redevienne la valeur effective, vous devez faire en sorte que l'animation cesse d'influencer la propriété.  Il y a trois façons de le faire avec les animations de table de montage séquentiel :  
  
-   Affectez la valeur <xref:System.Windows.Media.Animation.FillBehavior> à la propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de l'animation.  
  
-   Supprimez l'intégralité de la table de montage séquentiel.  
  
-   Supprimez l'animation de la propriété individuelle.  
  
## Affectation de la valeur Stop à la propriété FillBehavior de l'animation  
 En affectant la valeur <xref:System.Windows.Media.Animation.FillBehavior> à <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>, vous demandez à l'animation de cesser d'affecter sa propriété cible lorsqu'elle arrive au terme de sa période active.  
  
 [!code-xml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## Suppression de l'intégralité de la table de montage séquentiel  
 En utilisant un déclencheur <xref:System.Windows.Media.Animation.RemoveStoryboard> ou la méthode <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=fullName>, vous demandez aux animations de la table de montage séquentiel de cesser d'affecter leurs propriétés cibles.  La différence entre cette approche et la définition de la propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> est que vous pouvez supprimer la table de montage séquentiel à tout moment, tandis que la propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> ne prend effet que lorsque l'animation atteint la fin de sa période active.  
  
 [!code-xml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## Suppression d'une animation d'une propriété individuelle  
 Une autre technique pour empêcher une animation d'affecter une propriété consiste à utiliser la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> de l'objet animé.  Spécifiez la propriété animée comme premier paramètre et `null` comme second paramètre.  
  
 [!code-xml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 Cette technique fonctionne également pour les animations sans table de montage séquentiel.  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>   
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=fullName>   
 <xref:System.Windows.Media.Animation.RemoveStoryboard>   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble des techniques d'animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)