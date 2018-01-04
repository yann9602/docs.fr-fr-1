---
title: "Comment : définir la taille de la mosaïque pour un TileBrush"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e9b746fe66635054dbd35463f727d28a8abd3d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="ef3f5-102">Comment : définir la taille de la mosaïque pour un TileBrush</span><span class="sxs-lookup"><span data-stu-id="ef3f5-102">How to: Set the Tile Size for a TileBrush</span></span>
<span data-ttu-id="ef3f5-103">Cet exemple montre comment définir la taille des mosaïques pour un <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="ef3f5-104">Par défaut, un <xref:System.Windows.Media.TileBrush> produit une seule mosaïque qui remplit complètement la zone qui vous sont en train de peindre.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="ef3f5-105">Vous pouvez substituer ce comportement en définissant le <xref:System.Windows.Media.TileBrush.Viewport%2A> et <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>  
  
 <span data-ttu-id="ef3f5-106">Le <xref:System.Windows.Media.TileBrush.Viewport%2A> propriété spécifie la taille des mosaïques pour un <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="ef3f5-107">Par défaut, la valeur de la <xref:System.Windows.Media.TileBrush.Viewport%2A> propriété est relative à la taille de la zone qui est peinte.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="ef3f5-108">Pour rendre le <xref:System.Windows.Media.TileBrush.Viewport%2A> propriété spécifier une taille de mosaïque absolue, définissez la <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriété <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef3f5-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="ef3f5-109">Example</span></span>  
 <span data-ttu-id="ef3f5-110">L’exemple suivant utilise une <xref:System.Windows.Media.ImageBrush>, un type de <xref:System.Windows.Media.TileBrush>, pour peindre un rectangle avec des mosaïques.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="ef3f5-111">L’exemple définit chaque mosaïque à 50 % de 50 % de la zone de sortie (le rectangle).</span><span class="sxs-lookup"><span data-stu-id="ef3f5-111">The example sets each tile to  50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="ef3f5-112">Le rectangle est donc peint avec quatre projections de l’image.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-112">As a result, the rectangle is painted with four projections of the image.</span></span>  
  
 <span data-ttu-id="ef3f5-113">L’illustration suivante montre le résultat obtenu avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-113">The following illustration shows the output that the example produces.</span></span>
  
 <span data-ttu-id="ef3f5-114">![Exemple de mosaïque avec un pinceau image](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")</span><span class="sxs-lookup"><span data-stu-id="ef3f5-114">![Example of tiling with an image brush](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 <span data-ttu-id="ef3f5-115">L’exemple suivant crée un <xref:System.Windows.Media.ImageBrush>, définit son <xref:System.Windows.Media.TileBrush.Viewport%2A> à `0,0,25,25` et son <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> à <xref:System.Windows.Media.BrushMappingMode.Absolute>et l’utilise pour peindre un autre rectangle.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="ef3f5-116">Le pinceau produit ainsi des mosaïques d’une largeur de 25 pixels et d’une hauteur de 25 pixels.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>  
  
 <span data-ttu-id="ef3f5-117">L’illustration suivante montre le résultat obtenu avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-117">The following illustration shows the output that the example produces.</span></span>  
  
 <span data-ttu-id="ef3f5-118">![TileBrush en mosaïque avec Viewport de 0,0, 0,25 et 0,25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")</span><span class="sxs-lookup"><span data-stu-id="ef3f5-118">![A tiled TileBrush with a Viewport of 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 <span data-ttu-id="ef3f5-119">Les exemples précédents font partie d’un exemple plus complet.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="ef3f5-120">Pour obtenir un exemple complet, consultez [ImageBrush, exemple](http://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="ef3f5-120">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
 <span data-ttu-id="ef3f5-121">Bien que cet exemple utilise le <xref:System.Windows.Media.ImageBrush> (classe), le <xref:System.Windows.Media.TileBrush.Viewport%2A> et <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriétés se comportent de façon identique pour les autres <xref:System.Windows.Media.TileBrush> des objets, autrement dit, pour <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="ef3f5-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="ef3f5-122">Pour plus d’informations sur <xref:System.Windows.Media.ImageBrush> et l’autre <xref:System.Windows.Media.TileBrush> , consultez [peinture avec des Images, des dessins et des éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="ef3f5-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef3f5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef3f5-123">See Also</span></span>  
 <xref:System.Windows.Media.TileBrush>  
 [<span data-ttu-id="ef3f5-124">Peinture avec des images, des dessins et des objets visuels</span><span class="sxs-lookup"><span data-stu-id="ef3f5-124">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="ef3f5-125">Créer différents modèles de mosaïque avec un TileBrush</span><span class="sxs-lookup"><span data-stu-id="ef3f5-125">Create Different Tile Patterns with a TileBrush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
