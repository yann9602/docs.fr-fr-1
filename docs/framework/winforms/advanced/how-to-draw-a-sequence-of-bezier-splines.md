---
title: "Comment : dessiner une séquence de B &#233; Splines de Bézier"
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
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5bdd9ae29dcbb8397d2fe645e240572aad32a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="f4516-102">Comment : dessiner une séquence de B &#233; Splines de Bézier</span><span class="sxs-lookup"><span data-stu-id="f4516-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="f4516-103">Vous pouvez utiliser la <xref:System.Drawing.Graphics.DrawBeziers%2A> méthode de la <xref:System.Drawing.Graphics> classe pour dessiner une séquence de splines de Bézier reliées.</span><span class="sxs-lookup"><span data-stu-id="f4516-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4516-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f4516-104">Example</span></span>  
 <span data-ttu-id="f4516-105">L’exemple suivant dessine une courbe qui se compose de deux splines de Bézier connectés.</span><span class="sxs-lookup"><span data-stu-id="f4516-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="f4516-106">Le point de terminaison de la première spline de Bézier est le point de départ de la deuxième spline de Bézier.</span><span class="sxs-lookup"><span data-stu-id="f4516-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="f4516-107">L’illustration suivante montre les splines reliées et les sept points.</span><span class="sxs-lookup"><span data-stu-id="f4516-107">The following illustration shows the connected splines along with the seven points.</span></span>  
  
 <span data-ttu-id="f4516-108">![Spline de Bézier](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span><span class="sxs-lookup"><span data-stu-id="f4516-108">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f4516-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f4516-109">Compiling the Code</span></span>  
 <span data-ttu-id="f4516-110">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="f4516-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4516-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4516-111">See Also</span></span>  
 [<span data-ttu-id="f4516-112">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4516-112">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="f4516-113">Splines de Bézier dans GDI+</span><span class="sxs-lookup"><span data-stu-id="f4516-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [<span data-ttu-id="f4516-114">Génération et dessin de courbes</span><span class="sxs-lookup"><span data-stu-id="f4516-114">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
