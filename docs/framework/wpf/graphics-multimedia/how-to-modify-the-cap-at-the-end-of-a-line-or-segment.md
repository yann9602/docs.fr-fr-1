---
title: "Comment : modifier l'embout à la fin d'une ligne ou d'un segment"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e062b82e698a99705a2b06588aa9aae3a0c93157
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="7830a-102">Comment : modifier l'embout à la fin d'une ligne ou d'un segment</span><span class="sxs-lookup"><span data-stu-id="7830a-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="7830a-103">Cet exemple montre comment modifier la forme au début ou à la fin d’open <xref:System.Windows.Shapes.Shape> élément.</span><span class="sxs-lookup"><span data-stu-id="7830a-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="7830a-104">Pour modifier l’embout au début de l’open <xref:System.Windows.Shapes.Shape>, utilisez son <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="7830a-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="7830a-105">Pour modifier l’embout à la fin d’open <xref:System.Windows.Shapes.Shape>, utilisez son <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="7830a-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="7830a-106">Pour afficher les embouts de ligne disponibles, consultez le <xref:System.Windows.Media.PenLineCap> énumération.</span><span class="sxs-lookup"><span data-stu-id="7830a-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7830a-107">Cette propriété affecte uniquement une forme ouverte, comme un <xref:System.Windows.Shapes.Line>, un <xref:System.Windows.Shapes.Polyline>, ou open <xref:System.Windows.Shapes.Path> élément.</span><span class="sxs-lookup"><span data-stu-id="7830a-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="7830a-108">L’exemple suivant dessine quatre <xref:System.Windows.Shapes.Polyline> éléments et utilise un autre ensemble de formes à la fin de chacun.</span><span class="sxs-lookup"><span data-stu-id="7830a-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7830a-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="7830a-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="7830a-110">Cet exemple fait partie d’un exemple plus complet ; Pour obtenir un exemple complet, consultez [éléments de forme, exemple](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="7830a-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7830a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7830a-111">See Also</span></span>  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Media.PenLineCap>
