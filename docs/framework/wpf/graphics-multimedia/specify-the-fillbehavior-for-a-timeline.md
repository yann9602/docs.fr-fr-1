---
title: "Comment&#160;: sp&#233;cifier le FillBehavior pour une chronologie ayant atteint la fin de sa p&#233;riode active | Microsoft Docs"
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
  - "FillBehavior (propriété pour les chronologies inactives)"
  - "chronologies, FillBehavior (propriété)"
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: sp&#233;cifier le FillBehavior pour une chronologie ayant atteint la fin de sa p&#233;riode active
Cet exemple montre comment spécifier le <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> pour la <xref:System.Windows.Media.Animation.Timeline> inactive d'une propriété animée.  
  
## Exemple  
 La propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> d'un <xref:System.Windows.Media.Animation.Timeline> détermine ce qui arrive à la valeur d'une propriété animée lorsqu'elle n'est pas animée, c'est\-à\-dire lorsque le <xref:System.Windows.Media.Animation.Timeline> est inactif mais que son <xref:System.Windows.Media.Animation.Timeline> parent est en période active ou bloquée.  Par exemple, est\-ce qu'une propriété animée conserve sa valeur finale après la fin de l'animation ou est\-ce que la valeur qu'elle avait avant le démarrage de l'animation est rétablie ?  
  
 L'exemple suivant utilise un <xref:System.Windows.Media.Animation.DoubleAnimation> pour animer la <xref:System.Windows.FrameworkElement.Width%2A> de deux rectangles.  Chaque rectangle utilise un objet <xref:System.Windows.Media.Animation.Timeline> différent.  
  
 Un <xref:System.Windows.Media.Animation.Timeline> possède un <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> qui a la valeur <xref:System.Windows.Media.Animation.FillBehavior> ; de ce fait, la valeur non animée de la largeur du rectangle est rétablie lorsque le <xref:System.Windows.Media.Animation.Timeline> est terminée.  L'autre <xref:System.Windows.Media.Animation.Timeline> possède un <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> dont la valeur est <xref:System.Windows.Media.Animation.FillBehavior>, ce qui permet à la largeur de conserver sa valeur finale lorsque le <xref:System.Windows.Media.Animation.Timeline> est terminé.  
  
 [!code-xml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Pour obtenir l'exemple complet, consultez [Galerie d'exemples d'animation](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.DoubleAnimation>   
 <xref:System.Windows.FrameworkElement.Width%2A>   
 <xref:System.Windows.Media.Animation.Timeline>   
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>   
 <xref:System.Windows.Media.Animation.FillBehavior>   
 <xref:System.Windows.Media.Animation.FillBehavior>   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Animation and Timing](http://msdn.microsoft.com/fr-fr/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)