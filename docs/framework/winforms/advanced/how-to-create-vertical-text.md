---
title: "Comment : créer du texte vertical"
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
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8615a90094232381f2c8d51f5593276d0c01f892
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="f6142-102">Comment : créer du texte vertical</span><span class="sxs-lookup"><span data-stu-id="f6142-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="f6142-103">Vous pouvez utiliser un <xref:System.Drawing.StringFormat> pour spécifier que le texte doit être dessiné verticalement et non horizontalement.</span><span class="sxs-lookup"><span data-stu-id="f6142-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6142-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f6142-104">Example</span></span>  
 <span data-ttu-id="f6142-105">L’exemple suivant affecte la valeur <xref:System.Drawing.StringFormatFlags.DirectionVertical> à la <xref:System.Drawing.StringFormat.FormatFlags%2A> propriété d’un <xref:System.Drawing.StringFormat> objet.</span><span class="sxs-lookup"><span data-stu-id="f6142-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="f6142-106">Que <xref:System.Drawing.StringFormat> objet est passé à la <xref:System.Drawing.Graphics.DrawString%2A> méthode de la <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="f6142-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="f6142-107">La valeur <xref:System.Drawing.StringFormatFlags.DirectionVertical> est un membre de la <xref:System.Drawing.StringFormatFlags> énumération.</span><span class="sxs-lookup"><span data-stu-id="f6142-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="f6142-108">L’illustration suivante montre le texte vertical.</span><span class="sxs-lookup"><span data-stu-id="f6142-108">The following illustration shows the vertical text.</span></span>  
  
 <span data-ttu-id="f6142-109">![Polices du texte](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")</span><span class="sxs-lookup"><span data-stu-id="f6142-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6142-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f6142-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="f6142-111">L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e` , qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="f6142-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6142-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6142-112">See Also</span></span>  
 [<span data-ttu-id="f6142-113">Guide pratique pour écrire du texte avec GDI</span><span class="sxs-lookup"><span data-stu-id="f6142-113">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
