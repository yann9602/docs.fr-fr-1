---
title: "Comment : utiliser une matrice de couleurs pour définir des valeurs alpha dans des images"
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
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dde9417782e4404237a995364d65058f023c3e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Comment : utiliser une matrice de couleurs pour définir des valeurs alpha dans des images
Le <xref:System.Drawing.Bitmap> classe (qui hérite de la <xref:System.Drawing.Image> classe) et la <xref:System.Drawing.Imaging.ImageAttributes> classe fournit des fonctionnalités pour obtenir et définir des valeurs en pixels. Vous pouvez utiliser la <xref:System.Drawing.Imaging.ImageAttributes> classe pour modifier la valeur alpha de valeurs pour l’intégralité d’une image, ou vous pouvez appeler la <xref:System.Drawing.Bitmap.SetPixel%2A> méthode de la <xref:System.Drawing.Bitmap> classe pour modifier les valeurs de pixel individuelles.  
  
## <a name="example"></a>Exemple  
 La <xref:System.Drawing.Imaging.ImageAttributes> classe comporte plusieurs propriétés que vous pouvez utiliser pour modifier les images pendant le rendu. Dans l’exemple suivant, un <xref:System.Drawing.Imaging.ImageAttributes> objet est utilisé pour définir toutes les valeurs alpha à 80 pour cent de leur nature. Il suffit de l’initialisation d’une matrice de couleurs et la définition de la valeur alpha de mise à l’échelle de la valeur de la matrice à 0,8. L’adresse de la matrice des couleurs est passée à la <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> méthode de la <xref:System.Drawing.Imaging.ImageAttributes> objet et le <xref:System.Drawing.Imaging.ImageAttributes> objet est passé à la <xref:System.Drawing.Graphics.DrawString%2A> méthode de la <xref:System.Drawing.Graphics> objet.  
  
 Pendant le rendu, les valeurs alphanumériques dans la bitmap sont converties à 80 pour cent de leur nature. Cela entraîne une image qui est fusionnée avec l’arrière-plan. Comme le montre l’illustration suivante, l’image bitmap semble transparente ; Vous pouvez voir la ligne noire unie par son biais.  
  
 ![Fusion alpha utilisant une matrice](../../../../docs/framework/winforms/advanced/media/image2.png "image2")  
  
 Où l’image est au-dessus de la partie blanche de l’arrière-plan, l’image a été fusionnée avec la couleur blanche. L’image où l’image dépasse la ligne noire, est fusionnée avec la couleur noire.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques et dessins dans Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Fusion alpha de lignes et de remplissages](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
