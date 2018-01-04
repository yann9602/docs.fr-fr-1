---
title: "Comment : créer un dessin composite"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 424f77b076344ad86db992614175243d1473886d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-composite-drawing"></a><span data-ttu-id="073b3-102">Comment : créer un dessin composite</span><span class="sxs-lookup"><span data-stu-id="073b3-102">How to: Create a Composite Drawing</span></span>
<span data-ttu-id="073b3-103">Cet exemple montre comment utiliser un <xref:System.Windows.Media.DrawingGroup> pour créer des dessins complexes en combinant plusieurs <xref:System.Windows.Media.Drawing> des objets dans un seul dessin composite.</span><span class="sxs-lookup"><span data-stu-id="073b3-103">This example shows how to use a <xref:System.Windows.Media.DrawingGroup> to create complex drawings by combining multiple <xref:System.Windows.Media.Drawing> objects into a single composite drawing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="073b3-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="073b3-104">Example</span></span>  
 <span data-ttu-id="073b3-105">L’exemple suivant utilise un <xref:System.Windows.Media.DrawingGroup> pour créer un dessin composite à partir du <xref:System.Windows.Media.GeometryDrawing> et <xref:System.Windows.Media.ImageDrawing> objets.</span><span class="sxs-lookup"><span data-stu-id="073b3-105">The following example uses a <xref:System.Windows.Media.DrawingGroup> to create a composite drawing from the <xref:System.Windows.Media.GeometryDrawing> and <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="073b3-106">L’illustration suivante montre la sortie que l’exemple génère.</span><span class="sxs-lookup"><span data-stu-id="073b3-106">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="073b3-107">![DrawingGroup avec plusieurs dessins](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span><span class="sxs-lookup"><span data-stu-id="073b3-107">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span></span>  
<span data-ttu-id="073b3-108">Un dessin composite qui est créé à l’aide de DrawingGroup</span><span class="sxs-lookup"><span data-stu-id="073b3-108">A composite drawing that is created by using DrawingGroup</span></span>  
  
 <span data-ttu-id="073b3-109">Notez la bordure grise, qui affiche les limites du dessin.</span><span class="sxs-lookup"><span data-stu-id="073b3-109">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <span data-ttu-id="073b3-110">Vous pouvez utiliser un <xref:System.Windows.Media.DrawingGroup> pour appliquer un <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> définition, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, ou <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> aux dessins qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="073b3-110">You can use a <xref:System.Windows.Media.DrawingGroup> to apply a <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> setting, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, or <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> to the drawings it contains.</span></span> <span data-ttu-id="073b3-111">Car un <xref:System.Windows.Media.DrawingGroup> est également un <xref:System.Windows.Media.Drawing>, il peut contenir d’autres <xref:System.Windows.Media.DrawingGroup> objets.</span><span class="sxs-lookup"><span data-stu-id="073b3-111">Because a <xref:System.Windows.Media.DrawingGroup> is also a <xref:System.Windows.Media.Drawing>, it can contain other <xref:System.Windows.Media.DrawingGroup> objects.</span></span>  
  
 <span data-ttu-id="073b3-112">L’exemple suivant est similaire à l’exemple précédent, sauf qu’elle utilise supplémentaires <xref:System.Windows.Media.DrawingGroup> objets pour appliquer des effets bitmap et un masque d’opacité à certains dessins.</span><span class="sxs-lookup"><span data-stu-id="073b3-112">The following example is similar to the preceding example, except that it uses additional <xref:System.Windows.Media.DrawingGroup> objects to apply bitmap effects and an opacity mask to some of its drawings.</span></span> <span data-ttu-id="073b3-113">L’illustration suivante montre la sortie que l’exemple génère.</span><span class="sxs-lookup"><span data-stu-id="073b3-113">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="073b3-114">![DrawingGroup avec plusieurs dessins](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span><span class="sxs-lookup"><span data-stu-id="073b3-114">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span></span>  
<span data-ttu-id="073b3-115">Dessin composite qui contient plusieurs objets DrawingGroup</span><span class="sxs-lookup"><span data-stu-id="073b3-115">Composite drawing that has multiple DrawingGroup objects</span></span>  
  
 <span data-ttu-id="073b3-116">Notez la bordure grise, qui affiche les limites du dessin.</span><span class="sxs-lookup"><span data-stu-id="073b3-116">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <span data-ttu-id="073b3-117">Pour plus d’informations sur <xref:System.Windows.Media.Drawing> , consultez [vue d’ensemble des objets de dessin](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="073b3-117">For more information about <xref:System.Windows.Media.Drawing> objects, see [Drawing Objects Overview](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="073b3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="073b3-118">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>  
 <xref:System.Windows.Media.DrawingGroup.Transform%2A>  
 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>  
 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>  
 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>  
 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>  
 [<span data-ttu-id="073b3-119">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="073b3-119">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
