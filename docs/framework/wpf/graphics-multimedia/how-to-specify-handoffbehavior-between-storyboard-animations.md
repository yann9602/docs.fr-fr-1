---
title: "Comment : spécifier HandoffBehavior entre des animations de storyboard"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d11c559679b67c22eeed87893bf2e362084034c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>Comment : spécifier HandoffBehavior entre des animations de storyboard
Cet exemple montre comment spécifier le comportement de transfert entre des animations storyboard. Le <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> propriété du <xref:System.Windows.Media.Animation.BeginStoryboard> spécifie comment les nouvelles animations interagissent avec les animations existantes qui sont déjà appliquées à une propriété.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée deux boutons qui agrandissent lorsque le curseur de la souris se déplace au-dessus d’eux et diminuent lorsque le curseur se déplace. Si vous placez la souris sur un bouton, puis supprimez rapidement le curseur, la deuxième animation est appliquée avant que la première est terminée. C’est lorsque deux animations se chevauchent ainsi que vous pouvez voir la différence entre la <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> les valeurs de <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> et <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>. La valeur <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combine les animations qui se chevauche, ce qui provoque une transition plus lisse entre les animations alors que la valeur <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> provoque la nouvelle animation remplacement immédiat de l’animation qui se chevauchent plus haut.  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animation et minutage](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
