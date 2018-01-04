---
title: "Images, bitmaps et métafichiers"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metafiles [Windows Forms], about metafiles
- bitmaps [Windows Forms], about bitmaps
- images [Windows Forms], about images
- Windows Forms, images
ms.assetid: 7152b45b-a55c-49bc-8c78-ae002a844f71
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 67f72847e5dca20acd623c566a882e0094e94f68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="images-bitmaps-and-metafiles"></a><span data-ttu-id="bca27-102">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="bca27-102">Images, Bitmaps, and Metafiles</span></span>
<span data-ttu-id="bca27-103">La classe `Image` est une classe de base abstraite qui fournit des méthodes pour utiliser des images raster (bitmaps) et des images vectorielles (métafichiers).</span><span class="sxs-lookup"><span data-stu-id="bca27-103">The `Image` class is an abstract base class that provides methods for working with raster images (bitmaps) and vector images (metafiles).</span></span> <span data-ttu-id="bca27-104">La classe `Bitmap` et la classe <xref:System.Drawing.Imaging.Metafile> héritent toutes deux de la classe `Image`.</span><span class="sxs-lookup"><span data-stu-id="bca27-104">The `Bitmap` class and the <xref:System.Drawing.Imaging.Metafile> class both inherit from the `Image` class.</span></span> <span data-ttu-id="bca27-105">La classe `Bitmap` étend les fonctionnalités de la classe `Image` en fournissant des méthodes supplémentaires pour le chargement, l'enregistrement et la manipulation d'images raster.</span><span class="sxs-lookup"><span data-stu-id="bca27-105">The `Bitmap` class expands on the capabilities of the `Image` class by providing additional methods for loading, saving, and manipulating raster images.</span></span> <span data-ttu-id="bca27-106">La classe <xref:System.Drawing.Imaging.Metafile> étend les fonctionnalités de la classe `Image` en fournissant des méthodes supplémentaires pour l'enregistrement et l'examen d'images vectorielles.</span><span class="sxs-lookup"><span data-stu-id="bca27-106">The <xref:System.Drawing.Imaging.Metafile> class expands on the capabilities of the `Image` class by providing additional methods for recording and examining vector images.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bca27-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="bca27-107">In This Section</span></span>  
 [<span data-ttu-id="bca27-108">Types de bitmaps</span><span class="sxs-lookup"><span data-stu-id="bca27-108">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 <span data-ttu-id="bca27-109">Décrit les différents formats d'image.</span><span class="sxs-lookup"><span data-stu-id="bca27-109">Discusses the various image formats.</span></span>  
  
 [<span data-ttu-id="bca27-110">Métafichiers dans GDI+</span><span class="sxs-lookup"><span data-stu-id="bca27-110">Metafiles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/metafiles-in-gdi.md)  
 <span data-ttu-id="bca27-111">Traite de la prise en charge des métafichiers dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bca27-111">Discusses [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] support for metafiles.</span></span>  
  
 [<span data-ttu-id="bca27-112">Dessin, positionnement et clonage d'images dans GDI+</span><span class="sxs-lookup"><span data-stu-id="bca27-112">Drawing, Positioning, and Cloning Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/drawing-positioning-and-cloning-images-in-gdi.md)  
 <span data-ttu-id="bca27-113">Décrit les méthodes permettant de dessiner des images vectorielles et raster avec du code managé.</span><span class="sxs-lookup"><span data-stu-id="bca27-113">Discusses methods for drawing vector and raster images with managed code.</span></span>  
  
 [<span data-ttu-id="bca27-114">Rognage et mise à l'échelle d'images dans GDI+</span><span class="sxs-lookup"><span data-stu-id="bca27-114">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="bca27-115">Décrit les méthodes permettant de rogner et de mettre à l'échelle des images vectorielles et raster avec du code managé</span><span class="sxs-lookup"><span data-stu-id="bca27-115">Discusses methods for cropping and scaling vector and raster images with managed code</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bca27-116">Référence</span><span class="sxs-lookup"><span data-stu-id="bca27-116">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="bca27-117">Décrit cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="bca27-117">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="bca27-118">Décrit cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="bca27-118">Describes this class and has links to all of its members</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bca27-119">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="bca27-119">Related Sections</span></span>  
 [<span data-ttu-id="bca27-120">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="bca27-120">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)  
 <span data-ttu-id="bca27-121">Contient des liens vers des rubriques qui montrent comment utiliser des images dans votre application.</span><span class="sxs-lookup"><span data-stu-id="bca27-121">Contains links to topics that demonstrate how to use images in your application.</span></span>
