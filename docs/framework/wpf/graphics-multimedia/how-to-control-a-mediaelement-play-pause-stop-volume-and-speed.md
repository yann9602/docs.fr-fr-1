---
title: "Comment : contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)"
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
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7362c57afa3d5615ffaa0616823a954a2d577cfe
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="18d8e-102">Comment : contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)</span><span class="sxs-lookup"><span data-stu-id="18d8e-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="18d8e-103">L’exemple suivant montre comment contrôler la lecture du média à l’aide un <xref:System.Windows.Controls.MediaElement>.</span><span class="sxs-lookup"><span data-stu-id="18d8e-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="18d8e-104">L’exemple crée un lecteur multimédia simple qui vous permet de lire, suspendre, arrêter et ignorer dans les deux sens dans le support ainsi ajuster le taux de vitesse et de volume.</span><span class="sxs-lookup"><span data-stu-id="18d8e-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18d8e-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="18d8e-105">Example</span></span>  
 <span data-ttu-id="18d8e-106">Le code suivant crée l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="18d8e-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18d8e-107">Le <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriété du <xref:System.Windows.Controls.MediaElement> doit avoir la valeur `Manual` afin d’être capable de s’arrêter de manière interactive, suspendre et lire le média.</span><span class="sxs-lookup"><span data-stu-id="18d8e-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="18d8e-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="18d8e-108">Example</span></span>  
 <span data-ttu-id="18d8e-109">Le code suivant implémente les fonctionnalités des contrôles d’interface utilisateur de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="18d8e-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="18d8e-110">Le <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, et <xref:System.Windows.Controls.MediaElement.Stop%2A> méthodes sont utilisées pour lire, suspendre et arrêter le média, respectivement.</span><span class="sxs-lookup"><span data-stu-id="18d8e-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="18d8e-111">Modification de la <xref:System.Windows.Controls.MediaElement.Position%2A> propriété de la <xref:System.Windows.Controls.MediaElement> vous permet de naviguer dans le média.</span><span class="sxs-lookup"><span data-stu-id="18d8e-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="18d8e-112">Enfin, le <xref:System.Windows.Controls.MediaElement.Volume%2A> et <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> propriétés sont utilisées pour ajuster la vitesse de lecture et de volume du média.</span><span class="sxs-lookup"><span data-stu-id="18d8e-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="18d8e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18d8e-113">See Also</span></span>  
 [<span data-ttu-id="18d8e-114">Contrôler un MediaElement à l'aide d'un storyboard</span><span class="sxs-lookup"><span data-stu-id="18d8e-114">Control a MediaElement by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
