---
title: "Utilisation d&#39;encodeurs et de d&#233;codeurs d&#39;images dans GDI+ manag&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "décodeurs d'image, utilisation"
  - "encodeurs d'image, utilisation"
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Utilisation d&#39;encodeurs et de d&#233;codeurs d&#39;images dans GDI+ manag&#233;
L'espace de noms <xref:System.Drawing> fournit les classes <xref:System.Drawing.Image> et <xref:System.Drawing.Bitmap> pour stocker et manipuler des images.  Les encodeurs d'images de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] vous permettent d'écrire des images de la mémoire vers le disque. Les décodeurs d'images de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] vous permettent de charger des images du disque vers la mémoire.  Un encodeur traduit les données dans un objet <xref:System.Drawing.Image> ou <xref:System.Drawing.Bitmap> dans un format de fichier sur disque désigné.  Un décodeur traduit les données dans un fichier sur disque au format requis par les objets <xref:System.Drawing.Image> et <xref:System.Drawing.Bitmap>.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] contient des encodeurs et des décodeurs intégrés qui prennent en charge les types de fichiers suivants :  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] contient également des décodeurs intégrés qui prennent en charge les types de fichiers suivants :  
  
-   WMF  
  
-   EMF  
  
-   ICÔNE  
  
 Les rubriques suivantes présentent en détail les encodeurs et les décodeurs :  
  
## Dans cette section  
 [Comment : répertorier les encodeurs installés](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 Décrit comment répertorier les encodeurs disponibles sur un ordinateur.  
  
 [Comment : répertorier les décodeurs installés](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 Décrit comment répertorier les décodeurs disponibles sur un ordinateur.  
  
 [Comment : déterminer les paramètres pris en charge par un encodeur](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 Décrit comment répertorier le <xref:System.Drawing.Imaging.EncoderParameters> pris en charge par un encodeur.  
  
 [Comment : convertir une image BMP en image PNG](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 Décrit comment enregistrer une image dans un format d'image différent.  
  
 [Comment : définir le niveau de compression JPEG](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 Décrit comment modifier le niveau de qualité d'une image.  
  
## Référence  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## Rubriques connexes  
 [À propos du code managé GDI\+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)