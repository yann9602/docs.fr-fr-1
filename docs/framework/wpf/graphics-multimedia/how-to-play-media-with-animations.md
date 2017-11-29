---
title: "Comment : lire le média avec des animations"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb5fd3575a0caa692e4a4013452e3069210c9a4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-media-with-animations"></a><span data-ttu-id="29a64-102">Comment : lire le média avec des animations</span><span class="sxs-lookup"><span data-stu-id="29a64-102">How to: Play Media with Animations</span></span>
<span data-ttu-id="29a64-103">Cet exemple montre comment lire des médias et les animations en même temps à l’aide de la <xref:System.Windows.Media.MediaTimeline> et <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes dans le même <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="29a64-103">This example shows how to play media and animations at the same time by using the <xref:System.Windows.Media.MediaTimeline> and <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes in the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29a64-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="29a64-104">Example</span></span>  
 <span data-ttu-id="29a64-105">Vous pouvez utiliser une ou plusieurs <xref:System.Windows.Media.MediaTimeline> des objets dans une <xref:System.Windows.Media.Animation.Storyboard> ainsi que d’autres <xref:System.Windows.Media.Animation.Timeline> objets, tels que les animations.</span><span class="sxs-lookup"><span data-stu-id="29a64-105">You can use one or more <xref:System.Windows.Media.MediaTimeline> objects in a <xref:System.Windows.Media.Animation.Storyboard> together with other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span>  
  
 <span data-ttu-id="29a64-106">L’exemple suivant définit la <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> propriété de la <xref:System.Windows.Media.Animation.Storyboard> sur la valeur `Slip`, qui spécifie que l’animation ne progresse pas jusqu'à ce que la progression du média (vidéo dans cet exemple).</span><span class="sxs-lookup"><span data-stu-id="29a64-106">The following example sets the <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> property of the <xref:System.Windows.Media.Animation.Storyboard> to a value of `Slip`, which specifies that the animation does not progress until the media (video in this example) progresses.</span></span> <span data-ttu-id="29a64-107">Cette fonctionnalité peut être nécessaire si la lecture du média est retardée en raison du temps de chargement.</span><span class="sxs-lookup"><span data-stu-id="29a64-107">This functionality might be needed if media playback is delayed because of loading time.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="29a64-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29a64-108">See Also</span></span>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [<span data-ttu-id="29a64-109">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="29a64-109">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="29a64-110">Vue d'ensemble des plans conceptuels</span><span class="sxs-lookup"><span data-stu-id="29a64-110">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="29a64-111">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="29a64-111">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="29a64-112">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="29a64-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="29a64-113">Graphiques et multimédia</span><span class="sxs-lookup"><span data-stu-id="29a64-113">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
