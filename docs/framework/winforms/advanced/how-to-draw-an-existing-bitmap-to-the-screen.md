---
title: "Comment : dessiner une bitmap existante à l'écran"
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
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f435c397832e8f64b2bf911a59aae7578ffd3bdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a>Comment : dessiner une bitmap existante à l'écran
Vous pouvez facilement dessiner une image existante à l’écran. Vous devez d’abord créer un <xref:System.Drawing.Bitmap> objet à l’aide du constructeur de bitmap qui prend un nom de fichier <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>. Ce constructeur accepte des images avec différents formats de fichiers, notamment BMP, GIF, JPEG, PNG et TIFF. Après avoir créé le <xref:System.Drawing.Bitmap> d’objet, qui <xref:System.Drawing.Bitmap> de l’objet à la <xref:System.Drawing.Graphics.DrawImage%2A> méthode d’un <xref:System.Drawing.Graphics> objet.  
  
## <a name="example"></a>Exemple  
 Cet exemple crée un <xref:System.Drawing.Bitmap> objet à partir d’un fichier JPEG, puis dessine l’image bitmap avec son coin supérieur gauche à (60, 10).  
  
 L’illustration suivante montre la bitmap dessinée à l’emplacement spécifié.  
  
 ![Position de l’image](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques et dessins dans Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
