---
title: "Comment : écrire du texte à un emplacement spécifié"
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
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e4ed36740cd7e9478be3b4a7187329fb092c821
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-text-at-a-specified-location"></a>Comment : écrire du texte à un emplacement spécifié
Lorsque vous effectuez un dessin personnalisé, vous pouvez dessiner du texte dans une seule ligne horizontale, en commençant à un point spécifié. Vous pouvez dessiner du texte de cette manière à l’aide de la <xref:System.Drawing.Graphics.DrawString%2A> surchargées de la <xref:System.Drawing.Graphics> classe qui prend un <xref:System.Drawing.Point> ou <xref:System.Drawing.PointF> paramètre. Le <xref:System.Drawing.Graphics.DrawString%2A> méthode requiert également un <xref:System.Drawing.Brush> et<xref:System.Drawing.Font>  
  
 Vous pouvez également utiliser le <xref:System.Windows.Forms.TextRenderer.DrawText%2A> surchargées de la <xref:System.Windows.Forms.TextRenderer> qui accepte un <xref:System.Drawing.Point>. <xref:System.Windows.Forms.TextRenderer.DrawText%2A>requiert également un <xref:System.Drawing.Color> et un <xref:System.Drawing.Font>.  
  
 L’illustration suivante montre la sortie du texte dessiné à un point spécifié lorsque vous utilisez la <xref:System.Drawing.Graphics.DrawString%2A> la méthode surchargée.  
  
 ![Polices du texte](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>Pour dessiner une ligne de texte avec GDI +  
  
1.  Utilisez le <xref:System.Drawing.Graphics.DrawString%2A> méthode, en passant le texte que vous le souhaitez, <xref:System.Drawing.Point> ou <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, et <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>Pour dessiner une ligne de texte avec GDI  
  
1.  Utilisez le <xref:System.Windows.Forms.TextRenderer.DrawText%2A> méthode, en passant le texte que vous le souhaitez, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, et <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Les exemples précédents nécessitent :  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour écrire du texte avec GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Guide pratique pour construire des familles de polices et des polices](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [Guide pratique pour écrire du texte renvoyé à la ligne dans un rectangle](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)
