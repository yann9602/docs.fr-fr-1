---
title: "Comment&#160;: d&#233;finir une dur&#233;e pour une animation | Microsoft Docs"
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
  - "animation, durée"
  - "durée des animations"
  - "chronologies, description"
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: d&#233;finir une dur&#233;e pour une animation
Un <xref:System.Windows.Media.Animation.Timeline> représente un segment de temps dont la longueur est déterminée par le <xref:System.Windows.Duration> de la chronologie.  Lorsqu'un <xref:System.Windows.Media.Animation.Timeline> atteint la fin de sa durée, il arrête de jouer.  Si le <xref:System.Windows.Media.Animation.Timeline> contient des chronologies enfants, celles\-ci cessent également de jouer.  Dans le cas d'une animation, le <xref:System.Windows.Duration> indique le temps que prend une animation pour passer de sa valeur initiale à sa valeur finale.  
  
 Vous pouvez spécifier un <xref:System.Windows.Duration> avec une durée finie spécifique ou les valeurs spéciales <xref:System.Windows.Duration.Automatic%2A> ou <xref:System.Windows.Duration.Forever%2A>.  La durée d'une animation doit toujours être une valeur de temps, car une animation doit toujours avoir une longueur finie spécifique. À défaut, l'animation ne sait pas comment effectuer la transition entre ses valeurs cibles.  Les chronologies de conteneur \(objets <xref:System.Windows.Media.Animation.TimelineGroup>\), comme <xref:System.Windows.Media.Animation.Storyboard> et <xref:System.Windows.Media.Animation.ParallelTimeline>, ont une durée par défaut de <xref:System.Windows.Duration.Automatic%2A>, ce qui signifie qu'elles se terminent automatiquement lorsque leur dernier enfant arrête de jouer.  
  
 Dans l'exemple suivant, la largeur, la hauteur et la couleur de remplissage d'un <xref:System.Windows.Shapes.Rectangle> sont animées.  Les durées sont définies dans des chronologies d'animation et de conteneur qui entraînent des effets d'animation, notamment le contrôle de la vitesse perçue d'une animation et la substitution de la durée des chronologies enfants par la durée d'une chronologie de conteneur.  
  
## Exemple  
 [!code-xml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## Voir aussi  
 <xref:System.Windows.Duration>   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)