---
title: "Comment&#160;: simplifier des animations &#224; l&#39;aide de chronologies enfants | Microsoft Docs"
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
  - "animation, simplifier par des chronologies enfants"
  - "chronologies enfants"
  - "simplifier des animations à l'aide de chronologies enfants"
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: simplifier des animations &#224; l&#39;aide de chronologies enfants
Cet exemple montre comment simplifier des animations à l'aide d'objets <xref:System.Windows.Media.Animation.ParallelTimeline> enfants.  Un <xref:System.Windows.Media.Animation.Storyboard> est un type de <xref:System.Windows.Media.Animation.Timeline> qui fournit des informations de ciblage pour les chronologies qu'il contient.  Utilisez un <xref:System.Windows.Media.Animation.Storyboard> pour fournir des informations de ciblage sur la chronologie, y compris des informations sur l'objet et la propriété.  
  
 Pour débuter une animation, utilisez un ou plusieurs objets <xref:System.Windows.Media.Animation.ParallelTimeline> comme éléments enfants imbriqués d'un <xref:System.Windows.Media.Animation.Storyboard>.  Ces objets <xref:System.Windows.Media.Animation.ParallelTimeline> peuvent contenir d'autres animations et peuvent, par conséquent, mieux encapsuler les séquences temporelles dans des animations complexes.  Par exemple, si vous animez un <xref:System.Windows.Controls.TextBlock> et plusieurs formes dans le même <xref:System.Windows.Media.Animation.Storyboard>, vous pouvez séparer les animations pour le <xref:System.Windows.Controls.TextBlock> et les formes, en les mettant chacune dans un <xref:System.Windows.Media.Animation.ParallelTimeline> séparé.  Étant donné que chaque <xref:System.Windows.Media.Animation.ParallelTimeline> possède son propre <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> et que tous les éléments enfants du <xref:System.Windows.Media.Animation.ParallelTimeline> commencent par rapport à ce <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, la séquence temporelle est mieux encapsulée.  
  
 L'exemple suivant anime deux parties de texte \(objets <xref:System.Windows.Controls.TextBlock>\) à partir du même <xref:System.Windows.Media.Animation.Storyboard>.  Un <xref:System.Windows.Media.Animation.ParallelTimeline> encapsule les animations de l'un des objets <xref:System.Windows.Controls.TextBlock>.  
  
 **Remarque sur les performances :** bien que vous puissiez imbriquer des chronologies <xref:System.Windows.Media.Animation.Storyboard> les unes dans les autres, les <xref:System.Windows.Media.Animation.ParallelTimeline>s sont plus appropriés pour l'imbrication car ils requièrent moins de charge mémoire.  \(La classe <xref:System.Windows.Media.Animation.Storyboard> hérite de la classe <xref:System.Windows.Media.Animation.ParallelTimeline>.\)  
  
## Exemple  
 [!code-xml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## Voir aussi  
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Spécifier HandoffBehavior entre des animations de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)