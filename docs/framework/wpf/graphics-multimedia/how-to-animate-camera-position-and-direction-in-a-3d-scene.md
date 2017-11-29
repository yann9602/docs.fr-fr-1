---
title: "Comment : animer la position et la direction d'une caméra dans une scène 3D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 790260f974dcb0be398af202cc7156fc91efed91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a><span data-ttu-id="4a969-102">Comment : animer la position et la direction d'une caméra dans une scène 3D</span><span class="sxs-lookup"><span data-stu-id="4a969-102">How to: Animate Camera Position and Direction in a 3D Scene</span></span>
<span data-ttu-id="4a969-103">L’exemple suivant montre comment animer la position d’une caméra et animer la direction qu’il pointe dans une scène 3D.</span><span class="sxs-lookup"><span data-stu-id="4a969-103">The following example shows how to animate the position of a camera and animate the direction it is pointing in a 3D scene.</span></span> <span data-ttu-id="4a969-104">Il incombe à l’aide de <xref:System.Windows.Media.Animation.Point3DAnimation> et <xref:System.Windows.Media.Animation.Vector3DAnimation> pour animer la <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> et <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> propriétés respectivement de la <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span><span class="sxs-lookup"><span data-stu-id="4a969-104">This is done by using <xref:System.Windows.Media.Animation.Point3DAnimation> and <xref:System.Windows.Media.Animation.Vector3DAnimation> to animate the <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> and <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> properties respectively of the <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="4a969-105">Vous pouvez utiliser une animation comme suit pour modifier la vue du spectateur d’une scène en réponse à un événement.</span><span class="sxs-lookup"><span data-stu-id="4a969-105">You might use an animation like this to change the onlooker's view of a scene in response to an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a969-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="4a969-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="4a969-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a969-107">See Also</span></span>  
 <xref:System.Windows.Media.Animation.Vector3DAnimation>  
 <xref:System.Windows.Media.Animation.Point3DAnimation>  
 [<span data-ttu-id="4a969-108">Animer la position et la direction de la caméra à l’aide d’images clés</span><span class="sxs-lookup"><span data-stu-id="4a969-108">Animate Camera Position and Direction Using Key Frames</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)  
 [<span data-ttu-id="4a969-109">Vue d’ensemble des graphiques 3D</span><span class="sxs-lookup"><span data-stu-id="4a969-109">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
