---
title: "Comment : peindre une zone avec un dessin"
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
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1db788ae0fabdfd27cf215bfcf466c41df19c637
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-a-drawing"></a><span data-ttu-id="8cfb1-102">Comment : peindre une zone avec un dessin</span><span class="sxs-lookup"><span data-stu-id="8cfb1-102">How to: Paint an Area with a Drawing</span></span>
<span data-ttu-id="8cfb1-103">Cet exemple explique comment peindre une zone avec un dessin.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-103">This example shows how to paint an area with a drawing.</span></span> <span data-ttu-id="8cfb1-104">Pour peindre une zone avec un dessin, vous utilisez un <xref:System.Windows.Media.DrawingBrush> et un ou plusieurs <xref:System.Windows.Media.Drawing> objets.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-104">To paint an area with a drawing, you use a <xref:System.Windows.Media.DrawingBrush> and one or more <xref:System.Windows.Media.Drawing> objects.</span></span>   <span data-ttu-id="8cfb1-105">L’exemple suivant utilise un <xref:System.Windows.Media.DrawingBrush> pour peindre un objet avec un dessin de deux ellipses.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-105">The following example uses a <xref:System.Windows.Media.DrawingBrush> to paint an object with a drawing of two ellipses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cfb1-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="8cfb1-106">Example</span></span>  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 <span data-ttu-id="8cfb1-107">L’illustration suivante montre le résultat de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-107">The following illustration shows the example's output.</span></span>  
  
 <span data-ttu-id="8cfb1-108">![Résultat d’un DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span><span class="sxs-lookup"><span data-stu-id="8cfb1-108">![Output from a DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span></span>  
  
 <span data-ttu-id="8cfb1-109">(Le centre de la forme est blanc pour les raisons décrites dans [contrôler le remplissage d’une forme Composite](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-the-fill-of-a-composite-shape.md).)</span><span class="sxs-lookup"><span data-stu-id="8cfb1-109">(The center of the shape is white for reasons described in     [Control the Fill of a Composite Shape](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-the-fill-of-a-composite-shape.md).)</span></span>  
  
 <span data-ttu-id="8cfb1-110">En définissant un <xref:System.Windows.Media.DrawingBrush> l’objet <xref:System.Windows.Media.TileBrush.Viewport%2A> et <xref:System.Windows.Media.TileBrush.TileMode%2A> propriétés, vous pouvez créer un modèle extensible.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-110">By setting a <xref:System.Windows.Media.DrawingBrush> object's <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties, you can create a repeating pattern.</span></span> <span data-ttu-id="8cfb1-111">L’exemple suivant peint un objet avec un modèle créé à partir d’un dessin de deux ellipses.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-111">The following example paints an object with a pattern created from a drawing of two ellipses.</span></span>  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 <span data-ttu-id="8cfb1-112">L’illustration suivante montre la mosaïque <xref:System.Windows.Media.DrawingBrush> sortie.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-112">The following illustration shows the tiled <xref:System.Windows.Media.DrawingBrush> output.</span></span>  
  
 <span data-ttu-id="8cfb1-113">![Résultat en mosaïque d’un DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span><span class="sxs-lookup"><span data-stu-id="8cfb1-113">![Tiled output from a DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span></span>  
  
 <span data-ttu-id="8cfb1-114">Pour plus d’informations sur les pinceaux de dessin, consultez [peinture avec des Images, des dessins et des éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="8cfb1-114">For more information about drawing brushes, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span> <span data-ttu-id="8cfb1-115">Pour plus d’informations sur <xref:System.Windows.Media.Drawing> , consultez la [vue d’ensemble des objets de dessin](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8cfb1-115">For more information about <xref:System.Windows.Media.Drawing> objects, see the [Drawing Objects Overview](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span></span>
