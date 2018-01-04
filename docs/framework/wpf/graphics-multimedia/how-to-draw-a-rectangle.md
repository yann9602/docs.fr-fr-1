---
title: "Comment : dessiner un rectangle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58f29783e48aa7173010ffec6a65f9ac1d8a2b62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="6dcb1-102">Comment : dessiner un rectangle</span><span class="sxs-lookup"><span data-stu-id="6dcb1-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="6dcb1-103">Cet exemple montre comment dessiner un rectangle à l’aide de la <xref:System.Windows.Shapes.Rectangle> élément.</span><span class="sxs-lookup"><span data-stu-id="6dcb1-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="6dcb1-104">Pour dessiner un rectangle, créez un <xref:System.Windows.Shapes.Rectangle> élément et spécifiez son <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="6dcb1-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="6dcb1-105">Pour peindre l’intérieur du rectangle, définissez son <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="6dcb1-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="6dcb1-106">Pour donner le rectangle à un plan, utilisez son <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="6dcb1-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="6dcb1-107">Le rectangle de donner des angles arrondis, spécifiez le paramètre facultatif <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="6dcb1-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="6dcb1-108">Le <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> propriétés définies les rayons des axes x et y de l’ellipse utilisée pour arrondir les angles du rectangle.</span><span class="sxs-lookup"><span data-stu-id="6dcb1-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="6dcb1-109">Dans l’exemple suivant, deux <xref:System.Windows.Shapes.Rectangle> éléments sont dessinées dans une <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="6dcb1-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="6dcb1-110">Le premier rectangle est un <xref:System.Windows.Media.Brushes.Blue%2A> intérieurs.</span><span class="sxs-lookup"><span data-stu-id="6dcb1-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="6dcb1-111">Le deuxième rectangle a un <xref:System.Windows.Media.Brushes.Blue%2A> intérieurs, une <xref:System.Windows.Media.Brushes.Black%2A> plan et des angles arrondis.</span><span class="sxs-lookup"><span data-stu-id="6dcb1-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dcb1-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="6dcb1-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="6dcb1-113">Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les rectangles, vous pouvez utiliser des éléments de rectangle (et tous les autres éléments de forme) avec n’importe quelle <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.</span><span class="sxs-lookup"><span data-stu-id="6dcb1-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="6dcb1-114">En fait, les rectangles sont particulièrement utiles pour fournir des arrière-plans pour certaines parties de <xref:System.Windows.Controls.Grid> panneaux.</span><span class="sxs-lookup"><span data-stu-id="6dcb1-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="6dcb1-115">Pour obtenir un exemple, consultez la [vue d’ensemble de la Table](../../../../docs/framework/wpf/advanced/table-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6dcb1-115">For an example, see the [Table Overview](../../../../docs/framework/wpf/advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="6dcb1-116">Cet exemple fait partie d’un exemple plus complet ; Pour obtenir un exemple complet, consultez [éléments de forme, exemple](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="6dcb1-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dcb1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dcb1-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Rectangle>  
 [<span data-ttu-id="6dcb1-118">Éléments de forme, exemple</span><span class="sxs-lookup"><span data-stu-id="6dcb1-118">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [<span data-ttu-id="6dcb1-119">Vue d’ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="6dcb1-119">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="6dcb1-120">Vue d’ensemble de Table</span><span class="sxs-lookup"><span data-stu-id="6dcb1-120">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
