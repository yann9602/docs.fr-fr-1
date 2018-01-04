---
title: Ellipses et arcs dans GDI+
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71126942f4cde37cc5d26bfba029c5f50f1065a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ellipses-and-arcs-in-gdi"></a><span data-ttu-id="aacf7-102">Ellipses et arcs dans GDI+</span><span class="sxs-lookup"><span data-stu-id="aacf7-102">Ellipses and Arcs in GDI+</span></span>
<span data-ttu-id="aacf7-103">Vous pouvez facilement dessiner des ellipses et arcs à l’aide de la <xref:System.Drawing.Graphics.DrawEllipse%2A> et <xref:System.Drawing.Graphics.DrawArc%2A> méthodes de la <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="aacf7-103">You can easily draw ellipses and arcs using the <xref:System.Drawing.Graphics.DrawEllipse%2A> and <xref:System.Drawing.Graphics.DrawArc%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="drawing-an-ellipse"></a><span data-ttu-id="aacf7-104">Dessiner une Ellipse</span><span class="sxs-lookup"><span data-stu-id="aacf7-104">Drawing an Ellipse</span></span>  
 <span data-ttu-id="aacf7-105">Pour dessiner une ellipse, vous avez besoin une <xref:System.Drawing.Graphics> objet et un <xref:System.Drawing.Pen> objet.</span><span class="sxs-lookup"><span data-stu-id="aacf7-105">To draw an ellipse, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="aacf7-106">Le <xref:System.Drawing.Graphics> objet fournit les <xref:System.Drawing.Graphics.DrawEllipse%2A> (méthode) et le <xref:System.Drawing.Pen> objet stocke des attributs, tels que la largeur et la couleur, de la ligne utilisée pour représenter l’ellipse.</span><span class="sxs-lookup"><span data-stu-id="aacf7-106">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the ellipse.</span></span> <span data-ttu-id="aacf7-107">Le <xref:System.Drawing.Pen> objet est passé en tant qu’arguments à la <xref:System.Drawing.Graphics.DrawEllipse%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="aacf7-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="aacf7-108">Les autres arguments passés à la <xref:System.Drawing.Graphics.DrawEllipse%2A> méthode définissent le rectangle englobant de l’ellipse.</span><span class="sxs-lookup"><span data-stu-id="aacf7-108">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method specify the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="aacf7-109">L’illustration suivante montre une ellipse, ainsi que son rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="aacf7-109">The following illustration shows an ellipse along with its bounding rectangle.</span></span>  
  
 <span data-ttu-id="aacf7-110">![Ellipses et arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span><span class="sxs-lookup"><span data-stu-id="aacf7-110">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span></span>  
  
 <span data-ttu-id="aacf7-111">L’exemple suivant dessine une ellipse ; le rectangle englobant d’une largeur de 80, une hauteur de 40 et un coin supérieur gauche de (100, 50) :</span><span class="sxs-lookup"><span data-stu-id="aacf7-111">The following example draws an ellipse; the bounding rectangle has a width of 80, a height of 40, and an upper-left corner of (100, 50):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <span data-ttu-id="aacf7-112"><xref:System.Drawing.Graphics.DrawEllipse%2A>est une méthode surchargée de la <xref:System.Drawing.Graphics> classe, il y a plusieurs façons, vous pouvez lui fournir avec des arguments.</span><span class="sxs-lookup"><span data-stu-id="aacf7-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="aacf7-113">Par exemple, vous pouvez construire un <xref:System.Drawing.Rectangle> et passer le <xref:System.Drawing.Rectangle> à la <xref:System.Drawing.Graphics.DrawEllipse%2A> méthode en tant qu’argument :</span><span class="sxs-lookup"><span data-stu-id="aacf7-113">For example, you can construct a <xref:System.Drawing.Rectangle> and pass the <xref:System.Drawing.Rectangle> to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a><span data-ttu-id="aacf7-114">Dessin d’un Arc</span><span class="sxs-lookup"><span data-stu-id="aacf7-114">Drawing an Arc</span></span>  
 <span data-ttu-id="aacf7-115">Un arc est une partie d’une ellipse.</span><span class="sxs-lookup"><span data-stu-id="aacf7-115">An arc is a portion of an ellipse.</span></span> <span data-ttu-id="aacf7-116">Pour dessiner un arc, appelez le <xref:System.Drawing.Graphics.DrawArc%2A> méthode de la <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="aacf7-116">To draw an arc, you call the <xref:System.Drawing.Graphics.DrawArc%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="aacf7-117">Les paramètres de la <xref:System.Drawing.Graphics.DrawArc%2A> méthode sont les mêmes que les paramètres de la <xref:System.Drawing.Graphics.DrawEllipse%2A> (méthode), à ceci près que <xref:System.Drawing.Graphics.DrawArc%2A> nécessite un angle de départ et un angle de balayage.</span><span class="sxs-lookup"><span data-stu-id="aacf7-117">The parameters of the <xref:System.Drawing.Graphics.DrawArc%2A> method are the same as the parameters of the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, except that <xref:System.Drawing.Graphics.DrawArc%2A> requires a starting angle and sweep angle.</span></span> <span data-ttu-id="aacf7-118">L’exemple suivant dessine un arc avec un angle de départ de 30 degrés et l’angle de balayage de 180 degrés :</span><span class="sxs-lookup"><span data-stu-id="aacf7-118">The following example draws an arc with a starting angle of 30 degrees and a sweep angle of 180 degrees:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 <span data-ttu-id="aacf7-119">L’illustration suivante montre l’arc, l’ellipse et le rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="aacf7-119">The following illustration shows the arc, the ellipse, and the bounding rectangle.</span></span>  
  
 <span data-ttu-id="aacf7-120">![Ellipses et arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span><span class="sxs-lookup"><span data-stu-id="aacf7-120">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aacf7-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aacf7-121">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="aacf7-122">Lignes, courbes et formes</span><span class="sxs-lookup"><span data-stu-id="aacf7-122">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="aacf7-123">Guide pratique pour créer des objets graphiques pour le dessin</span><span class="sxs-lookup"><span data-stu-id="aacf7-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="aacf7-124">Guide pratique pour créer un stylet</span><span class="sxs-lookup"><span data-stu-id="aacf7-124">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [<span data-ttu-id="aacf7-125">Guide pratique pour dessiner une forme avec contour</span><span class="sxs-lookup"><span data-stu-id="aacf7-125">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
