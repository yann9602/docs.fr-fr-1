---
title: "Comment : dessiner une ligne remplie d'une texture"
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
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0aaba7981dc68bf7bdfe6dbd45685e61f7b763a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>Comment : dessiner une ligne remplie d'une texture
Au lieu de dessin d’une ligne avec une couleur unie, vous pouvez dessiner une ligne avec une texture. Pour dessiner des lignes et des courbes avec une texture, créez un <xref:System.Drawing.TextureBrush> de l’objet et passer <xref:System.Drawing.TextureBrush> de l’objet à un <xref:System.Drawing.Pen.%23ctor%2A> constructeur. La bitmap associée au pinceau de la texture est utilisée pour remplir le plan (de façon invisible) avec, et lorsque le stylet dessine une ligne ou une courbe, le trait du stylet débouche sur certains pixels de la texture en mosaïque.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un <xref:System.Drawing.Bitmap> objet à partir du fichier `Texture1.jpg`. Cette bitmap est utilisée pour construire un <xref:System.Drawing.TextureBrush> objet et le <xref:System.Drawing.TextureBrush> objet est utilisé pour construire un <xref:System.Drawing.Pen> objet. L’appel à <xref:System.Drawing.Graphics.DrawImage%2A> Dessine l’image bitmap avec son coin supérieur gauche à (0, 0). L’appel à <xref:System.Drawing.Graphics.DrawEllipse%2A> utilise le <xref:System.Drawing.Pen> objet pour dessiner une ellipse avec une texture.  
  
 L’illustration suivante montre l’image bitmap et l’ellipse avec une texture.  
  
 ![Stylets](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Créer un Windows Form et gérer du formulaire <xref:System.Windows.Forms.Control.Paint> événement. Collez le code précédent dans le <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements. Remplacez `Texture.jpg` avec une image valide sur votre système.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Graphiques et dessins dans Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
