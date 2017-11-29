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
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>Utilisation d'encodeurs et de décodeurs d'images dans GDI+ managé
Le <xref:System.Drawing> espace de noms fournit la <xref:System.Drawing.Image> et <xref:System.Drawing.Bitmap> classes pour le stockage et la manipulation d’images. À l’aide d’encodeurs d’image dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez écrire des images à partir de la mémoire sur le disque. À l’aide de décodeurs d’images dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez charger des images à partir du disque dans la mémoire. Un encodeur traduit les données dans un <xref:System.Drawing.Image> ou <xref:System.Drawing.Bitmap> objet dans un format de fichier de disque désigné. Un décodeur traduit les données dans un fichier de disque au format requis par le <xref:System.Drawing.Image> et <xref:System.Drawing.Bitmap> objets.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]a intégré encodeurs et décodeurs qui prennent en charge les types de fichiers suivants :  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]contient également des décodeurs intégrés qui prennent en charge les types de fichiers suivants :  
  
-   WMF  
  
-   EMF  
  
-   ICÔNE  
  
 Les rubriques suivantes abordent les encodeurs et décodeurs plus en détail :  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour répertorier les encodeurs installés](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 Décrit comment répertorier les encodeurs disponibles sur un ordinateur.  
  
 [Guide pratique pour répertorier les décodeurs installés](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 Décrit comment répertorier les décodeurs disponibles sur un ordinateur.  
  
 [Guide pratique pour déterminer les paramètres pris en charge par un encodeur](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 Décrit comment répertorier les <xref:System.Drawing.Imaging.EncoderParameters> pris en charge par un encodeur.  
  
 [Guide pratique pour convertir une image BMP en image PNG](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 Décrit comment enregistrer une image dans un format d’image différent.  
  
 [Guide pratique pour définir le niveau de compression JPEG](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 Décrit comment modifier le niveau de qualité d’une image.  
  
## <a name="reference"></a>Référence  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [À propos du code managé GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
