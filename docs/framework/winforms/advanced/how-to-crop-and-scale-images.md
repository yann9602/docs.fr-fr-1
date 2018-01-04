---
title: "Comment : rogner et mettre à l'échelle des images"
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
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de905cf70013098a4282e3f4af092ccbea16ccfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-crop-and-scale-images"></a>Comment : rogner et mettre à l'échelle des images
Le <xref:System.Drawing.Graphics> classe fournit plusieurs <xref:System.Drawing.Graphics.DrawImage%2A> méthodes, dont certaines ont des paramètres de rectangle source et destination que vous pouvez utiliser pour rogner et mise à l’échelle des images.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant construit une <xref:System.Drawing.Image> objet à partir du fichier de disque Apple.gif. Le code dessine l’image entière dans sa taille d’origine. Le code appelle ensuite la <xref:System.Drawing.Graphics.DrawImage%2A> méthode d’un <xref:System.Drawing.Graphics> objet à dessiner une partie de l’image dans un rectangle de destination qui est plus grand que l’image d’origine.  
  
 Le <xref:System.Drawing.Graphics.DrawImage%2A> méthode détermine la partie de la pomme à dessiner en examinant le rectangle source, qui est spécifié par les troisième, quatrième, cinquième et sixième arguments. Dans ce cas, la pomme est rognée à 75 pour cent de sa largeur et 75 pour cent de sa hauteur.  
  
 Le <xref:System.Drawing.Graphics.DrawImage%2A> méthode détermine où dessiner la pomme rognée et la taille à attribuer à la pomme rognée en examinant le rectangle de destination, qui est spécifié par le deuxième argument. Dans ce cas, le rectangle de destination est 30 pour cent plus large et 30 pour cent plus grands que l’image d’origine.  
  
 L’illustration suivante montre la pomme d’origine et la mise à l’échelle, pomme rognée.  
  
 ![Rognage et mise à l’échelle](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>. Veillez à remplacer `Apple.gif` avec un nom de fichier image et le chemin d’accès valides sur votre système.  
  
## <a name="see-also"></a>Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
