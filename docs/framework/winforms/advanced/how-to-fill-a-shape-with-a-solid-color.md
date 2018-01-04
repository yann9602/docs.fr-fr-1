---
title: "Comment : remplir une forme avec une couleur unie"
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
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f016404feeac47c5f77527b8baa68d70742d4763
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a><span data-ttu-id="e2f7d-102">Comment : remplir une forme avec une couleur unie</span><span class="sxs-lookup"><span data-stu-id="e2f7d-102">How to: Fill a Shape with a Solid Color</span></span>
<span data-ttu-id="e2f7d-103">Pour remplir une forme avec une couleur unie, créez un <xref:System.Drawing.SolidBrush> de l’objet, puis passez-le <xref:System.Drawing.SolidBrush> objet en tant qu’argument à une des méthodes de remplissage de la <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="e2f7d-103">To fill a shape with a solid color, create a <xref:System.Drawing.SolidBrush> object, and then pass that <xref:System.Drawing.SolidBrush> object as an argument to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="e2f7d-104">L’exemple suivant montre comment remplir une ellipse avec la couleur rouge.</span><span class="sxs-lookup"><span data-stu-id="e2f7d-104">The following example shows how to fill an ellipse with the color red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2f7d-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="e2f7d-105">Example</span></span>  
 <span data-ttu-id="e2f7d-106">Dans le code suivant, le <xref:System.Drawing.SolidBrush.%23ctor%2A> constructeur accepte un <xref:System.Drawing.Color> objet comme seul argument.</span><span class="sxs-lookup"><span data-stu-id="e2f7d-106">In the following code, the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor takes a <xref:System.Drawing.Color> object as its only argument.</span></span> <span data-ttu-id="e2f7d-107">Les valeurs utilisées par la <xref:System.Drawing.Color.FromArgb%2A> méthode représentent les composants alphanumériques, rouges, verts et bleus de la couleur.</span><span class="sxs-lookup"><span data-stu-id="e2f7d-107">The values used by the <xref:System.Drawing.Color.FromArgb%2A> method represent the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="e2f7d-108">Chacune de ces valeurs doit être comprise entre 0 et 255.</span><span class="sxs-lookup"><span data-stu-id="e2f7d-108">Each of these values must be in the range 0 through 255.</span></span> <span data-ttu-id="e2f7d-109">Le premier 255 indique que la couleur est entièrement opaque, et le deuxième 255 indique que le composant rouge est à intensité complète.</span><span class="sxs-lookup"><span data-stu-id="e2f7d-109">The first 255 indicates that the color is fully opaque, and the second 255 indicates that the red component is at full intensity.</span></span> <span data-ttu-id="e2f7d-110">Les deux zéros indiquent que les composants verts et bleus ont une intensité de 0.</span><span class="sxs-lookup"><span data-stu-id="e2f7d-110">The two zeros indicate that the green and blue components both have an intensity of 0.</span></span>  
  
 <span data-ttu-id="e2f7d-111">Les quatre nombres (0, 0, 100, 60) passés à la <xref:System.Drawing.Graphics.FillEllipse%2A> méthode spécifier l’emplacement et la taille du rectangle englobant de l’ellipse.</span><span class="sxs-lookup"><span data-stu-id="e2f7d-111">The four numbers (0, 0, 100, 60) passed to the <xref:System.Drawing.Graphics.FillEllipse%2A> method specify the location and size of the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="e2f7d-112">Le rectangle a un coin supérieur gauche de (0, 0), une largeur de 100 et une hauteur de 60.</span><span class="sxs-lookup"><span data-stu-id="e2f7d-112">The rectangle has an upper-left corner of (0, 0), a width of 100, and a height of 60.</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e2f7d-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e2f7d-113">Compiling the Code</span></span>  
 <span data-ttu-id="e2f7d-114">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="e2f7d-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f7d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2f7d-115">See Also</span></span>  
 [<span data-ttu-id="e2f7d-116">Utilisation d'un pinceau pour remplir des formes</span><span class="sxs-lookup"><span data-stu-id="e2f7d-116">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
