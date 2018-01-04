---
title: "Comment : simplifier des animations à l'aide de chronologies enfants"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d3b8f1ca1dbf7ba5452acffc62fdf0b655c9c12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a>Comment : simplifier des animations à l'aide de chronologies enfants
Cet exemple montre comment simplifier des animations à l’aide des enfants <xref:System.Windows.Media.Animation.ParallelTimeline> objets. A <xref:System.Windows.Media.Animation.Storyboard> est un type de <xref:System.Windows.Media.Animation.Timeline> qui fournit des informations de ciblage pour les chronologies qu’il contient. Utilisez un <xref:System.Windows.Media.Animation.Storyboard> pour fournir des informations, y compris les informations d’objet et la propriété de ciblage de chronologie.  
  
 Pour commencer une animation, utilisez une ou plusieurs <xref:System.Windows.Media.Animation.ParallelTimeline> objets en tant qu’éléments enfants imbriqués d’un <xref:System.Windows.Media.Animation.Storyboard>. Ces <xref:System.Windows.Media.Animation.ParallelTimeline> objets peuvent contenir d’autres animations et par conséquent, mieux encapsuler les séquences temporelles dans des animations complexes. Par exemple, si vous animez un <xref:System.Windows.Controls.TextBlock> et plusieurs formes dans le même <xref:System.Windows.Media.Animation.Storyboard>, vous pouvez séparer les animations de la <xref:System.Windows.Controls.TextBlock> et les formes, en les mettant chacune dans un distinct <xref:System.Windows.Media.Animation.ParallelTimeline>. Étant donné que chaque <xref:System.Windows.Media.Animation.ParallelTimeline> possède son propre <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> et tous les éléments enfants de la <xref:System.Windows.Media.Animation.ParallelTimeline> commencer par rapport à cette <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, minutage est mieux encapsulé.  
  
 L’exemple suivant anime deux parties de texte (<xref:System.Windows.Controls.TextBlock> objets) à partir d’au sein du même <xref:System.Windows.Media.Animation.Storyboard>. A <xref:System.Windows.Media.Animation.ParallelTimeline> encapsule les animations de l’un de le <xref:System.Windows.Controls.TextBlock> objets.  
  
 **Remarque de performances :** bien que vous pouvez imbriquer des <xref:System.Windows.Media.Animation.Storyboard> chronologies à l’intérieur de l’autre, <xref:System.Windows.Media.Animation.ParallelTimeline>s sont plus adaptés à l’imbrication, car elles nécessitent moins de surcharge. (Le <xref:System.Windows.Media.Animation.Storyboard> classe hérite de la <xref:System.Windows.Media.Animation.ParallelTimeline> classe.)  
  
## <a name="example"></a>Exemple  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Spécifier HandoffBehavior entre des animations de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)
