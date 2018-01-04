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
ms.workload: dotnet
ms.openlocfilehash: 0eb4542d8baf86f01417eb1925028a00471b40b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="e0853-102">Comment : déclencher une animation en cas de modification d'une valeur de propriété</span><span class="sxs-lookup"><span data-stu-id="e0853-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="e0853-103">Cet exemple montre comment utiliser un <xref:System.Windows.Trigger> pour démarrer un <xref:System.Windows.Media.Animation.Storyboard> quand une valeur de propriété change.</span><span class="sxs-lookup"><span data-stu-id="e0853-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="e0853-104">Vous pouvez utiliser un <xref:System.Windows.Trigger> à l’intérieur d’un <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, ou <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="e0853-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0853-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="e0853-105">Example</span></span>  
 <span data-ttu-id="e0853-106">L’exemple suivant utilise un <xref:System.Windows.Trigger> pour animer la <xref:System.Windows.UIElement.Opacity%2A> d’un <xref:System.Windows.Controls.Button> lors de son <xref:System.Windows.UIElement.IsMouseOver%2A> propriété devient `true`.</span><span class="sxs-lookup"><span data-stu-id="e0853-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="e0853-107">Les animations appliquées par la propriété <xref:System.Windows.Trigger> objets se comportent de façon plus complexe que <xref:System.Windows.EventTrigger> animations ou les animations démarrées à l’aide de <xref:System.Windows.Media.Animation.Storyboard> méthodes.</span><span class="sxs-lookup"><span data-stu-id="e0853-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="e0853-108">Ils « remise » avec les animations définie par d’autres <xref:System.Windows.Trigger> objets, mais composent avec <xref:System.Windows.EventTrigger> et les animations de méthode déclenchée.</span><span class="sxs-lookup"><span data-stu-id="e0853-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0853-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0853-109">See Also</span></span>  
 <xref:System.Windows.Trigger>  
 [<span data-ttu-id="e0853-110">Vue d’ensemble des techniques d’animation de propriétés</span><span class="sxs-lookup"><span data-stu-id="e0853-110">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [<span data-ttu-id="e0853-111">Vue d'ensemble des plans conceptuels</span><span class="sxs-lookup"><span data-stu-id="e0853-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
