---
title: "Comment : définir la largeur et l'alignement du stylet"
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
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6ed2a28c49554c686abb5e2635ab35b746b83465
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-pen-width-and-alignment"></a><span data-ttu-id="ebdd3-102">Comment : définir la largeur et l'alignement du stylet</span><span class="sxs-lookup"><span data-stu-id="ebdd3-102">How to: Set Pen Width and Alignment</span></span>
<span data-ttu-id="ebdd3-103">Lorsque vous créez un <xref:System.Drawing.Pen>, vous pouvez fournir la largeur du stylet comme l’un des arguments au constructeur.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-103">When you create a <xref:System.Drawing.Pen>, you can supply the pen width as one of the arguments to the constructor.</span></span> <span data-ttu-id="ebdd3-104">Vous pouvez également modifier la largeur du stylet avec le <xref:System.Drawing.Pen.Width%2A> propriété de la <xref:System.Drawing.Pen> classe.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-104">You can also change the pen width with the <xref:System.Drawing.Pen.Width%2A> property of the <xref:System.Drawing.Pen> class.</span></span>  
  
 <span data-ttu-id="ebdd3-105">Une ligne théorique a une largeur égale à 0.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-105">A theoretical line has a width of 0.</span></span> <span data-ttu-id="ebdd3-106">Lorsque vous dessinez une ligne qui est de 1 pixel de large, les pixels sont centrés sur la ligne théorique.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-106">When you draw a line that is 1 pixel wide, the pixels are centered on the theoretical line.</span></span> <span data-ttu-id="ebdd3-107">Si vous dessinez une ligne qui est supérieure à un pixel de large, les pixels sont centrés sur la ligne théorique ou apparaissent à côté de la ligne théorique.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-107">If you draw a line that is more than one pixel wide, the pixels are either centered on the theoretical line or appear to one side of the theoretical line.</span></span> <span data-ttu-id="ebdd3-108">Vous pouvez définir la propriété d’alignement d’un <xref:System.Drawing.Pen> pour déterminer comment les pixels dessinés avec ce stylet seront positionnés par rapport aux lignes théoriques.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-108">You can set the pen alignment property of a <xref:System.Drawing.Pen> to determine how the pixels drawn with that pen will be positioned relative to theoretical lines.</span></span>  
  
 <span data-ttu-id="ebdd3-109">Les valeurs <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, et <xref:System.Drawing.Drawing2D.PenAlignment.Inset> qui apparaissent dans l’exemple suivant des exemples de code sont des membres de la <xref:System.Drawing.Drawing2D.PenAlignment> énumération.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-109">The values <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, and <xref:System.Drawing.Drawing2D.PenAlignment.Inset> that appear in the following code examples are members of the <xref:System.Drawing.Drawing2D.PenAlignment> enumeration.</span></span>  
  
 <span data-ttu-id="ebdd3-110">L’exemple de code suivant dessine une ligne deux fois : une fois avec un stylet noir d’une largeur de 1 et une fois avec un stylet vert d’une largeur de 10.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-110">The following code example draws a line twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
### <a name="to-vary-the-width-of-a-pen"></a><span data-ttu-id="ebdd3-111">Pour faire varier la largeur d’un stylet</span><span class="sxs-lookup"><span data-stu-id="ebdd3-111">To vary the width of a pen</span></span>  
  
-   <span data-ttu-id="ebdd3-112">Définir la valeur de la <xref:System.Drawing.Pen.Alignment%2A> propriété <xref:System.Drawing.Drawing2D.PenAlignment.Center> (la valeur par défaut) pour spécifier que les pixels dessinés avec le stylet vert seront centrés sur la ligne théorique.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-112">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> (the default) to specify that pixels drawn with the green pen will be centered on the theoretical line.</span></span> <span data-ttu-id="ebdd3-113">L’illustration suivante montre la ligne résultante.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-113">The following illustration shows the resulting line.</span></span>  
  
     <span data-ttu-id="ebdd3-114">![Stylets](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span><span class="sxs-lookup"><span data-stu-id="ebdd3-114">![Pens](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span></span>  
  
     <span data-ttu-id="ebdd3-115">L’exemple de code suivant dessine un rectangle à deux reprises : une fois avec un stylet noir d’une largeur de 1 et une fois avec un stylet vert d’une largeur de 10.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-115">The following code example draws a rectangle twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a><span data-ttu-id="ebdd3-116">Pour modifier l’alignement d’un stylet</span><span class="sxs-lookup"><span data-stu-id="ebdd3-116">To change the alignment of a pen</span></span>  
  
-   <span data-ttu-id="ebdd3-117">Définir la valeur de la <xref:System.Drawing.Pen.Alignment%2A> propriété <xref:System.Drawing.Drawing2D.PenAlignment.Center> pour spécifier que les pixels dessinés avec le stylet vert seront centrés sur la limite du rectangle.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-117">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> to specify that the pixels drawn with the green pen will be centered on the boundary of the rectangle.</span></span>  
  
     <span data-ttu-id="ebdd3-118">L’illustration suivante montre le rectangle résultant.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-118">The following illustration shows the resulting rectangle.</span></span>  
  
     <span data-ttu-id="ebdd3-119">![Stylets](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span><span class="sxs-lookup"><span data-stu-id="ebdd3-119">![Pens](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a><span data-ttu-id="ebdd3-120">Pour créer un stylet d’incrustation</span><span class="sxs-lookup"><span data-stu-id="ebdd3-120">To create an inset pen</span></span>  
  
-   <span data-ttu-id="ebdd3-121">Modifier l’alignement du stylet vert en modifiant la troisième instruction dans l’exemple de code précédent comme suit :</span><span class="sxs-lookup"><span data-stu-id="ebdd3-121">Change the green pen's alignment by modifying the third statement in the preceding code example as follows:</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     <span data-ttu-id="ebdd3-122">Les pixels de la ligne verte large apparaissent maintenant à l’intérieur du rectangle comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="ebdd3-122">Now the pixels in the wide green line appear on the inside of the rectangle as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="ebdd3-123">![Stylets](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span><span class="sxs-lookup"><span data-stu-id="ebdd3-123">![Pens](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebdd3-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebdd3-124">See Also</span></span>  
 [<span data-ttu-id="ebdd3-125">Utilisation d'un stylet pour dessiner des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="ebdd3-125">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="ebdd3-126">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ebdd3-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
