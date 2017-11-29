---
title: "Comment : utiliser le mode d'interpolation pour contrôler la qualité d'image pendant la mise à l'échelle"
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
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10a0ef4e7fd8514245a7659dd515d8f363a716ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a>Comment : utiliser le mode d'interpolation pour contrôler la qualité d'image pendant la mise à l'échelle
Le mode d’interpolation d’un <xref:System.Drawing.Graphics> objet influence la façon dont [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dimensionne (étire et réduit) les images. Le <xref:System.Drawing.Drawing2D.InterpolationMode> énumération définit plusieurs modes d’interpolation, certains d'entre eux sont affichés dans la liste suivante :  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 Pour étendre une image, chaque pixel de l’image d’origine doit être mappé à un groupe de pixels de l’image plus grande. Pour réduire une image, groupes de pixels dans l’image d’origine doivent être mappés à pixels individuels dans l’image plus petite. L’efficacité des algorithmes qui effectuent ces mappages détermine la qualité d’une image à l’échelle. Les algorithmes qui produisent des images à l’échelle de qualité supérieure ont tendance à nécessiter plus de temps de traitement. Dans la liste précédente, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> est le mode de qualité et <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> est le mode de qualité optimale.  
  
 Pour définir le mode d’interpolation, assignez un des membres de la <xref:System.Drawing.Drawing2D.InterpolationMode> énumération à la <xref:System.Drawing.Graphics.InterpolationMode%2A> propriété d’un <xref:System.Drawing.Graphics> objet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant dessine une image et puis réduit l’image avec trois modes d’interpolation différent.  
  
 L’illustration suivante montre l’image d’origine et les trois images plus petites.  
  
 ![Image avec paramètres d’Interpolation variés](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
