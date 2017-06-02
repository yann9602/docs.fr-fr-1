---
title: "Comment&#160;: sp&#233;cifier HandoffBehavior entre des animations de storyboard | Microsoft Docs"
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
  - "animation, comportement de transfert de travail entre"
  - "Animations, comportement de transfert de travail entre animations"
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: sp&#233;cifier HandoffBehavior entre des animations de storyboard
Cet exemple montre comment spécifier le comportement du type de transition entre des animations storyboard.  La propriété <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> de <xref:System.Windows.Media.Animation.BeginStoryboard> explique comment les nouvelles animations interagissent avec les animations existantes qui s'appliquent déjà à une propriété.  
  
## Exemple  
 L'exemple suivant crée deux boutons qui s'agrandissent lorsque le curseur de la souris est placé dessus et qui diminuent lorsque le curseur s'éloigne.  Si vous pointez la souris sur un bouton et que vous déplacez rapidement le curseur, la deuxième animation sera appliquée avant que la première ne soit terminée.  C'est lorsque deux animations se chevauchent ainsi que vous pouvez voir la différence entre les valeurs <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> de <xref:System.Windows.Media.Animation.HandoffBehavior> et <xref:System.Windows.Media.Animation.HandoffBehavior>.  Une valeur de <xref:System.Windows.Media.Animation.HandoffBehavior> combine les animations qui se chevauchent, ce qui provoque une transition plus fluide entre les animations alors qu'une valeur de <xref:System.Windows.Media.Animation.HandoffBehavior> provoque le remplacement immédiat de la première animation chevauchée par la nouvelle animation.  
  
 [!code-xml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.BeginStoryboard>   
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Animation and Timing](http://msdn.microsoft.com/fr-fr/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)