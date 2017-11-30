---
title: "Comment : améliorer les performances en évitant la mise à l'échelle automatique"
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
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0130e0745dfca20da5dc723bb7cc84748bb0b148
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a><span data-ttu-id="fbbc4-102">Comment : améliorer les performances en évitant la mise à l'échelle automatique</span><span class="sxs-lookup"><span data-stu-id="fbbc4-102">How to: Improve Performance by Avoiding Automatic Scaling</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="fbbc4-103">peut automatiquement mettre à l’échelle une image que vous la dessinez, ce qui diminue les performances.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-103"> may automatically scale an image as you draw it, which would decrease performance.</span></span> <span data-ttu-id="fbbc4-104">Ou bien, vous pouvez contrôler la mise à l’échelle de l’image en passant les dimensions du rectangle de destination à le <xref:System.Drawing.Graphics.DrawImage%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="fbbc4-104">Alternatively, you can control the scaling of the image by passing the dimensions of the destination rectangle to the <xref:System.Drawing.Graphics.DrawImage%2A> method.</span></span>  
  
 <span data-ttu-id="fbbc4-105">Par exemple, l’appel suivant à la <xref:System.Drawing.Graphics.DrawImage%2A> méthode spécifie un coin supérieur gauche de (50, 30) mais ne spécifie ne pas un rectangle de destination.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-105">For example, the following call to the <xref:System.Drawing.Graphics.DrawImage%2A> method specifies an upper-left corner of (50, 30) but does not specify a destination rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 <span data-ttu-id="fbbc4-106">Bien que ce soit la version la plus simple de la <xref:System.Drawing.Graphics.DrawImage%2A> méthode en termes de nombre d’arguments requis, il n’est pas nécessairement la plus efficace.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-106">Although this is the easiest version of the <xref:System.Drawing.Graphics.DrawImage%2A> method in terms of the number of required arguments, it is not necessarily the most efficient.</span></span> <span data-ttu-id="fbbc4-107">Si la résolution utilisée par [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (habituellement 96 points par pouce) est différente de la résolution stockée dans le <xref:System.Drawing.Image> objet, puis le <xref:System.Drawing.Graphics.DrawImage%2A> méthode mettra à l’échelle l’image.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-107">If the resolution used by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (usually 96 dots per inch) is different from the resolution stored in the <xref:System.Drawing.Image> object, then the <xref:System.Drawing.Graphics.DrawImage%2A> method will scale the image.</span></span> <span data-ttu-id="fbbc4-108">Par exemple, un <xref:System.Drawing.Image> objet a une largeur de 216 pixels et une valeur de résolution horizontale stockée de 72 points par pouce.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-108">For example, suppose an <xref:System.Drawing.Image> object has a width of 216 pixels and a stored horizontal resolution value of 72 dots per inch.</span></span> <span data-ttu-id="fbbc4-109">Comme 216/72 est 3, <xref:System.Drawing.Graphics.DrawImage%2A> l’échelle l’image afin qu’elle a une largeur de 3 pouces à une résolution de 96 points par pouce.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-109">Because 216/72 is 3, <xref:System.Drawing.Graphics.DrawImage%2A> will scale the image so that it has a width of 3 inches at a resolution of 96 dots per inch.</span></span> <span data-ttu-id="fbbc4-110">Autrement dit, <xref:System.Drawing.Graphics.DrawImage%2A> affiche une image qui a une largeur de 96 x 3 = 288 pixels.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-110">That is, <xref:System.Drawing.Graphics.DrawImage%2A> will display an image that has a width of 96x3 = 288 pixels.</span></span>  
  
 <span data-ttu-id="fbbc4-111">Même si la résolution d’écran est différente de 96 points par pouce, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sera probablement l’échelle l’image comme si la résolution d’écran était de 96 points par pouce.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-111">Even if your screen resolution is different from 96 dots per inch, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] will probably scale the image as if the screen resolution were 96 dots per inch.</span></span> <span data-ttu-id="fbbc4-112">C’est parce qu’un [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> objet est associé à un contexte de périphérique et à quel moment [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] requêtes le contexte de périphérique pour la résolution d’écran, le résultat est habituellement 96, quelle que soit la résolution réelle de l’écran.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-112">That is because a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> object is associated with a device context, and when [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] queries the device context for the screen resolution, the result is usually 96, regardless of the actual screen resolution.</span></span> <span data-ttu-id="fbbc4-113">Vous pouvez éviter la mise à l’échelle automatique en spécifiant le rectangle de destination dans le <xref:System.Drawing.Graphics.DrawImage%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="fbbc4-113">You can avoid automatic scaling by specifying the destination rectangle in the <xref:System.Drawing.Graphics.DrawImage%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbbc4-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="fbbc4-114">Example</span></span>  
 <span data-ttu-id="fbbc4-115">L’exemple suivant dessine l’image même à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-115">The following example draws the same image twice.</span></span> <span data-ttu-id="fbbc4-116">Dans le premier cas, la largeur et la hauteur du rectangle de destination ne sont pas spécifiés, et l’image est ajustée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-116">In the first case, the width and height of the destination rectangle are not specified, and the image is automatically scaled.</span></span> <span data-ttu-id="fbbc4-117">Dans le second cas, la largeur et la hauteur (exprimée en pixels) du rectangle de destination sont spécifiés pour être le même que la largeur et la hauteur de l’image d’origine.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-117">In the second case, the width and height (measured in pixels) of the destination rectangle are specified to be the same as the width and height of the original image.</span></span> <span data-ttu-id="fbbc4-118">L’illustration suivante montre l’image rendue deux fois.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-118">The following illustration shows the image rendered twice.</span></span>  
  
 <span data-ttu-id="fbbc4-119">![Mise à l’échelle de Texture](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")</span><span class="sxs-lookup"><span data-stu-id="fbbc4-119">![Scaled Texture](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fbbc4-120">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="fbbc4-120">Compiling the Code</span></span>  
 <span data-ttu-id="fbbc4-121">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-121">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="fbbc4-122">Remplacez Texture.jpg avec un nom de l’image et le chemin d’accès valides sur votre système.</span><span class="sxs-lookup"><span data-stu-id="fbbc4-122">Replace Texture.jpg with an image name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbbc4-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbbc4-123">See Also</span></span>  
 [<span data-ttu-id="fbbc4-124">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="fbbc4-124">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="fbbc4-125">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="fbbc4-125">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
