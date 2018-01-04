---
title: "Comment : dessiner un rectangle rempli dans un Windows Form"
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
- cpp
f1_keywords: Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17d143c0c265fea876d084ebc21663d93553fe9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a>Comment : dessiner un rectangle rempli dans un Windows Form
Cet exemple dessine un rectangle rempli dans un formulaire.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Vous ne pouvez pas appeler cette méthode le <xref:System.Windows.Forms.Form.Load> Gestionnaire d’événements. Le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou masqué par une autre forme. Pour que votre contenu soit automatiquement repeint, vous devez substituer la <xref:System.Windows.Forms.Control.OnPaint%2A> (méthode).  
  
## <a name="robust-programming"></a>Programmation fiable  
 Vous devez toujours appeler <xref:System.IDisposable.Dispose%2A> sur tous les objets qui consomment des ressources système, telles que <xref:System.Drawing.Brush> et <xref:System.Drawing.Graphics> objets.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.Graphics.FillRectangle%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Graphiques et dessins dans Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Pinceaux et remplissage de formes dans GDI+](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)
