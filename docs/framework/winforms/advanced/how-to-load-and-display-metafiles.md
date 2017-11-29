---
title: "Comment : charger et afficher des métafichiers"
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
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 722b6d36801c69e500535a32e952ef8f45634d03
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-load-and-display-metafiles"></a>Comment : charger et afficher des métafichiers
Le <xref:System.Drawing.Imaging.Metafile> (classe), qui hérite de la <xref:System.Drawing.Image> de classe, fournit des méthodes pour l’enregistrement, l’affichage et examen d’images vectorielles.  
  
## <a name="example"></a>Exemple  
 Pour afficher une image vectorielle (métafichier) à l’écran, vous devez un <xref:System.Drawing.Imaging.Metafile> objet et un <xref:System.Drawing.Graphics> objet. Passez le nom d’un fichier (ou un flux de données) à un <xref:System.Drawing.Imaging.Metafile> constructeur. Après avoir créé un <xref:System.Drawing.Imaging.Metafile> d’objet, qui <xref:System.Drawing.Imaging.Metafile> de l’objet à la <xref:System.Drawing.Graphics.DrawImage%2A> méthode d’un <xref:System.Drawing.Graphics> objet.  
  
 L’exemple crée un <xref:System.Drawing.Imaging.Metafile> objet à partir d’un fichier EMF (métafichier amélioré), puis dessine l’image avec son coin supérieur gauche à (60, 10).  
  
 L’illustration suivante montre le métafichier dessiné à l’emplacement spécifié.  
  
 ![Position de l’image](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
