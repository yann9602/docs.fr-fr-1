---
title: "Comment : dessiner avec des pinceaux opaques et translucides"
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
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4af2664851ed0903a362a4b88edf1db9bb042dfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="f7956-102">Comment : dessiner avec des pinceaux opaques et translucides</span><span class="sxs-lookup"><span data-stu-id="f7956-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="f7956-103">Quand vous remplissez une forme, vous devez passer un objet <xref:System.Drawing.Brush> à l'une des méthodes de remplissage de la classe <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="f7956-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="f7956-104">L'unique paramètre du constructeur <xref:System.Drawing.SolidBrush.%23ctor%2A> est un objet <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="f7956-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="f7956-105">Pour remplir une forme opaque, affectez au composant alpha de la couleur la valeur 255.</span><span class="sxs-lookup"><span data-stu-id="f7956-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="f7956-106">Pour remplir une forme translucide, affectez au composant alpha n'importe quelle valeur comprise entre 1 et 254.</span><span class="sxs-lookup"><span data-stu-id="f7956-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="f7956-107">Quand vous remplissez une forme translucide, la couleur de la forme est fusionnée avec les couleurs d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="f7956-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="f7956-108">Le composant alpha spécifie comment les couleurs de forme et d'arrière-plan sont mélangées ; les valeurs alpha proches de 0 favorisent les couleurs d'arrière-plan, tandis que les valeurs alpha proches de 255 favorisent la couleur de forme.</span><span class="sxs-lookup"><span data-stu-id="f7956-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7956-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="f7956-109">Example</span></span>  
 <span data-ttu-id="f7956-110">L'exemple suivant dessine une bitmap, puis remplit trois ellipses qui chevauchent la bitmap.</span><span class="sxs-lookup"><span data-stu-id="f7956-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="f7956-111">La première ellipse utilise un composant alpha de 255. Elle est donc opaque.</span><span class="sxs-lookup"><span data-stu-id="f7956-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="f7956-112">Les deuxième et troisième ellipses utilisent un composant alpha de 128 et sont donc translucides. Vous pouvez voir l'image d'arrière-plan à travers les ellipses.</span><span class="sxs-lookup"><span data-stu-id="f7956-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="f7956-113">L'appel qui définit la propriété <xref:System.Drawing.Graphics.CompositingQuality%2A> fait en sorte que la fusion pour la troisième ellipse s'effectue parallèlement à une correction gamma.</span><span class="sxs-lookup"><span data-stu-id="f7956-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  
  
 <span data-ttu-id="f7956-114">L'illustration suivante montre la sortie du code suivant.</span><span class="sxs-lookup"><span data-stu-id="f7956-114">The following illustration shows the output of the following code.</span></span>  
  
 <span data-ttu-id="f7956-115">![Opaques et translucides](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")</span><span class="sxs-lookup"><span data-stu-id="f7956-115">![Opaque and Semitransparent](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f7956-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f7956-116">Compiling the Code</span></span>  
 <span data-ttu-id="f7956-117">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs>`e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="f7956-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7956-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7956-118">See Also</span></span>  
 [<span data-ttu-id="f7956-119">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7956-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="f7956-120">Fusion alpha de lignes et de remplissages</span><span class="sxs-lookup"><span data-stu-id="f7956-120">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [<span data-ttu-id="f7956-121">Guide pratique pour affecter un arrière-plan transparent à votre contrôle</span><span class="sxs-lookup"><span data-stu-id="f7956-121">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [<span data-ttu-id="f7956-122">Guide pratique pour dessiner des lignes opaques et translucides</span><span class="sxs-lookup"><span data-stu-id="f7956-122">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
