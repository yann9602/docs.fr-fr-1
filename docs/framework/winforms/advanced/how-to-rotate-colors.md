---
title: "Comment : faire pivoter des couleurs"
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
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81b022011bd5613b8e956aa83482d2836508a4f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-colors"></a>Comment : faire pivoter des couleurs
Rotation dans un espace de couleurs à quatre dimensions est difficile de visualiser. Nous pouvons facilitent la visualisation, choisissez de conserver un des composants de couleur fixe. Supposons que nous acceptons de conserver le composant alpha est fixé à 1 (entièrement opaque). Vous pouvez ensuite visualiser un espace à trois dimensions de couleur des axes de rouges, verts et bleus, comme indiqué dans l’illustration suivante.  
  
 ![Recoloriage](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")  
  
 Une couleur peut être considérée comme un point dans un espace 3D. Par exemple, le point (1, 0, 0) dans l’espace représente la couleur rouge, et le point (0, 1, 0) dans l’espace représente la couleur verte.  
  
 L’illustration suivante montre ce que cela signifie pour faire pivoter la couleur (1, 0, 0) via un angle de 60 degrés dans le plan rouge-vert. Rotation d’un plan parallèle au plan rouge-vert peut être considérée comme une rotation sur l’axe bleu.  
  
 ![Recoloriage](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")  
  
 L’illustration suivante montre comment initialiser une matrice de couleurs pour effectuer des rotations sur chacun des trois axes de coordonnées (rouge, vert, bleu).  
  
 ![Recoloriage](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")  
  
## <a name="example"></a>Exemple  
 L’exemple suivant prend une image qui est une couleur (1, 0, 0.6) et applique une rotation de 60 degrés sur l’axe bleu. L’angle de rotation est rangé dans un plan parallèle au plan rouge-vert.  
  
 L’illustration suivante montre l’image d’origine sur la gauche et l’image pivotée de couleur sur la droite.  
  
 ![Faire pivoter des couleurs](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")  
  
 L’illustration suivante montre une visualisation de la rotation de couleurs effectuée dans le code suivant.  
  
 ![Recoloriage](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements. Remplacez `RotationInput.bmp` avec un nom de fichier image et le chemin d’accès valide sur votre système.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Graphiques et dessins dans Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Recoloriage des images](../../../../docs/framework/winforms/advanced/recoloring-images.md)
