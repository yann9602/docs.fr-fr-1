---
title: "Utilisation d'encodeurs et de décodeurs d'images dans GDI+ managé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64384e3c283b6596e36d5b2bd583a304faf080b4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="cecb2-102">Utilisation d'encodeurs et de décodeurs d'images dans GDI+ managé</span><span class="sxs-lookup"><span data-stu-id="cecb2-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="cecb2-103">Le <xref:System.Drawing> espace de noms fournit la <xref:System.Drawing.Image> et <xref:System.Drawing.Bitmap> classes pour le stockage et la manipulation d’images.</span><span class="sxs-lookup"><span data-stu-id="cecb2-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="cecb2-104">À l’aide d’encodeurs d’image dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez écrire des images à partir de la mémoire sur le disque.</span><span class="sxs-lookup"><span data-stu-id="cecb2-104">By using image encoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can write images from memory to disk.</span></span> <span data-ttu-id="cecb2-105">À l’aide de décodeurs d’images dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez charger des images à partir du disque dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="cecb2-105">By using image decoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can load images from disk into memory.</span></span> <span data-ttu-id="cecb2-106">Un encodeur traduit les données dans un <xref:System.Drawing.Image> ou <xref:System.Drawing.Bitmap> objet dans un format de fichier de disque désigné.</span><span class="sxs-lookup"><span data-stu-id="cecb2-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="cecb2-107">Un décodeur traduit les données dans un fichier de disque au format requis par le <xref:System.Drawing.Image> et <xref:System.Drawing.Bitmap> objets.</span><span class="sxs-lookup"><span data-stu-id="cecb2-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="cecb2-108">a intégré encodeurs et décodeurs qui prennent en charge les types de fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="cecb2-108"> has built-in encoders and decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="cecb2-109">BMP</span><span class="sxs-lookup"><span data-stu-id="cecb2-109">BMP</span></span>  
  
-   <span data-ttu-id="cecb2-110">GIF</span><span class="sxs-lookup"><span data-stu-id="cecb2-110">GIF</span></span>  
  
-   <span data-ttu-id="cecb2-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="cecb2-111">JPEG</span></span>  
  
-   <span data-ttu-id="cecb2-112">PNG</span><span class="sxs-lookup"><span data-stu-id="cecb2-112">PNG</span></span>  
  
-   <span data-ttu-id="cecb2-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="cecb2-113">TIFF</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="cecb2-114">contient également des décodeurs intégrés qui prennent en charge les types de fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="cecb2-114"> also has built-in decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="cecb2-115">WMF</span><span class="sxs-lookup"><span data-stu-id="cecb2-115">WMF</span></span>  
  
-   <span data-ttu-id="cecb2-116">EMF</span><span class="sxs-lookup"><span data-stu-id="cecb2-116">EMF</span></span>  
  
-   <span data-ttu-id="cecb2-117">ICÔNE</span><span class="sxs-lookup"><span data-stu-id="cecb2-117">ICON</span></span>  
  
 <span data-ttu-id="cecb2-118">Les rubriques suivantes abordent les encodeurs et décodeurs plus en détail :</span><span class="sxs-lookup"><span data-stu-id="cecb2-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cecb2-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="cecb2-119">In This Section</span></span>  
 [<span data-ttu-id="cecb2-120">Guide pratique pour répertorier les encodeurs installés</span><span class="sxs-lookup"><span data-stu-id="cecb2-120">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 <span data-ttu-id="cecb2-121">Décrit comment répertorier les encodeurs disponibles sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cecb2-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="cecb2-122">Guide pratique pour répertorier les décodeurs installés</span><span class="sxs-lookup"><span data-stu-id="cecb2-122">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 <span data-ttu-id="cecb2-123">Décrit comment répertorier les décodeurs disponibles sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cecb2-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="cecb2-124">Guide pratique pour déterminer les paramètres pris en charge par un encodeur</span><span class="sxs-lookup"><span data-stu-id="cecb2-124">How to: Determine the Parameters Supported by an Encoder</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="cecb2-125">Décrit comment répertorier les <xref:System.Drawing.Imaging.EncoderParameters> pris en charge par un encodeur.</span><span class="sxs-lookup"><span data-stu-id="cecb2-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="cecb2-126">Guide pratique pour convertir une image BMP en image PNG</span><span class="sxs-lookup"><span data-stu-id="cecb2-126">How to: Convert a BMP image to a PNG image</span></span>](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="cecb2-127">Décrit comment enregistrer une image dans un format d’image différent.</span><span class="sxs-lookup"><span data-stu-id="cecb2-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="cecb2-128">Guide pratique pour définir le niveau de compression JPEG</span><span class="sxs-lookup"><span data-stu-id="cecb2-128">How to: Set JPEG Compression Level</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="cecb2-129">Décrit comment modifier le niveau de qualité d’une image.</span><span class="sxs-lookup"><span data-stu-id="cecb2-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cecb2-130">Référence</span><span class="sxs-lookup"><span data-stu-id="cecb2-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="cecb2-131">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="cecb2-131">Related Sections</span></span>  
 [<span data-ttu-id="cecb2-132">À propos du code managé GDI+</span><span class="sxs-lookup"><span data-stu-id="cecb2-132">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [<span data-ttu-id="cecb2-133">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="cecb2-133">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
