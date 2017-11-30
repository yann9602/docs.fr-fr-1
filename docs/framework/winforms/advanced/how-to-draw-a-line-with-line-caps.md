---
title: "Comment : dessiner une ligne avec des embouts de ligne"
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
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e2d5a5aba4a7634e0ea8480aa9744a5a7b9721d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line-with-line-caps"></a><span data-ttu-id="c1d54-102">Comment : dessiner une ligne avec des embouts de ligne</span><span class="sxs-lookup"><span data-stu-id="c1d54-102">How to: Draw a Line with Line Caps</span></span>
<span data-ttu-id="c1d54-103">Vous pouvez dessiner le début ou la fin d’une ligne dans une des différentes formes appelées des embouts de ligne.</span><span class="sxs-lookup"><span data-stu-id="c1d54-103">You can draw the start or end of a line in one of several shapes called line caps.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c1d54-104">prend en charge plusieurs embouts de ligne, telles que rond, carré, losange et pointe de flèche.</span><span class="sxs-lookup"><span data-stu-id="c1d54-104"> supports several line caps, such as round, square, diamond, and arrowhead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1d54-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="c1d54-105">Example</span></span>  
 <span data-ttu-id="c1d54-106">Vous pouvez spécifier des embouts de ligne pour le début d’une ligne (embout de début), à la fin d’une ligne (extrémité de fin) ou les tirets d’une ligne en pointillés (embout pointillé).</span><span class="sxs-lookup"><span data-stu-id="c1d54-106">You can specify line caps for the start of a line (start cap), the end of a line (end cap), or the dashes of a dashed line (dash cap).</span></span>  
  
 <span data-ttu-id="c1d54-107">L’exemple suivant dessine une ligne avec une pointe de flèche à une extrémité et une extrémité arrondie à l’autre extrémité.</span><span class="sxs-lookup"><span data-stu-id="c1d54-107">The following example draws a line with an arrowhead at one end and a round cap at the other end.</span></span> <span data-ttu-id="c1d54-108">L’illustration montre la ligne résultante :</span><span class="sxs-lookup"><span data-stu-id="c1d54-108">The illustration shows the resulting line:</span></span>  
  
 <span data-ttu-id="c1d54-109">![Stylets](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span><span class="sxs-lookup"><span data-stu-id="c1d54-109">![Pens](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1d54-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="c1d54-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="c1d54-111">Créer un Windows Form et gérer du formulaire <xref:System.Windows.Forms.Control.Paint> événement.</span><span class="sxs-lookup"><span data-stu-id="c1d54-111">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="c1d54-112">Collez l’exemple de code dans le <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements en passant `e` comme <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="c1d54-112">Paste the example code into the <xref:System.Windows.Forms.Control.Paint> event handler passing `e` as <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1d54-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1d54-113">See Also</span></span>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>  
 [<span data-ttu-id="c1d54-114">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c1d54-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="c1d54-115">Utilisation d'un stylet pour dessiner des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="c1d54-115">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
