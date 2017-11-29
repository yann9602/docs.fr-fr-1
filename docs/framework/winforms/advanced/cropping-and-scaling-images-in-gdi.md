---
title: "Rognage et mise à l'échelle d'images dans GDI+"
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
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63e1e55e57d586cbbca87361b95c18f0f53b8c75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cropping-and-scaling-images-in-gdi"></a><span data-ttu-id="923a3-102">Rognage et mise à l'échelle d'images dans GDI+</span><span class="sxs-lookup"><span data-stu-id="923a3-102">Cropping and Scaling Images in GDI+</span></span>
<span data-ttu-id="923a3-103">Vous pouvez utiliser la <xref:System.Drawing.Graphics.DrawImage%2A> méthode de la <xref:System.Drawing.Graphics> classe pour dessiner et positionner des images vectorielles et des images raster.</span><span class="sxs-lookup"><span data-stu-id="923a3-103">You can use the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> class to draw and position vector images and raster images.</span></span> <span data-ttu-id="923a3-104"><xref:System.Drawing.Graphics.DrawImage%2A>est une méthode surchargée, il existe plusieurs façons, vous pouvez lui fournir avec des arguments.</span><span class="sxs-lookup"><span data-stu-id="923a3-104"><xref:System.Drawing.Graphics.DrawImage%2A> is an overloaded method, so there are several ways you can supply it with arguments.</span></span>  
  
## <a name="drawimage-variations"></a><span data-ttu-id="923a3-105">DrawImage Variations</span><span class="sxs-lookup"><span data-stu-id="923a3-105">DrawImage Variations</span></span>  
 <span data-ttu-id="923a3-106">Une variante de la <xref:System.Drawing.Graphics.DrawImage%2A> méthode reçoit un <xref:System.Drawing.Bitmap> et un <xref:System.Drawing.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="923a3-106">One variation of the <xref:System.Drawing.Graphics.DrawImage%2A> method receives a <xref:System.Drawing.Bitmap> and a <xref:System.Drawing.Rectangle>.</span></span> <span data-ttu-id="923a3-107">Le rectangle spécifie la destination de l’opération de dessin ; Autrement dit, il spécifie le rectangle dans lequel dessiner l’image.</span><span class="sxs-lookup"><span data-stu-id="923a3-107">The rectangle specifies the destination for the drawing operation; that is, it specifies the rectangle in which to draw the image.</span></span> <span data-ttu-id="923a3-108">Si la taille du rectangle de destination est différente de la taille de l’image d’origine, l’image est ajustée en fonction du rectangle de destination.</span><span class="sxs-lookup"><span data-stu-id="923a3-108">If the size of the destination rectangle is different from the size of the original image, the image is scaled to fit the destination rectangle.</span></span> <span data-ttu-id="923a3-109">L’exemple de code suivant montre comment dessiner des trois fois la même image : aucune mise à l’échelle, avec une expansion et avec une compression :</span><span class="sxs-lookup"><span data-stu-id="923a3-109">The following code example shows how to draw the same image three times: once with no scaling, once with an expansion, and once with a compression:</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 <span data-ttu-id="923a3-110">L’illustration suivante montre les trois images.</span><span class="sxs-lookup"><span data-stu-id="923a3-110">The following illustration shows the three pictures.</span></span>  
  
 <span data-ttu-id="923a3-111">![Mise à l’échelle](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span><span class="sxs-lookup"><span data-stu-id="923a3-111">![Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span></span>  
  
 <span data-ttu-id="923a3-112">Des variantes de la <xref:System.Drawing.Graphics.DrawImage%2A> méthode ont un paramètre du rectangle source comme un rectangle de destination.</span><span class="sxs-lookup"><span data-stu-id="923a3-112">Some variations of the <xref:System.Drawing.Graphics.DrawImage%2A> method have a source-rectangle parameter as well as a destination-rectangle parameter.</span></span> <span data-ttu-id="923a3-113">Le paramètre du rectangle source Spécifie la partie de l’image d’origine à dessiner.</span><span class="sxs-lookup"><span data-stu-id="923a3-113">The source-rectangle parameter specifies the portion of the original image to draw.</span></span> <span data-ttu-id="923a3-114">Le rectangle de destination Spécifie le rectangle dans lequel dessiner la partie de l’image.</span><span class="sxs-lookup"><span data-stu-id="923a3-114">The destination rectangle specifies the rectangle in which to draw that portion of the image.</span></span> <span data-ttu-id="923a3-115">Si la taille du rectangle de destination est différente de la taille du rectangle source, l’image est redimensionnée pour remplir le rectangle de destination.</span><span class="sxs-lookup"><span data-stu-id="923a3-115">If the size of the destination rectangle is different from the size of the source rectangle, the picture is scaled to fit the destination rectangle.</span></span>  
  
 <span data-ttu-id="923a3-116">L’exemple de code suivant montre comment construire un <xref:System.Drawing.Bitmap> à partir du fichier Runner.jpg.</span><span class="sxs-lookup"><span data-stu-id="923a3-116">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Runner.jpg.</span></span> <span data-ttu-id="923a3-117">L’image entière est dessiné avec aucune mise à l’échelle à (0, 0).</span><span class="sxs-lookup"><span data-stu-id="923a3-117">The entire image is drawn with no scaling at (0, 0).</span></span> <span data-ttu-id="923a3-118">Ensuite, une petite partie de l’image est dessinée à deux reprises : une fois avec une compression et une fois avec une expansion.</span><span class="sxs-lookup"><span data-stu-id="923a3-118">Then a small portion of the image is drawn twice: once with a compression and once with an expansion.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 <span data-ttu-id="923a3-119">L’illustration suivante montre l’image non ajustée et les parties de l’image réduite et agrandie.</span><span class="sxs-lookup"><span data-stu-id="923a3-119">The following illustration shows the unscaled image, and the compressed and expanded image portions.</span></span>  
  
 <span data-ttu-id="923a3-120">![Rognage et mise à l’échelle](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span><span class="sxs-lookup"><span data-stu-id="923a3-120">![Cropping and Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="923a3-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="923a3-121">See Also</span></span>  
 [<span data-ttu-id="923a3-122">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="923a3-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="923a3-123">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="923a3-123">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
