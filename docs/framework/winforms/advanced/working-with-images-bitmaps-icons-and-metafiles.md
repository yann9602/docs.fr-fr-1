---
title: "Utilisation des images, bitmaps, icônes et métafichiers"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metafiles [Windows Forms], working with
- examples [Windows Forms], bitmaps
- examples [Windows Forms], images
- bitmaps [Windows Forms], working with
- images [Windows Forms], working with
- examples [Windows Forms], metafiles
ms.assetid: a626d701-bd99-4fd8-b92f-7b8f794e042b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53dc25d6a23c5cdbba1c640905eadbdc6b1acb71
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="79230-102">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="79230-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="79230-103"> fournit la classe `Bitmap` pour utiliser des images raster et la classe `Metafile` pour utiliser des images vectorielles.</span><span class="sxs-lookup"><span data-stu-id="79230-103"> provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="79230-104">Les classes `Bitmap` et `Metafile` héritent toutes deux de la classe `Image`.</span><span class="sxs-lookup"><span data-stu-id="79230-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79230-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="79230-105">In This Section</span></span>  
 [<span data-ttu-id="79230-106">Guide pratique pour dessiner une bitmap existante à l'écran</span><span class="sxs-lookup"><span data-stu-id="79230-106">How to: Draw an Existing Bitmap to the Screen</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="79230-107">Décrit comment charger et dessiner des bitmaps.</span><span class="sxs-lookup"><span data-stu-id="79230-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="79230-108">Guide pratique pour charger et afficher des métafichiers</span><span class="sxs-lookup"><span data-stu-id="79230-108">How to: Load and Display Metafiles</span></span>](../../../../docs/framework/winforms/advanced/how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="79230-109">Montre comment charger et dessiner des métafichiers.</span><span class="sxs-lookup"><span data-stu-id="79230-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="79230-110">Rognage et mise à l'échelle d'images dans GDI+</span><span class="sxs-lookup"><span data-stu-id="79230-110">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="79230-111">Explique comment rogner et mettre à l'échelle des images raster et vectorielles.</span><span class="sxs-lookup"><span data-stu-id="79230-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="79230-112">Guide pratique pour faire pivoter, refléter et incliner des images</span><span class="sxs-lookup"><span data-stu-id="79230-112">How to: Rotate, Reflect, and Skew Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="79230-113">Décrit comment dessiner des images pivotées, reflétées et inclinées.</span><span class="sxs-lookup"><span data-stu-id="79230-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="79230-114">Guide pratique pour utiliser le mode d'interpolation pour contrôler la qualité d'image pendant la mise à l'échelle</span><span class="sxs-lookup"><span data-stu-id="79230-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="79230-115">Montre comment utiliser l'énumération <xref:System.Drawing.Drawing2D.InterpolationMode> pour modifier la qualité d'image.</span><span class="sxs-lookup"><span data-stu-id="79230-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="79230-116">Guide pratique pour créer des images miniatures</span><span class="sxs-lookup"><span data-stu-id="79230-116">How to: Create Thumbnail Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-thumbnail-images.md)  
 <span data-ttu-id="79230-117">Décrit comment créer des images miniatures.</span><span class="sxs-lookup"><span data-stu-id="79230-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="79230-118">Guide pratique pour améliorer les performances en évitant la mise à l’échelle automatique</span><span class="sxs-lookup"><span data-stu-id="79230-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="79230-119">Explique comment dessiner une image sans mise à l'échelle automatique.</span><span class="sxs-lookup"><span data-stu-id="79230-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="79230-120">Guide pratique pour lire des métadonnées d'image</span><span class="sxs-lookup"><span data-stu-id="79230-120">How to: Read Image Metadata</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-image-metadata.md)  
 <span data-ttu-id="79230-121">Décrit comment lire des métadonnées à partir d'une image.</span><span class="sxs-lookup"><span data-stu-id="79230-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="79230-122">Guide pratique pour créer une bitmap au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="79230-122">How to: Create a Bitmap at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="79230-123">Montre comment dessiner une bitmap au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="79230-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="79230-124">Guide pratique pour extraire l'icône associée à un fichier dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="79230-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="79230-125">Décrit comment extraire une icône qui est une ressource incorporée d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="79230-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="79230-126">Référence</span><span class="sxs-lookup"><span data-stu-id="79230-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="79230-127">Décrit cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="79230-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="79230-128">Décrit cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="79230-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="79230-129">Décrit cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="79230-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="79230-130">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="79230-130">Related Sections</span></span>  
 [<span data-ttu-id="79230-131">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="79230-131">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="79230-132">Contient des liens vers des rubriques qui traitent des différents types de bitmaps et de leur manipulation dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="79230-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
