---
title: "Comment : dessiner du texte dans un Windows Form"
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
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 23919145a04bb4b3d1674b153649aca2228364eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-text-on-a-windows-form"></a><span data-ttu-id="e7892-102">Comment : dessiner du texte dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="e7892-102">How to: Draw Text on a Windows Form</span></span>
<span data-ttu-id="e7892-103">L’exemple de code suivant montre comment utiliser le <xref:System.Drawing.Graphics.DrawString%2A> méthode de le <xref:System.Drawing.Graphics> pour dessiner du texte dans un formulaire.</span><span class="sxs-lookup"><span data-stu-id="e7892-103">The following code example shows how to use the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> to draw text on a form.</span></span> <span data-ttu-id="e7892-104">Vous pouvez également utiliser <xref:System.Windows.Forms.TextRenderer> pour dessiner du texte sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="e7892-104">Alternatively, you can use <xref:System.Windows.Forms.TextRenderer> for drawing text on a form.</span></span> <span data-ttu-id="e7892-105">Pour plus d’informations, consultez [Comment : dessiner le texte avec GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md).</span><span class="sxs-lookup"><span data-stu-id="e7892-105">For more information, see [How to: Draw Text with GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7892-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7892-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7892-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e7892-107">Compiling the Code</span></span>  
 <span data-ttu-id="e7892-108">Vous ne pouvez pas appeler la <xref:System.Drawing.Graphics.DrawString%2A> méthode dans le <xref:System.Windows.Forms.Form.Load> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="e7892-108">You cannot call the <xref:System.Drawing.Graphics.DrawString%2A> method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="e7892-109">Le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou masqué par une autre forme.</span><span class="sxs-lookup"><span data-stu-id="e7892-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="e7892-110">Pour que votre contenu soit automatiquement repeint, vous devez substituer la <xref:System.Windows.Forms.Control.OnPaint%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="e7892-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e7892-111">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="e7892-111">Robust Programming</span></span>  
 <span data-ttu-id="e7892-112">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="e7892-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e7892-113">La police Arial n’est pas installée.</span><span class="sxs-lookup"><span data-stu-id="e7892-113">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7892-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7892-114">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawString%2A>  
 <xref:System.Windows.Forms.TextRenderer.DrawText%2A>  
 <xref:System.Drawing.StringFormat.FormatFlags%2A>  
 <xref:System.Drawing.StringFormatFlags>  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="e7892-115">Mise en route de la programmation graphique</span><span class="sxs-lookup"><span data-stu-id="e7892-115">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="e7892-116">Guide pratique pour écrire du texte avec GDI</span><span class="sxs-lookup"><span data-stu-id="e7892-116">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
