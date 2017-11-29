---
title: "Comment : dessiner une ellipse ou un cercle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4da623c34b4c3b84dee0f02d631d032eb1c061d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="b5cf0-102">Comment : dessiner une ellipse ou un cercle</span><span class="sxs-lookup"><span data-stu-id="b5cf0-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="b5cf0-103">Cet exemple montre comment dessiner des ellipses et des cercles à l’aide de la <xref:System.Windows.Shapes.Ellipse> élément.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="b5cf0-104">Pour dessiner une ellipse, créez un <xref:System.Windows.Shapes.Ellipse> élément et spécifiez son <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="b5cf0-105">Utilisez ses <xref:System.Windows.Shapes.Shape.Fill%2A> propriété pour spécifier le <xref:System.Windows.Media.Brush> qui est utilisé pour peindre l’intérieur de l’ellipse.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="b5cf0-106">Utilisez ses <xref:System.Windows.Shapes.Shape.Stroke%2A> propriété pour spécifier le <xref:System.Windows.Media.Brush> qui est utilisé pour peindre le contour de l’ellipse.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="b5cf0-107">Le <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propriété spécifie l’épaisseur du contour de l’ellipse.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="b5cf0-108">Pour tracer un cercle, vérifiez le <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> de la <xref:System.Windows.Shapes.Ellipse> élément égal à l’autre.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="b5cf0-109">L’exemple suivant dessine quatre <xref:System.Windows.Shapes.Ellipse> éléments au sein d’un <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5cf0-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5cf0-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="b5cf0-111">Bien que cet exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les points de suspension, vous pouvez utiliser des éléments de l’ellipse (et tous les autres éléments de forme) avec n’importe quelle <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.</span><span class="sxs-lookup"><span data-stu-id="b5cf0-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="b5cf0-112">Cet exemple fait partie d’un exemple plus complet ; Pour obtenir un exemple complet, consultez [éléments de forme, exemple](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="b5cf0-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5cf0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5cf0-113">See Also</span></span>  
 <xref:System.Windows.Shapes.Ellipse>  
 <xref:System.Windows.Shapes.Shape>  
 [<span data-ttu-id="b5cf0-114">Éléments de forme, exemple</span><span class="sxs-lookup"><span data-stu-id="b5cf0-114">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)
