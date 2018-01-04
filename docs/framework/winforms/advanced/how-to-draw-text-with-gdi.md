---
title: "Comment : écrire du texte avec GDI"
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
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6c7fb4d8c6bd93481935a9f2ef7dd4b34af7e71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-text-with-gdi"></a>Comment : écrire du texte avec GDI
Avec la <xref:System.Windows.Forms.TextRenderer.DrawText%2A> méthode dans le <xref:System.Windows.Forms.TextRenderer> (classe), vous pouvez accéder aux [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] fonctionnalité pour dessiner du texte sur un formulaire ou un contrôle. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]rendu de texte offre généralement de meilleures performances et une mesure que de texte plus précise [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
> [!NOTE]
>  Le <xref:System.Windows.Forms.TextRenderer.DrawText%2A> méthodes de la <xref:System.Windows.Forms.TextRenderer> classe ne sont pas pris en charge pour l’impression. Lors de l’impression, utilisez toujours la <xref:System.Drawing.Graphics.DrawString%2A> méthodes de la <xref:System.Drawing.Graphics> classe.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment dessiner du texte sur plusieurs lignes dans un rectangle à l’aide de la <xref:System.Windows.Forms.TextRenderer.DrawText%2A> (méthode).  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 Pour afficher le texte avec le <xref:System.Windows.Forms.TextRenderer> (classe), vous devez une <xref:System.Drawing.IDeviceContext>, comme un <xref:System.Drawing.Graphics> et un <xref:System.Drawing.Font>, un emplacement pour dessiner le texte et la couleur dans laquelle il doit être dessiné. Si vous le souhaitez, vous pouvez spécifier le texte à l’aide de la mise en forme le <xref:System.Windows.Forms.TextFormatFlags> énumération.  
  
 Pour plus d’informations sur l’obtention d’un <xref:System.Drawing.Graphics>, consultez [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md). Pour plus d’informations sur la construction d’un <xref:System.Drawing.Font>, consultez [Comment : construire des familles de polices et les polices](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple de code précédent est conçu pour une utilisation avec Windows Forms et nécessite le <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
