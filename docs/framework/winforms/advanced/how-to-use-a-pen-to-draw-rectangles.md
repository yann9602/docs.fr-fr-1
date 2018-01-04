---
title: "Comment : utiliser un stylet pour dessiner des rectangles"
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
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7257fa21432ec5d849a257f4a5e412515f474363
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a><span data-ttu-id="cbe42-102">Comment : utiliser un stylet pour dessiner des rectangles</span><span class="sxs-lookup"><span data-stu-id="cbe42-102">How to: Use a Pen to Draw Rectangles</span></span>
<span data-ttu-id="cbe42-103">Pour dessiner des rectangles, vous avez besoin une <xref:System.Drawing.Graphics> objet et un <xref:System.Drawing.Pen> objet.</span><span class="sxs-lookup"><span data-stu-id="cbe42-103">To draw rectangles, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="cbe42-104">Le <xref:System.Drawing.Graphics> objet fournit les <xref:System.Drawing.Graphics.DrawRectangle%2A> (méthode) et le <xref:System.Drawing.Pen> objet stocke les fonctionnalités de la ligne, telles que la couleur et la largeur.</span><span class="sxs-lookup"><span data-stu-id="cbe42-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbe42-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="cbe42-105">Example</span></span>  
 <span data-ttu-id="cbe42-106">L’exemple suivant dessine un rectangle avec son coin supérieur gauche à (10, 10).</span><span class="sxs-lookup"><span data-stu-id="cbe42-106">The following example draws a rectangle with its upper-left corner at (10, 10).</span></span> <span data-ttu-id="cbe42-107">Le rectangle a une largeur de 100 et une hauteur de 50.</span><span class="sxs-lookup"><span data-stu-id="cbe42-107">The rectangle has a width of 100 and a height of 50.</span></span> <span data-ttu-id="cbe42-108">Le deuxième argument passé à la <xref:System.Drawing.Pen.%23ctor%2A> constructeur indique que la largeur du stylet est de 5 pixels.</span><span class="sxs-lookup"><span data-stu-id="cbe42-108">The second argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor indicates that the pen width is 5 pixels.</span></span>  
  
 <span data-ttu-id="cbe42-109">Lorsque le rectangle est dessiné, le stylet est centré sur la limite du rectangle.</span><span class="sxs-lookup"><span data-stu-id="cbe42-109">When the rectangle is drawn, the pen is centered on the rectangle's boundary.</span></span> <span data-ttu-id="cbe42-110">Étant donné que la largeur du stylet est 5, les côtés du rectangle sont dessinés 5 pixels large, par exemple : 1 pixel est dessiné sur la limite proprement dite, 2 pixels sont dessinées à l’intérieur et 2 pixels sont dessinées à l’extérieur.</span><span class="sxs-lookup"><span data-stu-id="cbe42-110">Because the pen width is 5, the sides of the rectangle are drawn 5 pixels wide, such that 1 pixel is drawn on the boundary itself, 2 pixels are drawn on the inside, and 2 pixels are drawn on the outside.</span></span> <span data-ttu-id="cbe42-111">Pour plus d’informations sur l’alignement du stylet, consultez [Comment : définir la largeur et l’alignement](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).</span><span class="sxs-lookup"><span data-stu-id="cbe42-111">For more details on pen alignment, see [How to: Set Pen Width and Alignment](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).</span></span>  
  
 <span data-ttu-id="cbe42-112">L’illustration suivante montre le rectangle résultant.</span><span class="sxs-lookup"><span data-stu-id="cbe42-112">The following illustration shows the resulting rectangle.</span></span> <span data-ttu-id="cbe42-113">Les lignes discontinues montrent où le rectangle aurait été dessiné Si la largeur du stylet avait été un pixel.</span><span class="sxs-lookup"><span data-stu-id="cbe42-113">The dotted lines show where the rectangle would have been drawn if the pen width had been one pixel.</span></span> <span data-ttu-id="cbe42-114">L’affichage agrandi de l’angle supérieur gauche du rectangle montre que les lignes noires épaisses sont centrées sur les lignes en pointillés.</span><span class="sxs-lookup"><span data-stu-id="cbe42-114">The enlarged view of the upper-left corner of the rectangle shows that the thick black lines are centered on those dotted lines.</span></span>  
  
 <span data-ttu-id="cbe42-115">![Stylets](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")</span><span class="sxs-lookup"><span data-stu-id="cbe42-115">![Pens](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cbe42-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="cbe42-116">Compiling the Code</span></span>  
 <span data-ttu-id="cbe42-117">L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="cbe42-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe42-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbe42-118">See Also</span></span>  
 [<span data-ttu-id="cbe42-119">Utilisation d'un stylet pour dessiner des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="cbe42-119">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
