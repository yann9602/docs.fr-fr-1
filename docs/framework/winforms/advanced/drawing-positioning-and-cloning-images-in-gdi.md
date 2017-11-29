---
title: Dessin, positionnement et clonage d'images dans GDI+
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
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3ba716a36280d2ac08dae907abbdbe05e563dfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a><span data-ttu-id="981f3-102">Dessin, positionnement et clonage d'images dans GDI+</span><span class="sxs-lookup"><span data-stu-id="981f3-102">Drawing, Positioning, and Cloning Images in GDI+</span></span>
<span data-ttu-id="981f3-103">Vous pouvez utiliser la <xref:System.Drawing.Bitmap> classe pour charger et afficher des images raster et vous pouvez utiliser la <xref:System.Drawing.Imaging.Metafile> classe pour charger et afficher des images vectorielles.</span><span class="sxs-lookup"><span data-stu-id="981f3-103">You can use the <xref:System.Drawing.Bitmap> class to load and display raster images, and you can use the <xref:System.Drawing.Imaging.Metafile> class to load and display vector images.</span></span> <span data-ttu-id="981f3-104">Le <xref:System.Drawing.Bitmap> et <xref:System.Drawing.Imaging.Metafile> classes héritent de la <xref:System.Drawing.Image> classe.</span><span class="sxs-lookup"><span data-stu-id="981f3-104">The <xref:System.Drawing.Bitmap> and <xref:System.Drawing.Imaging.Metafile> classes inherit from the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="981f3-105">Pour afficher une image vectorielle, vous avez besoin d’une instance de la <xref:System.Drawing.Graphics> classe et un <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="981f3-105">To display a vector image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="981f3-106">Pour afficher une image raster, vous avez besoin d’une instance de la <xref:System.Drawing.Graphics> classe et un <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="981f3-106">To display a raster image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="981f3-107">L’instance de la <xref:System.Drawing.Graphics> classe fournit le <xref:System.Drawing.Graphics.DrawImage%2A> méthode qui reçoit le <xref:System.Drawing.Imaging.Metafile> ou <xref:System.Drawing.Bitmap> en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="981f3-107">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawImage%2A> method, which receives the <xref:System.Drawing.Imaging.Metafile> or <xref:System.Drawing.Bitmap> as an argument.</span></span>  
  
## <a name="file-types-and-cloning"></a><span data-ttu-id="981f3-108">Types de fichiers et de clonage</span><span class="sxs-lookup"><span data-stu-id="981f3-108">File Types and Cloning</span></span>  
 <span data-ttu-id="981f3-109">L’exemple de code suivant montre comment construire un <xref:System.Drawing.Bitmap> à partir du fichier Climber.jpg et affiche la bitmap.</span><span class="sxs-lookup"><span data-stu-id="981f3-109">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Climber.jpg and displays the bitmap.</span></span> <span data-ttu-id="981f3-110">Le point de destination pour l’angle supérieur gauche de l’image, (10, 10), est spécifié dans les deuxième et troisième paramètres.</span><span class="sxs-lookup"><span data-stu-id="981f3-110">The destination point for the upper-left corner of the image, (10, 10), is specified in the second and third parameters.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 <span data-ttu-id="981f3-111">L’illustration suivante montre l’image.</span><span class="sxs-lookup"><span data-stu-id="981f3-111">The following illustration shows the image.</span></span>  
  
 <span data-ttu-id="981f3-112">![Exemple d’image](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span><span class="sxs-lookup"><span data-stu-id="981f3-112">![Image Sample](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span></span>  
  
 <span data-ttu-id="981f3-113">Vous pouvez construire <xref:System.Drawing.Bitmap> objets à partir de graphiques différents formats de fichier : BMP, GIF, JPEG, EXIF, PNG, TIFF et icône.</span><span class="sxs-lookup"><span data-stu-id="981f3-113">You can construct <xref:System.Drawing.Bitmap> objects from a variety of graphics file formats: BMP, GIF, JPEG, EXIF, PNG, TIFF, and ICON.</span></span>  
  
 <span data-ttu-id="981f3-114">L’exemple de code suivant montre comment construire <xref:System.Drawing.Bitmap> objets à partir de divers types de fichier, puis affiche les bitmaps.</span><span class="sxs-lookup"><span data-stu-id="981f3-114">The following code example shows how to construct <xref:System.Drawing.Bitmap> objects from a variety of file types and then displays the bitmaps.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <span data-ttu-id="981f3-115">Le <xref:System.Drawing.Bitmap> classe fournit un <xref:System.Drawing.Bitmap.Clone%2A> méthode que vous pouvez utiliser pour effectuer une copie d’un objet <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="981f3-115">The <xref:System.Drawing.Bitmap> class provides a <xref:System.Drawing.Bitmap.Clone%2A> method that you can use to make a copy of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="981f3-116">Le <xref:System.Drawing.Bitmap.Clone%2A> méthode possède un paramètre du rectangle source que vous pouvez utiliser pour spécifier la partie de l’image bitmap d’origine que vous souhaitez copier.</span><span class="sxs-lookup"><span data-stu-id="981f3-116">The <xref:System.Drawing.Bitmap.Clone%2A> method has a source rectangle parameter that you can use to specify the portion of the original bitmap that you want to copy.</span></span> <span data-ttu-id="981f3-117">L’exemple de code suivant montre comment créer un <xref:System.Drawing.Bitmap> en clonant la moitié supérieure d’un objet <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="981f3-117">The following code example shows how to create a <xref:System.Drawing.Bitmap> by cloning the top half of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="981f3-118">Ensuite, les deux images sont dessinées.</span><span class="sxs-lookup"><span data-stu-id="981f3-118">Then both images are drawn.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 <span data-ttu-id="981f3-119">L’illustration suivante montre les deux images.</span><span class="sxs-lookup"><span data-stu-id="981f3-119">The following illustration shows the two images.</span></span>  
  
 <span data-ttu-id="981f3-120">![Rognage](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span><span class="sxs-lookup"><span data-stu-id="981f3-120">![Cropping](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="981f3-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="981f3-121">See Also</span></span>  
 [<span data-ttu-id="981f3-122">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="981f3-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="981f3-123">Guide pratique pour créer des objets graphiques pour le dessin</span><span class="sxs-lookup"><span data-stu-id="981f3-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="981f3-124">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="981f3-124">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
