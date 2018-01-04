---
title: "Comment : spécifier l'inversion automatique ou non d'une chronologie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da1330a8513f43e7543f97838ef8e9be788af396
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a><span data-ttu-id="31fe8-102">Comment : spécifier l'inversion automatique ou non d'une chronologie</span><span class="sxs-lookup"><span data-stu-id="31fe8-102">How to: Specify Whether a Timeline Automatically Reverses</span></span>
<span data-ttu-id="31fe8-103">Une chronologie <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriété détermine si elle joue à l’issue d’une itération en avant dans l’ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="31fe8-103">A timeline's <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property determines whether it plays in reverse after it completes a forward iteration.</span></span> <span data-ttu-id="31fe8-104">L’exemple suivant montre plusieurs animations durée identiques et les valeurs cibles, mais avec différentes <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> paramètres.</span><span class="sxs-lookup"><span data-stu-id="31fe8-104">The following example shows several animations with identical duration and target values, but with different <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> settings.</span></span> <span data-ttu-id="31fe8-105">Pour illustrer comment le <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriété se comporte avec différentes <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , certaines animations sont configurés pour répéter.</span><span class="sxs-lookup"><span data-stu-id="31fe8-105">To demonstrate how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property behaves with different <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> settings, some animations are set to repeat.</span></span> <span data-ttu-id="31fe8-106">La dernière animation indique comment la <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriété fonctionne sur des chronologies imbriquées.</span><span class="sxs-lookup"><span data-stu-id="31fe8-106">The last animation shows how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property works on nested timelines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31fe8-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="31fe8-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
