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
ms.workload: dotnet
ms.openlocfilehash: 0bbe7ac4b8c541ea76392f94f538e41816cf5c3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cropping-and-scaling-images-in-gdi"></a>Rognage et mise à l'échelle d'images dans GDI+
Vous pouvez utiliser la <xref:System.Drawing.Graphics.DrawImage%2A> méthode de la <xref:System.Drawing.Graphics> classe pour dessiner et positionner des images vectorielles et des images raster. <xref:System.Drawing.Graphics.DrawImage%2A>est une méthode surchargée, il existe plusieurs façons, vous pouvez lui fournir avec des arguments.  
  
## <a name="drawimage-variations"></a>DrawImage Variations  
 Une variante de la <xref:System.Drawing.Graphics.DrawImage%2A> méthode reçoit un <xref:System.Drawing.Bitmap> et un <xref:System.Drawing.Rectangle>. Le rectangle spécifie la destination de l’opération de dessin ; Autrement dit, il spécifie le rectangle dans lequel dessiner l’image. Si la taille du rectangle de destination est différente de la taille de l’image d’origine, l’image est ajustée en fonction du rectangle de destination. L’exemple de code suivant montre comment dessiner des trois fois la même image : aucune mise à l’échelle, avec une expansion et avec une compression :  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 L’illustration suivante montre les trois images.  
  
 ![Mise à l’échelle](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 Des variantes de la <xref:System.Drawing.Graphics.DrawImage%2A> méthode ont un paramètre du rectangle source comme un rectangle de destination. Le paramètre du rectangle source Spécifie la partie de l’image d’origine à dessiner. Le rectangle de destination Spécifie le rectangle dans lequel dessiner la partie de l’image. Si la taille du rectangle de destination est différente de la taille du rectangle source, l’image est redimensionnée pour remplir le rectangle de destination.  
  
 L’exemple de code suivant montre comment construire un <xref:System.Drawing.Bitmap> à partir du fichier Runner.jpg. L’image entière est dessiné avec aucune mise à l’échelle à (0, 0). Ensuite, une petite partie de l’image est dessinée à deux reprises : une fois avec une compression et une fois avec une expansion.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 L’illustration suivante montre l’image non ajustée et les parties de l’image réduite et agrandie.  
  
 ![Rognage et mise à l’échelle](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
