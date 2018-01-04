---
title: "Comment : dessiner une ligne avec des embouts de ligne"
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
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4048757e11724aa1e175d8b18c47f48d22d807e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-line-with-line-caps"></a>Comment : dessiner une ligne avec des embouts de ligne
Vous pouvez dessiner le début ou la fin d’une ligne dans une des différentes formes appelées des embouts de ligne. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]prend en charge plusieurs embouts de ligne, telles que rond, carré, losange et pointe de flèche.  
  
## <a name="example"></a>Exemple  
 Vous pouvez spécifier des embouts de ligne pour le début d’une ligne (embout de début), à la fin d’une ligne (extrémité de fin) ou les tirets d’une ligne en pointillés (embout pointillé).  
  
 L’exemple suivant dessine une ligne avec une pointe de flèche à une extrémité et une extrémité arrondie à l’autre extrémité. L’illustration montre la ligne résultante :  
  
 ![Stylets](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Créer un Windows Form et gérer du formulaire <xref:System.Windows.Forms.Control.Paint> événement. Collez l’exemple de code dans le <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements en passant `e` comme <xref:System.Windows.Forms.PaintEventArgs>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>  
 [Graphiques et dessins dans Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
