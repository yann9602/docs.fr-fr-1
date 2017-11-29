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
ms.openlocfilehash: f59fddb1add29d52ccba6fc8b8ce84938b53a1c2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a><span data-ttu-id="2cad2-102">Comment : recevoir une Notification quand une horloge au format &#39; modification de l’état s</span><span class="sxs-lookup"><span data-stu-id="2cad2-102">How to: Receive Notification When a Clock&#39;s State Changes</span></span>
<span data-ttu-id="2cad2-103">D’une horloge <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> événement se produit lors de son <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> devient non valide, par exemple lorsque l’horloge démarre ou s’arrête.</span><span class="sxs-lookup"><span data-stu-id="2cad2-103">A clock's <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> event occurs when its <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> becomes invalid, such as when the clock starts or stops.</span></span> <span data-ttu-id="2cad2-104">Vous pouvez inscrire directement à l’aide de cet événement un <xref:System.Windows.Media.Animation.Clock>, ou vous pouvez effectuer à l’aide un <xref:System.Windows.Media.Animation.Timeline>.</span><span class="sxs-lookup"><span data-stu-id="2cad2-104">You can register for this event with directly using a <xref:System.Windows.Media.Animation.Clock>, or you can register using a <xref:System.Windows.Media.Animation.Timeline>.</span></span>  
  
 <span data-ttu-id="2cad2-105">Dans l’exemple suivant, un <xref:System.Windows.Media.Animation.Storyboard> et deux <xref:System.Windows.Media.Animation.DoubleAnimation> objets sont utilisés pour animer la largeur de deux rectangles.</span><span class="sxs-lookup"><span data-stu-id="2cad2-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> and two <xref:System.Windows.Media.Animation.DoubleAnimation> objects are used to animate the width of two rectangles.</span></span> <span data-ttu-id="2cad2-106">Le <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> événement est utilisé pour écouter les changements d’état de l’horloge.</span><span class="sxs-lookup"><span data-stu-id="2cad2-106">The <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event is used to listen for clock state changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cad2-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="2cad2-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 <span data-ttu-id="2cad2-108">L’illustration suivante montre les différents États des animations en tant que la chronologie parent (*Storyboard*) progresse.</span><span class="sxs-lookup"><span data-stu-id="2cad2-108">The following illustration shows the different states the animations enter as the parent timeline (*Storyboard*) progresses.</span></span>  
  
 <span data-ttu-id="2cad2-109">![États d’horloge pour une table de montage séquentiel avec deux animations](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span><span class="sxs-lookup"><span data-stu-id="2cad2-109">![Clock states for a Storyboard with two animations](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span></span>  
  
 <span data-ttu-id="2cad2-110">Le tableau suivant répertorie les moments qui *Animation1*de <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> se déclenche des événements :</span><span class="sxs-lookup"><span data-stu-id="2cad2-110">The following table shows the times at which *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
|<span data-ttu-id="2cad2-111">Durée (en secondes)</span><span class="sxs-lookup"><span data-stu-id="2cad2-111">Time (Seconds)</span></span>|<span data-ttu-id="2cad2-112">1</span><span class="sxs-lookup"><span data-stu-id="2cad2-112">1</span></span>|<span data-ttu-id="2cad2-113">10</span><span class="sxs-lookup"><span data-stu-id="2cad2-113">10</span></span>|<span data-ttu-id="2cad2-114">19</span><span class="sxs-lookup"><span data-stu-id="2cad2-114">19</span></span>|<span data-ttu-id="2cad2-115">21</span><span class="sxs-lookup"><span data-stu-id="2cad2-115">21</span></span>|<span data-ttu-id="2cad2-116">30</span><span class="sxs-lookup"><span data-stu-id="2cad2-116">30</span></span>|<span data-ttu-id="2cad2-117">39</span><span class="sxs-lookup"><span data-stu-id="2cad2-117">39</span></span>|  
|<span data-ttu-id="2cad2-118">État</span><span class="sxs-lookup"><span data-stu-id="2cad2-118">State</span></span>|<span data-ttu-id="2cad2-119">Actif</span><span class="sxs-lookup"><span data-stu-id="2cad2-119">Active</span></span>|<span data-ttu-id="2cad2-120">Actif</span><span class="sxs-lookup"><span data-stu-id="2cad2-120">Active</span></span>|<span data-ttu-id="2cad2-121">Arrêté</span><span class="sxs-lookup"><span data-stu-id="2cad2-121">Stopped</span></span>|<span data-ttu-id="2cad2-122">Actif</span><span class="sxs-lookup"><span data-stu-id="2cad2-122">Active</span></span>|<span data-ttu-id="2cad2-123">Actif</span><span class="sxs-lookup"><span data-stu-id="2cad2-123">Active</span></span>|<span data-ttu-id="2cad2-124">Arrêté</span><span class="sxs-lookup"><span data-stu-id="2cad2-124">Stopped</span></span>|  
  
 <span data-ttu-id="2cad2-125">Le tableau suivant répertorie les moments qui *Animation2*de <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> se déclenche des événements :</span><span class="sxs-lookup"><span data-stu-id="2cad2-125">The following table shows the times at which *Animation2*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="2cad2-126">Durée (en secondes)</span><span class="sxs-lookup"><span data-stu-id="2cad2-126">Time (Seconds)</span></span>|<span data-ttu-id="2cad2-127">1</span><span class="sxs-lookup"><span data-stu-id="2cad2-127">1</span></span>|<span data-ttu-id="2cad2-128">9</span><span class="sxs-lookup"><span data-stu-id="2cad2-128">9</span></span>|<span data-ttu-id="2cad2-129">11</span><span class="sxs-lookup"><span data-stu-id="2cad2-129">11</span></span>|<span data-ttu-id="2cad2-130">19</span><span class="sxs-lookup"><span data-stu-id="2cad2-130">19</span></span>|<span data-ttu-id="2cad2-131">21</span><span class="sxs-lookup"><span data-stu-id="2cad2-131">21</span></span>|<span data-ttu-id="2cad2-132">29</span><span class="sxs-lookup"><span data-stu-id="2cad2-132">29</span></span>|<span data-ttu-id="2cad2-133">31</span><span class="sxs-lookup"><span data-stu-id="2cad2-133">31</span></span>|<span data-ttu-id="2cad2-134">39</span><span class="sxs-lookup"><span data-stu-id="2cad2-134">39</span></span>|  
|<span data-ttu-id="2cad2-135">État</span><span class="sxs-lookup"><span data-stu-id="2cad2-135">State</span></span>|<span data-ttu-id="2cad2-136">Actif</span><span class="sxs-lookup"><span data-stu-id="2cad2-136">Active</span></span>|<span data-ttu-id="2cad2-137">Remplissage</span><span class="sxs-lookup"><span data-stu-id="2cad2-137">Filling</span></span>|<span data-ttu-id="2cad2-138">Actif</span><span class="sxs-lookup"><span data-stu-id="2cad2-138">Active</span></span>|<span data-ttu-id="2cad2-139">Arrêté</span><span class="sxs-lookup"><span data-stu-id="2cad2-139">Stopped</span></span>|<span data-ttu-id="2cad2-140">Actif</span><span class="sxs-lookup"><span data-stu-id="2cad2-140">Active</span></span>|<span data-ttu-id="2cad2-141">Remplissage</span><span class="sxs-lookup"><span data-stu-id="2cad2-141">Filling</span></span>|<span data-ttu-id="2cad2-142">Actif</span><span class="sxs-lookup"><span data-stu-id="2cad2-142">Active</span></span>|<span data-ttu-id="2cad2-143">Arrêté</span><span class="sxs-lookup"><span data-stu-id="2cad2-143">Stopped</span></span>|  
  
 <span data-ttu-id="2cad2-144">Notez que *Animation1*de <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> événement est déclenché au bout de 10 secondes, même si son état reste <xref:System.Windows.Media.Animation.ClockState.Active>.</span><span class="sxs-lookup"><span data-stu-id="2cad2-144">Notice that *Animation1*'s  <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires at 10 seconds, even though its state remains <xref:System.Windows.Media.Animation.ClockState.Active>.</span></span> <span data-ttu-id="2cad2-145">C’est parce que son état a changé dans 10 secondes, mais il a été remplacée par <xref:System.Windows.Media.Animation.ClockState.Active> à <xref:System.Windows.Media.Animation.ClockState.Filling> , puis revient à <xref:System.Windows.Media.Animation.ClockState.Active> dans le même battement.</span><span class="sxs-lookup"><span data-stu-id="2cad2-145">That's because its state changed at 10 seconds, but it changed from <xref:System.Windows.Media.Animation.ClockState.Active> to <xref:System.Windows.Media.Animation.ClockState.Filling> and then back to <xref:System.Windows.Media.Animation.ClockState.Active> in the same tick.</span></span>
