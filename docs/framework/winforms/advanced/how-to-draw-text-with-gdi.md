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
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="3cde9-102">Comment : écrire du texte avec GDI</span><span class="sxs-lookup"><span data-stu-id="3cde9-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="3cde9-103">Avec la <xref:System.Windows.Forms.TextRenderer.DrawText%2A> méthode dans le <xref:System.Windows.Forms.TextRenderer> (classe), vous pouvez accéder aux [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] fonctionnalité pour dessiner du texte sur un formulaire ou un contrôle.</span><span class="sxs-lookup"><span data-stu-id="3cde9-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] functionality for drawing text on a form or control.</span></span> [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]<span data-ttu-id="3cde9-104">rendu de texte offre généralement de meilleures performances et une mesure que de texte plus précise [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3cde9-104"> text rendering typically offers better performance and more accurate text measuring than [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cde9-105">Le <xref:System.Windows.Forms.TextRenderer.DrawText%2A> méthodes de la <xref:System.Windows.Forms.TextRenderer> classe ne sont pas pris en charge pour l’impression.</span><span class="sxs-lookup"><span data-stu-id="3cde9-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="3cde9-106">Lors de l’impression, utilisez toujours la <xref:System.Drawing.Graphics.DrawString%2A> méthodes de la <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="3cde9-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cde9-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="3cde9-107">Example</span></span>  
 <span data-ttu-id="3cde9-108">L’exemple de code suivant montre comment dessiner du texte sur plusieurs lignes dans un rectangle à l’aide de la <xref:System.Windows.Forms.TextRenderer.DrawText%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="3cde9-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="3cde9-109">Pour afficher le texte avec le <xref:System.Windows.Forms.TextRenderer> (classe), vous devez une <xref:System.Drawing.IDeviceContext>, comme un <xref:System.Drawing.Graphics> et un <xref:System.Drawing.Font>, un emplacement pour dessiner le texte et la couleur dans laquelle il doit être dessiné.</span><span class="sxs-lookup"><span data-stu-id="3cde9-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="3cde9-110">Si vous le souhaitez, vous pouvez spécifier le texte à l’aide de la mise en forme le <xref:System.Windows.Forms.TextFormatFlags> énumération.</span><span class="sxs-lookup"><span data-stu-id="3cde9-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="3cde9-111">Pour plus d’informations sur l’obtention d’un <xref:System.Drawing.Graphics>, consultez [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="3cde9-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="3cde9-112">Pour plus d’informations sur la construction d’un <xref:System.Drawing.Font>, consultez [Comment : construire des familles de polices et les polices](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).</span><span class="sxs-lookup"><span data-stu-id="3cde9-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3cde9-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3cde9-113">Compiling the Code</span></span>  
 <span data-ttu-id="3cde9-114">L’exemple de code précédent est conçu pour une utilisation avec Windows Forms et nécessite le <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="3cde9-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cde9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cde9-115">See Also</span></span>  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [<span data-ttu-id="3cde9-116">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="3cde9-116">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
