---
title: "Comment : améliorer les performances en évitant la mise à l'échelle automatique"
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
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f49fc4b1e59879b9ecc67295610187fa2e5e80d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>Comment : améliorer les performances en évitant la mise à l'échelle automatique
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]peut automatiquement mettre à l’échelle une image que vous la dessinez, ce qui diminue les performances. Ou bien, vous pouvez contrôler la mise à l’échelle de l’image en passant les dimensions du rectangle de destination à le <xref:System.Drawing.Graphics.DrawImage%2A> (méthode).  
  
 Par exemple, l’appel suivant à la <xref:System.Drawing.Graphics.DrawImage%2A> méthode spécifie un coin supérieur gauche de (50, 30) mais ne spécifie ne pas un rectangle de destination.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 Bien que ce soit la version la plus simple de la <xref:System.Drawing.Graphics.DrawImage%2A> méthode en termes de nombre d’arguments requis, il n’est pas nécessairement la plus efficace. Si la résolution utilisée par [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (habituellement 96 points par pouce) est différente de la résolution stockée dans le <xref:System.Drawing.Image> objet, puis le <xref:System.Drawing.Graphics.DrawImage%2A> méthode mettra à l’échelle l’image. Par exemple, un <xref:System.Drawing.Image> objet a une largeur de 216 pixels et une valeur de résolution horizontale stockée de 72 points par pouce. Comme 216/72 est 3, <xref:System.Drawing.Graphics.DrawImage%2A> l’échelle l’image afin qu’elle a une largeur de 3 pouces à une résolution de 96 points par pouce. Autrement dit, <xref:System.Drawing.Graphics.DrawImage%2A> affiche une image qui a une largeur de 96 x 3 = 288 pixels.  
  
 Même si la résolution d’écran est différente de 96 points par pouce, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sera probablement l’échelle l’image comme si la résolution d’écran était de 96 points par pouce. C’est parce qu’un [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> objet est associé à un contexte de périphérique et à quel moment [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] requêtes le contexte de périphérique pour la résolution d’écran, le résultat est habituellement 96, quelle que soit la résolution réelle de l’écran. Vous pouvez éviter la mise à l’échelle automatique en spécifiant le rectangle de destination dans le <xref:System.Drawing.Graphics.DrawImage%2A> (méthode).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant dessine l’image même à deux reprises. Dans le premier cas, la largeur et la hauteur du rectangle de destination ne sont pas spécifiés, et l’image est ajustée automatiquement. Dans le second cas, la largeur et la hauteur (exprimée en pixels) du rectangle de destination sont spécifiés pour être le même que la largeur et la hauteur de l’image d’origine. L’illustration suivante montre l’image rendue deux fois.  
  
 ![Mise à l’échelle de Texture](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>. Remplacez Texture.jpg avec un nom de l’image et le chemin d’accès valides sur votre système.  
  
## <a name="see-also"></a>Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
