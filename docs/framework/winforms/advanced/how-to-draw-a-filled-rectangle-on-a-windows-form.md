---
title: "Comment : dessiner un rectangle rempli dans un Windows Form"
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
- cpp
f1_keywords: Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dce1a8d1070ed1d016da0c94c1f3ecc1ed9df389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="fb4d3-102">Comment : dessiner un rectangle rempli dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="fb4d3-102">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="fb4d3-103">Cet exemple dessine un rectangle rempli dans un formulaire.</span><span class="sxs-lookup"><span data-stu-id="fb4d3-103">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb4d3-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="fb4d3-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fb4d3-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="fb4d3-105">Compiling the Code</span></span>  
 <span data-ttu-id="fb4d3-106">Vous ne pouvez pas appeler cette méthode le <xref:System.Windows.Forms.Form.Load> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="fb4d3-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="fb4d3-107">Le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou masqué par une autre forme.</span><span class="sxs-lookup"><span data-stu-id="fb4d3-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="fb4d3-108">Pour que votre contenu soit automatiquement repeint, vous devez substituer la <xref:System.Windows.Forms.Control.OnPaint%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="fb4d3-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fb4d3-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="fb4d3-109">Robust Programming</span></span>  
 <span data-ttu-id="fb4d3-110">Vous devez toujours appeler <xref:System.IDisposable.Dispose%2A> sur tous les objets qui consomment des ressources système, telles que <xref:System.Drawing.Brush> et <xref:System.Drawing.Graphics> objets.</span><span class="sxs-lookup"><span data-stu-id="fb4d3-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb4d3-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb4d3-111">See Also</span></span>  
 <xref:System.Drawing.Graphics.FillRectangle%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="fb4d3-112">Mise en route de la programmation graphique</span><span class="sxs-lookup"><span data-stu-id="fb4d3-112">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="fb4d3-113">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb4d3-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="fb4d3-114">Utilisation d'un stylet pour dessiner des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="fb4d3-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="fb4d3-115">Pinceaux et remplissage de formes dans GDI+</span><span class="sxs-lookup"><span data-stu-id="fb4d3-115">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)
