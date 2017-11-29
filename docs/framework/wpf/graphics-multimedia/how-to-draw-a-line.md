---
title: "Comment : dessiner une ligne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4911aea91416fb84e9a18d54c145b494737ef9dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="0bb10-102">Comment : dessiner une ligne</span><span class="sxs-lookup"><span data-stu-id="0bb10-102">How to: Draw a Line</span></span>
<span data-ttu-id="0bb10-103">Cet exemple vous montre comment dessiner des lignes à l’aide de la <xref:System.Windows.Shapes.Line> élément.</span><span class="sxs-lookup"><span data-stu-id="0bb10-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="0bb10-104">Pour dessiner une ligne, créez un <xref:System.Windows.Shapes.Line> élément.</span><span class="sxs-lookup"><span data-stu-id="0bb10-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="0bb10-105">Utiliser sa <xref:System.Windows.Shapes.Line.X1%2A> et <xref:System.Windows.Shapes.Line.Y1%2A> propriétés pour définir son point de départ ; et ses <xref:System.Windows.Shapes.Line.X2%2A> et <xref:System.Windows.Shapes.Line.Y2%2A> propriétés à définir son point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0bb10-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="0bb10-106">Enfin, définissez son <xref:System.Windows.Shapes.Shape.Stroke%2A> et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> , car une ligne sans trait est invisible.</span><span class="sxs-lookup"><span data-stu-id="0bb10-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="0bb10-107">Définition de la <xref:System.Windows.Shapes.Shape.Fill%2A> , élément pour une ligne n’a aucun effet, car une ligne n’a pas d’intérieur.</span><span class="sxs-lookup"><span data-stu-id="0bb10-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="0bb10-108">L’exemple suivant dessine trois lignes dans un <xref:System.Windows.Controls.Canvas> élément.</span><span class="sxs-lookup"><span data-stu-id="0bb10-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bb10-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="0bb10-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="0bb10-110">Cet exemple fait partie d’un exemple plus complet ; Pour obtenir un exemple complet, consultez [éléments de forme, exemple](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="0bb10-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb10-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bb10-111">See Also</span></span>  
 <xref:System.Windows.Shapes.Line>  
 [<span data-ttu-id="0bb10-112">Éléments de forme, exemple</span><span class="sxs-lookup"><span data-stu-id="0bb10-112">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)
