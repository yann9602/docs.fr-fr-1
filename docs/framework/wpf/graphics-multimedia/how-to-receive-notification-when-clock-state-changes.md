---
title: "Comment : recevoir une Notification quand une horloge au format &#39; modification de l’état s"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 396e2c51894ad5ed11f8953bceb1bd36899cfc62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a><span data-ttu-id="0f1f8-102">Comment : recevoir une Notification quand une horloge au format &#39; modification de l’état s</span><span class="sxs-lookup"><span data-stu-id="0f1f8-102">How to: Receive Notification When a Clock&#39;s State Changes</span></span>
<span data-ttu-id="0f1f8-103">D’une horloge <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> événement se produit lors de son <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> devient non valide, par exemple lorsque l’horloge démarre ou s’arrête.</span><span class="sxs-lookup"><span data-stu-id="0f1f8-103">A clock's <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> event occurs when its <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> becomes invalid, such as when the clock starts or stops.</span></span> <span data-ttu-id="0f1f8-104">Vous pouvez inscrire directement à l’aide de cet événement un <xref:System.Windows.Media.Animation.Clock>, ou vous pouvez effectuer à l’aide un <xref:System.Windows.Media.Animation.Timeline>.</span><span class="sxs-lookup"><span data-stu-id="0f1f8-104">You can register for this event with directly using a <xref:System.Windows.Media.Animation.Clock>, or you can register using a <xref:System.Windows.Media.Animation.Timeline>.</span></span>  
  
 <span data-ttu-id="0f1f8-105">Dans l’exemple suivant, un <xref:System.Windows.Media.Animation.Storyboard> et deux <xref:System.Windows.Media.Animation.DoubleAnimation> objets sont utilisés pour animer la largeur de deux rectangles.</span><span class="sxs-lookup"><span data-stu-id="0f1f8-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> and two <xref:System.Windows.Media.Animation.DoubleAnimation> objects are used to animate the width of two rectangles.</span></span> <span data-ttu-id="0f1f8-106">Le <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> événement est utilisé pour écouter les changements d’état de l’horloge.</span><span class="sxs-lookup"><span data-stu-id="0f1f8-106">The <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event is used to listen for clock state changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f1f8-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="0f1f8-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 <span data-ttu-id="0f1f8-108">L’illustration suivante montre les différents États des animations en tant que la chronologie parent (*Storyboard*) progresse.</span><span class="sxs-lookup"><span data-stu-id="0f1f8-108">The following illustration shows the different states the animations enter as the parent timeline (*Storyboard*) progresses.</span></span>  
  
 <span data-ttu-id="0f1f8-109">![États d’horloge pour une table de montage séquentiel avec deux animations](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span><span class="sxs-lookup"><span data-stu-id="0f1f8-109">![Clock states for a Storyboard with two animations](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span></span>  
  
 <span data-ttu-id="0f1f8-110">Le tableau suivant répertorie les moments qui *Animation1*de <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> se déclenche des événements :</span><span class="sxs-lookup"><span data-stu-id="0f1f8-110">The following table shows the times at which *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
|<span data-ttu-id="0f1f8-111">Durée (en secondes)</span><span class="sxs-lookup"><span data-stu-id="0f1f8-111">Time (Seconds)</span></span>|<span data-ttu-id="0f1f8-112">1</span><span class="sxs-lookup"><span data-stu-id="0f1f8-112">1</span></span>|<span data-ttu-id="0f1f8-113">10</span><span class="sxs-lookup"><span data-stu-id="0f1f8-113">10</span></span>|<span data-ttu-id="0f1f8-114">19</span><span class="sxs-lookup"><span data-stu-id="0f1f8-114">19</span></span>|<span data-ttu-id="0f1f8-115">21</span><span class="sxs-lookup"><span data-stu-id="0f1f8-115">21</span></span>|<span data-ttu-id="0f1f8-116">30</span><span class="sxs-lookup"><span data-stu-id="0f1f8-116">30</span></span>|<span data-ttu-id="0f1f8-117">39</span><span class="sxs-lookup"><span data-stu-id="0f1f8-117">39</span></span>|  
|<span data-ttu-id="0f1f8-118">État</span><span class="sxs-lookup"><span data-stu-id="0f1f8-118">State</span></span>|<span data-ttu-id="0f1f8-119">Actif</span><span class="sxs-lookup"><span data-stu-id="0f1f8-119">Active</span></span>|<span data-ttu-id="0f1f8-120">Actif</span><span class="sxs-lookup"><span data-stu-id="0f1f8-120">Active</span></span>|<span data-ttu-id="0f1f8-121">Arrêté</span><span class="sxs-lookup"><span data-stu-id="0f1f8-121">Stopped</span></span>|<span data-ttu-id="0f1f8-122">Actif</span><span class="sxs-lookup"><span data-stu-id="0f1f8-122">Active</span></span>|<span data-ttu-id="0f1f8-123">Actif</span><span class="sxs-lookup"><span data-stu-id="0f1f8-123">Active</span></span>|<span data-ttu-id="0f1f8-124">Arrêté</span><span class="sxs-lookup"><span data-stu-id="0f1f8-124">Stopped</span></span>|  
  
 <span data-ttu-id="0f1f8-125">Le tableau suivant répertorie les moments qui *Animation2*de <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> se déclenche des événements :</span><span class="sxs-lookup"><span data-stu-id="0f1f8-125">The following table shows the times at which *Animation2*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="0f1f8-126">Durée (en secondes)</span><span class="sxs-lookup"><span data-stu-id="0f1f8-126">Time (Seconds)</span></span>|<span data-ttu-id="0f1f8-127">1</span><span class="sxs-lookup"><span data-stu-id="0f1f8-127">1</span></span>|<span data-ttu-id="0f1f8-128">9</span><span class="sxs-lookup"><span data-stu-id="0f1f8-128">9</span></span>|<span data-ttu-id="0f1f8-129">11</span><span class="sxs-lookup"><span data-stu-id="0f1f8-129">11</span></span>|<span data-ttu-id="0f1f8-130">19</span><span class="sxs-lookup"><span data-stu-id="0f1f8-130">19</span></span>|<span data-ttu-id="0f1f8-131">21</span><span class="sxs-lookup"><span data-stu-id="0f1f8-131">21</span></span>|<span data-ttu-id="0f1f8-132">29</span><span class="sxs-lookup"><span data-stu-id="0f1f8-132">29</span></span>|<span data-ttu-id="0f1f8-133">31</span><span class="sxs-lookup"><span data-stu-id="0f1f8-133">31</span></span>|<span data-ttu-id="0f1f8-134">39</span><span class="sxs-lookup"><span data-stu-id="0f1f8-134">39</span></span>|  
|<span data-ttu-id="0f1f8-135">État</span><span class="sxs-lookup"><span data-stu-id="0f1f8-135">State</span></span>|<span data-ttu-id="0f1f8-136">Actif</span><span class="sxs-lookup"><span data-stu-id="0f1f8-136">Active</span></span>|<span data-ttu-id="0f1f8-137">Remplissage</span><span class="sxs-lookup"><span data-stu-id="0f1f8-137">Filling</span></span>|<span data-ttu-id="0f1f8-138">Actif</span><span class="sxs-lookup"><span data-stu-id="0f1f8-138">Active</span></span>|<span data-ttu-id="0f1f8-139">Arrêté</span><span class="sxs-lookup"><span data-stu-id="0f1f8-139">Stopped</span></span>|<span data-ttu-id="0f1f8-140">Actif</span><span class="sxs-lookup"><span data-stu-id="0f1f8-140">Active</span></span>|<span data-ttu-id="0f1f8-141">Remplissage</span><span class="sxs-lookup"><span data-stu-id="0f1f8-141">Filling</span></span>|<span data-ttu-id="0f1f8-142">Actif</span><span class="sxs-lookup"><span data-stu-id="0f1f8-142">Active</span></span>|<span data-ttu-id="0f1f8-143">Arrêté</span><span class="sxs-lookup"><span data-stu-id="0f1f8-143">Stopped</span></span>|  
  
 <span data-ttu-id="0f1f8-144">Notez que *Animation1*de <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> événement est déclenché au bout de 10 secondes, même si son état reste <xref:System.Windows.Media.Animation.ClockState.Active>.</span><span class="sxs-lookup"><span data-stu-id="0f1f8-144">Notice that *Animation1*'s  <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires at 10 seconds, even though its state remains <xref:System.Windows.Media.Animation.ClockState.Active>.</span></span> <span data-ttu-id="0f1f8-145">C’est parce que son état a changé dans 10 secondes, mais il a été remplacée par <xref:System.Windows.Media.Animation.ClockState.Active> à <xref:System.Windows.Media.Animation.ClockState.Filling> , puis revient à <xref:System.Windows.Media.Animation.ClockState.Active> dans le même battement.</span><span class="sxs-lookup"><span data-stu-id="0f1f8-145">That's because its state changed at 10 seconds, but it changed from <xref:System.Windows.Media.Animation.ClockState.Active> to <xref:System.Windows.Media.Animation.ClockState.Filling> and then back to <xref:System.Windows.Media.Animation.ClockState.Active> in the same tick.</span></span>
