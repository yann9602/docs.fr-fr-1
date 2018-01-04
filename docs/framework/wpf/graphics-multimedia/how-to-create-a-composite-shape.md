---
title: "Comment : créer une forme composite"
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
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ecb4ecdc5c83cbb6f2b4faee9cb3654939bd346
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="12126-102">Comment : créer une forme composite</span><span class="sxs-lookup"><span data-stu-id="12126-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="12126-103">Cet exemple montre comment créer des formes composites à l’aide de <xref:System.Windows.Media.Geometry> objets et les afficher à l’aide un <xref:System.Windows.Shapes.Path> élément.</span><span class="sxs-lookup"><span data-stu-id="12126-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="12126-104">Dans l’exemple suivant, un <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>et un <xref:System.Windows.Media.RectangleGeometry> sont utilisés avec un <xref:System.Windows.Media.GeometryGroup> pour créer une forme composite.</span><span class="sxs-lookup"><span data-stu-id="12126-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="12126-105">Les géométries sont ensuite dessinées à l’aide un <xref:System.Windows.Shapes.Path> élément.</span><span class="sxs-lookup"><span data-stu-id="12126-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12126-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="12126-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="12126-107">L’illustration suivante montre la forme créée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="12126-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="12126-108">![Géométrie composée créée à l’aide de GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="12126-108">![A composite geometry created using a GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="12126-109">Géométrie composite</span><span class="sxs-lookup"><span data-stu-id="12126-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="12126-110">Des formes plus complexes, telles que des polygones et des formes avec des segments de courbe, peuvent être créées en utilisant un <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="12126-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="12126-111">Pour obtenir un exemple montrant comment créer une forme à l’aide un <xref:System.Windows.Media.PathGeometry>, consultez [créer une forme à l’aide de PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="12126-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="12126-112">Bien que cet exemple restitue une forme à l’écran à l’aide un <xref:System.Windows.Shapes.Path> élément, <xref:System.Windows.Media.Geometry> objets peuvent également être utilisés pour décrire le contenu d’un <xref:System.Windows.Media.GeometryDrawing> ou <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="12126-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="12126-113">Ils peuvent également être utilisés pour le découpage et le test de positionnement.</span><span class="sxs-lookup"><span data-stu-id="12126-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="12126-114">Cet exemple fait partie d’un exemple plus vaste ; pour l’exemple complet, consultez [Géométries, exemple](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="12126-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>
