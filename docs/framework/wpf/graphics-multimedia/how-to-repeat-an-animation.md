---
title: "Comment&#160;: r&#233;p&#233;ter une animation | Microsoft Docs"
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
  - "animation, répéter"
  - "RepeatBehavior (propriété de chronologies)"
  - "répéter l'animation"
  - "chronologies (propriété RepeatBehavior)"
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: r&#233;p&#233;ter une animation
Cet exemple montre comment utiliser la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> d'un <xref:System.Windows.Media.Animation.Timeline> pour contrôler le comportement de répétition d'une animation.  
  
## Exemple  
 La propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> d'un <xref:System.Windows.Media.Animation.Timeline> contrôle le nombre de fois qu'une animation répète sa durée simple.  En utilisant <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, vous pouvez spécifier qu'un <xref:System.Windows.Media.Animation.Timeline> soit répété un certain nombre de fois \(nombre d'itérations\) ou pendant une période spécifiée.  Dans les deux cas, l'animation est répétée du début à la fin, autant de fois qu'il le faut pour répondre à la durée ou au nombre demandé.  
  
 Par défaut, le facteur de répétition des chronologies est 1.0, ce qui signifie qu'elles ne sont exécutées qu'une seule fois.  Toutefois, si vous affectez à la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> d'un <xref:System.Windows.Media.Animation.Timeline> la valeur <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, la chronologie se répète indéfiniment.  
  
 L'exemple suivant montre comment utiliser la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pour contrôler le comportement de répétition d'une animation.  L'exemple anime la propriété <xref:System.Windows.FrameworkElement.Width%2A> de cinq rectangles, chacun utilisant un type de comportement de répétition différent.  
  
 [!code-xml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Pour l'exemple complet, consultez [Comportement de minutage d'une animation, exemple](http://go.microsoft.com/fwlink/?LinkID=159970).  
  
## Voir aussi  
 [Accumuler des valeurs d'animation pendant des cycles de répétition](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)   
 [Spécifier l'inversion automatique ou non d'une chronologie](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)   
 [Animation and Timing](http://msdn.microsoft.com/fr-fr/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Comportement de minutage d'une animation, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159970)