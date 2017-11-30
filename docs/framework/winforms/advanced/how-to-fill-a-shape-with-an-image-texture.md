---
title: "Comment : remplir une forme avec une texture d'image"
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
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c20562cade6917a3426fe04861a05c4b6b0bd543
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a><span data-ttu-id="3ade5-102">Comment : remplir une forme avec une texture d'image</span><span class="sxs-lookup"><span data-stu-id="3ade5-102">How to: Fill a Shape with an Image Texture</span></span>
<span data-ttu-id="3ade5-103">Vous pouvez remplir une forme fermée avec une texture à l’aide de la <xref:System.Drawing.Image> classe et la <xref:System.Drawing.TextureBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="3ade5-103">You can fill a closed shape with a texture by using the <xref:System.Drawing.Image> class and the <xref:System.Drawing.TextureBrush> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ade5-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="3ade5-104">Example</span></span>  
 <span data-ttu-id="3ade5-105">L’exemple suivant remplit une ellipse avec une image.</span><span class="sxs-lookup"><span data-stu-id="3ade5-105">The following example fills an ellipse with an image.</span></span> <span data-ttu-id="3ade5-106">Le code construit une <xref:System.Drawing.Image> de l’objet et transmet ensuite l’adresse de cet <xref:System.Drawing.Image> objet en tant qu’argument à une <xref:System.Drawing.TextureBrush.%23ctor%2A> constructeur.</span><span class="sxs-lookup"><span data-stu-id="3ade5-106">The code constructs an <xref:System.Drawing.Image> object, and then passes the address of that <xref:System.Drawing.Image> object as an argument to a <xref:System.Drawing.TextureBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="3ade5-107">La troisième instruction met l’image à l’échelle et la quatrième remplit l’ellipse avec des copies répétées de l’image à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="3ade5-107">The third statement scales the image, and the fourth statement fills the ellipse with repeated copies of the scaled image.</span></span>  
  
 <span data-ttu-id="3ade5-108">Dans le code suivant, le <xref:System.Drawing.TextureBrush.Transform%2A> propriété contient la transformation qui est appliquée à l’image avant qu’elle est dessinée.</span><span class="sxs-lookup"><span data-stu-id="3ade5-108">In the following code, the <xref:System.Drawing.TextureBrush.Transform%2A> property contains the transformation that is applied to the image before it is drawn.</span></span> <span data-ttu-id="3ade5-109">Supposez que l’image d’origine a une largeur de 640 pixels et une hauteur de 480 pixels.</span><span class="sxs-lookup"><span data-stu-id="3ade5-109">Assume that the original image has a width of 640 pixels and a height of 480 pixels.</span></span> <span data-ttu-id="3ade5-110">La transformation réduit l’image à 75 × 75 en définissant les valeurs de mise à l’échelle horizontales et verticales.</span><span class="sxs-lookup"><span data-stu-id="3ade5-110">The transform shrinks the image to 75×75 by setting the horizontal and vertical scaling values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ade5-111">Dans l’exemple suivant, la taille de l’image est 75 × 75 et la taille de l’ellipse est 150 × 250.</span><span class="sxs-lookup"><span data-stu-id="3ade5-111">In the following example, the image size is 75×75, and the ellipse size is 150×250.</span></span> <span data-ttu-id="3ade5-112">Étant donné que l’image est plus petite que l’ellipse qu’elle remplit, l’ellipse est affichée en mosaïque avec l’image.</span><span class="sxs-lookup"><span data-stu-id="3ade5-112">Because the image is smaller than the ellipse it is filling, the ellipse is tiled with the image.</span></span> <span data-ttu-id="3ade5-113">Signifie que l’image est répétée horizontalement et verticalement jusqu'à ce que la limite de la forme de mosaïque est atteinte.</span><span class="sxs-lookup"><span data-stu-id="3ade5-113">Tiling means that the image is repeated horizontally and vertically until the boundary of the shape is reached.</span></span> <span data-ttu-id="3ade5-114">Pour plus d’informations sur la mosaïque, consultez [Comment : remplir une forme avec une Image](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).</span><span class="sxs-lookup"><span data-stu-id="3ade5-114">For more information about tiling, see [How to: Tile a Shape with an Image](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3ade5-115">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3ade5-115">Compiling the Code</span></span>  
 <span data-ttu-id="3ade5-116">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="3ade5-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ade5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ade5-117">See Also</span></span>  
 [<span data-ttu-id="3ade5-118">Utilisation d'un pinceau pour remplir des formes</span><span class="sxs-lookup"><span data-stu-id="3ade5-118">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
