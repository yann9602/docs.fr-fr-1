---
title: "Comment : contrôler un MediaElement à l'aide d'un storyboard"
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
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f52801ee3704c13ec5213cfc54b6392baa97e245
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="b6ae0-102">Comment : contrôler un MediaElement à l'aide d'un storyboard</span><span class="sxs-lookup"><span data-stu-id="b6ae0-102">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="b6ae0-103">Cet exemple montre comment contrôler une <xref:System.Windows.Controls.MediaElement> en utilisant un <xref:System.Windows.Media.MediaTimeline> dans un <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="b6ae0-103">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6ae0-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6ae0-104">Example</span></span>  
 <span data-ttu-id="b6ae0-105">Lorsque vous utilisez un <xref:System.Windows.Media.MediaTimeline> dans un <xref:System.Windows.Media.Animation.Storyboard> pour contrôler le minutage d’une <xref:System.Windows.Controls.MediaElement>, les fonctionnalités sont identiques à celles des autres <xref:System.Windows.Media.Animation.Timeline> objets, tels que les animations.</span><span class="sxs-lookup"><span data-stu-id="b6ae0-105">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="b6ae0-106">Par exemple, un <xref:System.Windows.Media.MediaTimeline> utilise <xref:System.Windows.Media.Animation.Timeline> propriétés, telles que le <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriété pour indiquer quand commencer un <xref:System.Windows.Controls.MediaElement> (Démarrer la lecture du média).</span><span class="sxs-lookup"><span data-stu-id="b6ae0-106">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="b6ae0-107">Elle utilise également le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriété pour spécifier la durée pendant laquelle le <xref:System.Windows.Controls.MediaElement> est actif (durée de lecture du média).</span><span class="sxs-lookup"><span data-stu-id="b6ae0-107">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="b6ae0-108">Pour plus d’informations sur l’utilisation de <xref:System.Windows.Media.Animation.Timeline> objets avec un <xref:System.Windows.Media.Animation.Storyboard>, consultez [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b6ae0-108">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="b6ae0-109">Cet exemple montre comment créer un lecteur multimédia simple qui utilise un <xref:System.Windows.Media.MediaTimeline> pour contrôler la lecture.</span><span class="sxs-lookup"><span data-stu-id="b6ae0-109">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="b6ae0-110">Le lecteur multimédia comprend play, suspendre, reprendre et arrêter des boutons.</span><span class="sxs-lookup"><span data-stu-id="b6ae0-110">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="b6ae0-111">Le lecteur a également un <xref:System.Windows.Controls.Slider> contrôle qui agit comme une barre de progression.</span><span class="sxs-lookup"><span data-stu-id="b6ae0-111">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="b6ae0-112">L’exemple suivant crée le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] du lecteur multimédia.</span><span class="sxs-lookup"><span data-stu-id="b6ae0-112">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="b6ae0-113">L’exemple suivant crée les fonctionnalités de la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="b6ae0-113">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b6ae0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6ae0-114">See Also</span></span>  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="b6ae0-115">Contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)</span><span class="sxs-lookup"><span data-stu-id="b6ae0-115">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)  
 [<span data-ttu-id="b6ae0-116">Vue d'ensemble des plans conceptuels</span><span class="sxs-lookup"><span data-stu-id="b6ae0-116">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="b6ae0-117">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="b6ae0-117">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="b6ae0-118">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="b6ae0-118">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="b6ae0-119">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="b6ae0-119">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="b6ae0-120">Graphiques et multimédia</span><span class="sxs-lookup"><span data-stu-id="b6ae0-120">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
