---
title: "Comment : joindre des lignes"
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
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d12cc7b4b4c878ec812190fd56a1face64118ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-join-lines"></a><span data-ttu-id="fde34-102">Comment : joindre des lignes</span><span class="sxs-lookup"><span data-stu-id="fde34-102">How to: Join Lines</span></span>
<span data-ttu-id="fde34-103">Une jointure de ligne est la zone commune formée par deux lignes dont les extrémités se rencontrent ou se chevauchent.</span><span class="sxs-lookup"><span data-stu-id="fde34-103">A line join is the common area that is formed by two lines whose ends meet or overlap.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="fde34-104">fournit trois styles de jonction de ligne : angle aigu, en biseau et arrondie.</span><span class="sxs-lookup"><span data-stu-id="fde34-104"> provides three line join styles: miter, bevel, and round.</span></span> <span data-ttu-id="fde34-105">Style de ligne de jointure est une propriété de la <xref:System.Drawing.Pen> classe.</span><span class="sxs-lookup"><span data-stu-id="fde34-105">Line join style is a property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="fde34-106">Lorsque vous spécifiez un style de jointure de ligne pour un <xref:System.Drawing.Pen> ce style de jointure sera appliqué à toutes les lignes connectées dans un objet <xref:System.Drawing.Drawing2D.GraphicsPath> objet dessiné à l’aide de ce stylet.</span><span class="sxs-lookup"><span data-stu-id="fde34-106">When you specify a line join style for a <xref:System.Drawing.Pen> object, that join style will be applied to all the connected lines in any <xref:System.Drawing.Drawing2D.GraphicsPath> object drawn using that pen.</span></span>  
  
 <span data-ttu-id="fde34-107">L’illustration suivante montre les résultats de l’exemple de jointure de ligne en relief.</span><span class="sxs-lookup"><span data-stu-id="fde34-107">The following illustration shows the results of the beveled line join example.</span></span>  
  
 <span data-ttu-id="fde34-108">![Stylets](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span><span class="sxs-lookup"><span data-stu-id="fde34-108">![Pens](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span></span>  
  
## <a name="example"></a><span data-ttu-id="fde34-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="fde34-109">Example</span></span>  
 <span data-ttu-id="fde34-110">Vous pouvez spécifier le style de ligne de jointure à l’aide de la <xref:System.Drawing.Pen.LineJoin%2A> propriété de la <xref:System.Drawing.Pen> classe.</span><span class="sxs-lookup"><span data-stu-id="fde34-110">You can specify the line join style by using the <xref:System.Drawing.Pen.LineJoin%2A> property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="fde34-111">L’exemple illustre une ligne en relief entre une ligne horizontale et une ligne verticale.</span><span class="sxs-lookup"><span data-stu-id="fde34-111">The example demonstrates a beveled line join between a horizontal line and a vertical line.</span></span> <span data-ttu-id="fde34-112">Dans le code suivant, la valeur <xref:System.Drawing.Drawing2D.LineJoin.Bevel> affectée à la <xref:System.Drawing.Pen.LineJoin%2A> propriété est un membre de la <xref:System.Drawing.Drawing2D.LineJoin> énumération.</span><span class="sxs-lookup"><span data-stu-id="fde34-112">In the following code, the value <xref:System.Drawing.Drawing2D.LineJoin.Bevel> assigned to the <xref:System.Drawing.Pen.LineJoin%2A> property is a member of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration.</span></span> <span data-ttu-id="fde34-113">Les autres membres de la <xref:System.Drawing.Drawing2D.LineJoin> énumération sont <xref:System.Drawing.Drawing2D.LineJoin.Miter> et <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span><span class="sxs-lookup"><span data-stu-id="fde34-113">The other members of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration are <xref:System.Drawing.Drawing2D.LineJoin.Miter> and <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fde34-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="fde34-114">Compiling the Code</span></span>  
 <span data-ttu-id="fde34-115">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="fde34-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde34-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fde34-116">See Also</span></span>  
 [<span data-ttu-id="fde34-117">Utilisation d'un stylet pour dessiner des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="fde34-117">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
