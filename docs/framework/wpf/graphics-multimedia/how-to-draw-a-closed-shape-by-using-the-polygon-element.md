---
title: "Comment : dessiner une forme fermée à l'aide de l'élément Polygon"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b38efefa503ec3786b6e40f7b93bac59596b419f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a><span data-ttu-id="57075-102">Comment : dessiner une forme fermée à l'aide de l'élément Polygon</span><span class="sxs-lookup"><span data-stu-id="57075-102">How to: Draw a Closed Shape by Using the Polygon Element</span></span>
<span data-ttu-id="57075-103">Cet exemple montre comment dessiner une forme fermée à l’aide de la <xref:System.Windows.Shapes.Polygon> élément.</span><span class="sxs-lookup"><span data-stu-id="57075-103">This example shows how to draw a closed shape by using the <xref:System.Windows.Shapes.Polygon> element.</span></span> <span data-ttu-id="57075-104">Pour dessiner une forme fermée, créez un <xref:System.Windows.Shapes.Polygon> élément et utiliser ses <xref:System.Windows.Shapes.Polygon.Points%2A> propriété pour spécifier les sommets d’une forme.</span><span class="sxs-lookup"><span data-stu-id="57075-104">To draw a closed shape, create a <xref:System.Windows.Shapes.Polygon> element and use its <xref:System.Windows.Shapes.Polygon.Points%2A> property to specify the vertices of a shape.</span></span> <span data-ttu-id="57075-105">Une ligne est dessinée automatiquement qui se connecte le premier et le dernier point.</span><span class="sxs-lookup"><span data-stu-id="57075-105">A line is automatically drawn that connects the first and last points.</span></span> <span data-ttu-id="57075-106">Enfin, spécifiez un <xref:System.Windows.Shapes.Shape.Fill%2A>, un <xref:System.Windows.Shapes.Shape.Stroke%2A>, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="57075-106">Finally, specify a <xref:System.Windows.Shapes.Shape.Fill%2A>, a <xref:System.Windows.Shapes.Shape.Stroke%2A>, or both.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57075-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="57075-107">Example</span></span>  
 <span data-ttu-id="57075-108">Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], une syntaxe valide pour les points est une liste délimitée par l’espace de paires de séparées par des virgules coordonnées x et y.</span><span class="sxs-lookup"><span data-stu-id="57075-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 <span data-ttu-id="57075-109">Bien que l’exemple utilise un <xref:System.Windows.Controls.Canvas> pour contenir les polygones, vous pouvez utiliser des éléments de polygone (et tous les autres éléments de forme) avec n’importe quelle <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.</span><span class="sxs-lookup"><span data-stu-id="57075-109">Although the example uses a <xref:System.Windows.Controls.Canvas> to contain the polygons, you can use polygon elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="57075-110">Cet exemple fait partie d’un exemple plus complet ; Pour obtenir un exemple complet, consultez [éléments de forme, exemple](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="57075-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>
