---
title: "Comment : déclencher une animation en cas de modification d'une valeur de propriété"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d722be0f0367f7e6e98ef1c8451ce58ee28fedd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>Comment : déclencher une animation en cas de modification d'une valeur de propriété
Cet exemple montre comment utiliser un <xref:System.Windows.Trigger> pour démarrer un <xref:System.Windows.Media.Animation.Storyboard> quand une valeur de propriété change. Vous pouvez utiliser un <xref:System.Windows.Trigger> à l’intérieur d’un <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, ou <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un <xref:System.Windows.Trigger> pour animer la <xref:System.Windows.UIElement.Opacity%2A> d’un <xref:System.Windows.Controls.Button> lors de son <xref:System.Windows.UIElement.IsMouseOver%2A> propriété devient `true`.  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 Les animations appliquées par la propriété <xref:System.Windows.Trigger> objets se comportent de façon plus complexe que <xref:System.Windows.EventTrigger> animations ou les animations démarrées à l’aide de <xref:System.Windows.Media.Animation.Storyboard> méthodes.  Ils « remise » avec les animations définie par d’autres <xref:System.Windows.Trigger> objets, mais composent avec <xref:System.Windows.EventTrigger> et les animations de méthode déclenchée.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Trigger>  
 [Vue d’ensemble des techniques d’animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Vue d'ensemble des plans conceptuels](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
