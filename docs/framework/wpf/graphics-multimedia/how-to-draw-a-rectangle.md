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
ms.openlocfilehash: 4c163897af27c9b34c8cd87a3b197047f86d21ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="7bf9c-102">Comment : dessiner un rectangle</span><span class="sxs-lookup"><span data-stu-id="7bf9c-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="7bf9c-103">Cet exemple montre comment dessiner un rectangle à l’aide de la <xref:System.Windows.Shapes.Rectangle> élément.</span><span class="sxs-lookup"><span data-stu-id="7bf9c-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="7bf9c-104">Pour dessiner un rectangle, créez un <xref:System.Windows.Shapes.Rectangle> élément et spécifiez son <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="7bf9c-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="7bf9c-105">Pour peindre l’intérieur du rectangle, définissez son <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="7bf9c-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="7bf9c-106">Pour donner le rectangle à un plan, utilisez son <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="7bf9c-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="7bf9c-107">Le rectangle de donner des angles arrondis, spécifiez le paramètre facultatif <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="7bf9c-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="7bf9c-108">Le <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> propriétés définies les rayons des axes x et y de l’ellipse utilisée pour arrondir les angles du rectangle.</span><span class="sxs-lookup"><span data-stu-id="7bf9c-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="7bf9c-109">Dans l’exemple suivant, deux <xref:System.Windows.Shapes.Rectangle> éléments sont dessinées dans une <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="7bf9c-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="7bf9c-110">Le premier rectangle est un <xref:System.Windows.Media.Brushes.Blue%2A> intérieurs.</span><span class="sxs-lookup"><span data-stu-id="7bf9c-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="7bf9c-111">Le deuxième rectangle a un <xref:System.Windows.Media.Brushes.Blue%2A> intérieurs, une <xref:System.Windows.Media.Brushes.Black%2A> plan et des angles arrondis.</span><span class="sxs-lookup"><span data-stu-id="7bf9c-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bf9c-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="7bf9c-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="7bf9c-113">Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les rectangles, vous pouvez utiliser des éléments de rectangle (et tous les autres éléments de forme) avec n’importe quelle <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.</span><span class="sxs-lookup"><span data-stu-id="7bf9c-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="7bf9c-114">En fait, les rectangles sont particulièrement utiles pour fournir des arrière-plans pour certaines parties de <xref:System.Windows.Controls.Grid> panneaux.</span><span class="sxs-lookup"><span data-stu-id="7bf9c-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="7bf9c-115">Pour obtenir un exemple, consultez la [vue d’ensemble de la Table](../../../../docs/framework/wpf/advanced/table-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7bf9c-115">For an example, see the [Table Overview](../../../../docs/framework/wpf/advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="7bf9c-116">Cet exemple fait partie d’un exemple plus complet ; Pour obtenir un exemple complet, consultez [éléments de forme, exemple](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="7bf9c-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf9c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bf9c-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Rectangle>  
 [<span data-ttu-id="7bf9c-118">Éléments de forme, exemple</span><span class="sxs-lookup"><span data-stu-id="7bf9c-118">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [<span data-ttu-id="7bf9c-119">Vue d’ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="7bf9c-119">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="7bf9c-120">Vue d’ensemble de Table</span><span class="sxs-lookup"><span data-stu-id="7bf9c-120">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
