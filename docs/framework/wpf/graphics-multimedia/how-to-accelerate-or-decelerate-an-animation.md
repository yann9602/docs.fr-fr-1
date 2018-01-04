---
title: "Comment : accélérer ou décélérer une animation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c06518e3eada30bd4e22549a9ee3c8f16070f5ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="7fde2-102">Comment : accélérer ou décélérer une animation</span><span class="sxs-lookup"><span data-stu-id="7fde2-102">How to: Accelerate or Decelerate an Animation</span></span>
<span data-ttu-id="7fde2-103">Cet exemple montre comment réaliser une animation d’accélérer et ralentir au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="7fde2-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="7fde2-104">Dans l’exemple suivant, plusieurs rectangles sont animés par des animations avec différents <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> et <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> paramètres.</span><span class="sxs-lookup"><span data-stu-id="7fde2-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fde2-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="7fde2-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="7fde2-106">Code a été omis de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="7fde2-106">Code has been omitted from this example.</span></span> <span data-ttu-id="7fde2-107">Pour obtenir le code complet, consultez la [comportement de minutage d’Animation exemple](http://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="7fde2-107">For the complete code, see the [Animation Timing Behavior Sample](http://go.microsoft.com/fwlink/?LinkID=159970).</span></span>
