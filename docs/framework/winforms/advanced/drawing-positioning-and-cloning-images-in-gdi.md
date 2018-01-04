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
ms.workload: dotnet
ms.openlocfilehash: bbff4023a51687539472ac3e040b125f2f92fc28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>Dessin, positionnement et clonage d'images dans GDI+
Vous pouvez utiliser la <xref:System.Drawing.Bitmap> classe pour charger et afficher des images raster et vous pouvez utiliser la <xref:System.Drawing.Imaging.Metafile> classe pour charger et afficher des images vectorielles. Le <xref:System.Drawing.Bitmap> et <xref:System.Drawing.Imaging.Metafile> classes héritent de la <xref:System.Drawing.Image> classe. Pour afficher une image vectorielle, vous avez besoin d’une instance de la <xref:System.Drawing.Graphics> classe et un <xref:System.Drawing.Imaging.Metafile>. Pour afficher une image raster, vous avez besoin d’une instance de la <xref:System.Drawing.Graphics> classe et un <xref:System.Drawing.Bitmap>. L’instance de la <xref:System.Drawing.Graphics> classe fournit le <xref:System.Drawing.Graphics.DrawImage%2A> méthode qui reçoit le <xref:System.Drawing.Imaging.Metafile> ou <xref:System.Drawing.Bitmap> en tant qu’argument.  
  
## <a name="file-types-and-cloning"></a>Types de fichiers et de clonage  
 L’exemple de code suivant montre comment construire un <xref:System.Drawing.Bitmap> à partir du fichier Climber.jpg et affiche la bitmap. Le point de destination pour l’angle supérieur gauche de l’image, (10, 10), est spécifié dans les deuxième et troisième paramètres.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 L’illustration suivante montre l’image.  
  
 ![Exemple d’image](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 Vous pouvez construire <xref:System.Drawing.Bitmap> objets à partir de graphiques différents formats de fichier : BMP, GIF, JPEG, EXIF, PNG, TIFF et icône.  
  
 L’exemple de code suivant montre comment construire <xref:System.Drawing.Bitmap> objets à partir de divers types de fichier, puis affiche les bitmaps.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 Le <xref:System.Drawing.Bitmap> classe fournit un <xref:System.Drawing.Bitmap.Clone%2A> méthode que vous pouvez utiliser pour effectuer une copie d’un objet <xref:System.Drawing.Bitmap>. Le <xref:System.Drawing.Bitmap.Clone%2A> méthode possède un paramètre du rectangle source que vous pouvez utiliser pour spécifier la partie de l’image bitmap d’origine que vous souhaitez copier. L’exemple de code suivant montre comment créer un <xref:System.Drawing.Bitmap> en clonant la moitié supérieure d’un objet <xref:System.Drawing.Bitmap>. Ensuite, les deux images sont dessinées.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 L’illustration suivante montre les deux images.  
  
 ![Rognage](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Guide pratique pour créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
