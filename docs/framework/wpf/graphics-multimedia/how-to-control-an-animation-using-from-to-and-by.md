---
title: "Comment : contrôler une animation avec From, To et By"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17f87c8bcf09022aa389df779e29f5e5affabc20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Comment : contrôler une animation avec From, To et By
Un « à partir de/à/By » ou « animation de base » crée une transition entre deux valeurs cibles (consultez [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) pour une introduction aux différents types d’animations). Pour définir les valeurs cibles d’une animation de base, utilisez son <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriétés.  Le tableau suivant résume comment la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriétés peuvent être utilisées ensemble ou séparément pour déterminer les cibles d’une animation les valeurs.  
  
|Propriétés spécifiées|Comportement obtenu|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|L’animation passe de la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété la valeur de base de la propriété animée ou à une animation précédente de sortie de valeur, en fonction de la configuration de l’animation précédente.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|L’animation passe de la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> valeur à la propriété spécifiée par le <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|L’animation passe de la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété à la valeur spécifiée par la somme de la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriétés.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|L’animation progresse à partir de la valeur de base de la propriété animée ou d’une animation précédente valeur de sortie à la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|L’animation passe de la valeur de base de la propriété animée ou d’une animation précédente valeur de sortie à la somme de cette valeur et la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété.|  
  
> [!NOTE]
>  Ne définissez pas les deux le <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété et le <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété sur la même animation.  
  
 Pour utiliser d’autres méthodes d’interpolation ou effectuer une animation entre plus de deux valeurs cibles, utilisez une animation d’image clé. Consultez [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md) pour plus d’informations.  
  
 Pour plus d’informations sur l’application de plusieurs animations à une propriété unique, consultez [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 L’exemple ci-dessous montre les différents effets du paramètre <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, et <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriétés sur des animations.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Exemple de valeurs cibles d’animation From, To et By](http://go.microsoft.com/fwlink/?LinkID=159988)
