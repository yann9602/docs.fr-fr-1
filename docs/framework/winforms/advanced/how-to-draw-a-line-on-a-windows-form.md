---
title: "Comment : dessiner une ligne dans un Windows Form"
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
f1_keywords: Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 984cdaca14c354ca78118412911c69c282ddd1bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="d77b0-102">Comment : dessiner une ligne dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="d77b0-102">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="d77b0-103">Cet exemple dessine une ligne dans un formulaire.</span><span class="sxs-lookup"><span data-stu-id="d77b0-103">This example draws a line on a form.</span></span> <span data-ttu-id="d77b0-104">En général, lorsque vous dessinez sur un formulaire, vous gérez du formulaire <xref:System.Windows.Forms.Control.Paint> événement et d’effectuer le dessin à l’aide du <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> propriété de la <xref:System.Windows.Forms.PaintEventArgs>, comme illustré dans cet exemple</span><span class="sxs-lookup"><span data-stu-id="d77b0-104">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="d77b0-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="d77b0-105">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d77b0-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d77b0-106">Compiling the Code</span></span>  
 <span data-ttu-id="d77b0-107">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs>`e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="d77b0-107">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d77b0-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="d77b0-108">Robust Programming</span></span>  
 <span data-ttu-id="d77b0-109">Vous devez toujours appeler <xref:System.IDisposable.Dispose%2A> sur tous les objets qui consomment des ressources système, telles que <xref:System.Drawing.Pen> objets.</span><span class="sxs-lookup"><span data-stu-id="d77b0-109">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d77b0-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d77b0-110">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawLine%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="d77b0-111">Mise en route de la programmation graphique</span><span class="sxs-lookup"><span data-stu-id="d77b0-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="d77b0-112">Utilisation d'un stylet pour dessiner des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="d77b0-112">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="d77b0-113">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d77b0-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
