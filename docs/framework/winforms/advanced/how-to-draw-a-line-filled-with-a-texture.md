---
title: "Comment : dessiner une ligne remplie d'une texture"
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
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 33374a16e6fee80dd45227acd4c5860d5bfc4545
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a><span data-ttu-id="1528b-102">Comment : dessiner une ligne remplie d'une texture</span><span class="sxs-lookup"><span data-stu-id="1528b-102">How to: Draw a Line Filled with a Texture</span></span>
<span data-ttu-id="1528b-103">Au lieu de dessin d’une ligne avec une couleur unie, vous pouvez dessiner une ligne avec une texture.</span><span class="sxs-lookup"><span data-stu-id="1528b-103">Instead of drawing a line with a solid color, you can draw a line with a texture.</span></span> <span data-ttu-id="1528b-104">Pour dessiner des lignes et des courbes avec une texture, créez un <xref:System.Drawing.TextureBrush> de l’objet et passer <xref:System.Drawing.TextureBrush> de l’objet à un <xref:System.Drawing.Pen.%23ctor%2A> constructeur.</span><span class="sxs-lookup"><span data-stu-id="1528b-104">To draw lines and curves with a texture, create a <xref:System.Drawing.TextureBrush> object, and pass that <xref:System.Drawing.TextureBrush> object to a <xref:System.Drawing.Pen.%23ctor%2A> constructor.</span></span> <span data-ttu-id="1528b-105">La bitmap associée au pinceau de la texture est utilisée pour remplir le plan (de façon invisible) avec, et lorsque le stylet dessine une ligne ou une courbe, le trait du stylet débouche sur certains pixels de la texture en mosaïque.</span><span class="sxs-lookup"><span data-stu-id="1528b-105">The bitmap associated with the texture brush is used to tile the plane (invisibly), and when the pen draws a line or curve, the stroke of the pen uncovers certain pixels of the tiled texture.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1528b-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="1528b-106">Example</span></span>  
 <span data-ttu-id="1528b-107">L’exemple suivant crée un <xref:System.Drawing.Bitmap> objet à partir du fichier `Texture1.jpg`.</span><span class="sxs-lookup"><span data-stu-id="1528b-107">The following example creates a <xref:System.Drawing.Bitmap> object from the file `Texture1.jpg`.</span></span> <span data-ttu-id="1528b-108">Cette bitmap est utilisée pour construire un <xref:System.Drawing.TextureBrush> objet et le <xref:System.Drawing.TextureBrush> objet est utilisé pour construire un <xref:System.Drawing.Pen> objet.</span><span class="sxs-lookup"><span data-stu-id="1528b-108">That bitmap is used to construct a <xref:System.Drawing.TextureBrush> object, and the <xref:System.Drawing.TextureBrush> object is used to construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="1528b-109">L’appel à <xref:System.Drawing.Graphics.DrawImage%2A> Dessine l’image bitmap avec son coin supérieur gauche à (0, 0).</span><span class="sxs-lookup"><span data-stu-id="1528b-109">The call to <xref:System.Drawing.Graphics.DrawImage%2A> draws the bitmap with its upper-left corner at (0, 0).</span></span> <span data-ttu-id="1528b-110">L’appel à <xref:System.Drawing.Graphics.DrawEllipse%2A> utilise le <xref:System.Drawing.Pen> objet pour dessiner une ellipse avec une texture.</span><span class="sxs-lookup"><span data-stu-id="1528b-110">The call to <xref:System.Drawing.Graphics.DrawEllipse%2A> uses the <xref:System.Drawing.Pen> object to draw a textured ellipse.</span></span>  
  
 <span data-ttu-id="1528b-111">L’illustration suivante montre l’image bitmap et l’ellipse avec une texture.</span><span class="sxs-lookup"><span data-stu-id="1528b-111">The following illustration shows the bitmap and the textured ellipse.</span></span>  
  
 <span data-ttu-id="1528b-112">![Stylets](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span><span class="sxs-lookup"><span data-stu-id="1528b-112">![Pens](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1528b-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="1528b-113">Compiling the Code</span></span>  
 <span data-ttu-id="1528b-114">Créer un Windows Form et gérer du formulaire <xref:System.Windows.Forms.Control.Paint> événement.</span><span class="sxs-lookup"><span data-stu-id="1528b-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="1528b-115">Collez le code précédent dans le <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="1528b-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="1528b-116">Remplacez `Texture.jpg` avec une image valide sur votre système.</span><span class="sxs-lookup"><span data-stu-id="1528b-116">Replace `Texture.jpg` with an image valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1528b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1528b-117">See Also</span></span>  
 [<span data-ttu-id="1528b-118">Utilisation d'un stylet pour dessiner des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="1528b-118">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="1528b-119">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1528b-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
