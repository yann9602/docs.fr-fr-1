---
title: Utilisation d'un stylet pour dessiner des lignes et des formes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0913dc2745e1b244e4b03c0e6b946441a401c5b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="6668c-102">Utilisation d'un stylet pour dessiner des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="6668c-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="6668c-103">Utilisez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objets pour dessiner des segments de ligne, des courbes et des contours des formes.</span><span class="sxs-lookup"><span data-stu-id="6668c-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="6668c-104">Dans cette section, *ligne* fait référence à un de ces éléments, sauf si spécifié pour n'indiquer qu’un segment de ligne.</span><span class="sxs-lookup"><span data-stu-id="6668c-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="6668c-105">Définir les propriétés d’un stylet pour contrôler la couleur, largeur, l’alignement et le style des lignes dessinées avec ce stylet.</span><span class="sxs-lookup"><span data-stu-id="6668c-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6668c-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6668c-106">In This Section</span></span>  
 [<span data-ttu-id="6668c-107">Guide pratique pour utiliser un stylet pour dessiner des lignes</span><span class="sxs-lookup"><span data-stu-id="6668c-107">How to: Use a Pen to Draw Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="6668c-108">Explique comment dessiner des lignes.</span><span class="sxs-lookup"><span data-stu-id="6668c-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="6668c-109">Guide pratique pour utiliser un stylet pour dessiner des rectangles</span><span class="sxs-lookup"><span data-stu-id="6668c-109">How to: Use a Pen to Draw Rectangles</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="6668c-110">Décrit comment dessiner des rectangles.</span><span class="sxs-lookup"><span data-stu-id="6668c-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="6668c-111">Guide pratique pour définir la largeur et l'alignement du stylet</span><span class="sxs-lookup"><span data-stu-id="6668c-111">How to: Set Pen Width and Alignment</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="6668c-112">Explique comment modifier la largeur et l’alignement d’un `Pen` objet.</span><span class="sxs-lookup"><span data-stu-id="6668c-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="6668c-113">Guide pratique pour dessiner une ligne avec des embouts de ligne</span><span class="sxs-lookup"><span data-stu-id="6668c-113">How to: Draw a Line with Line Caps</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="6668c-114">Décrit comment ajouter des majuscules lorsque vous dessinez une ligne.</span><span class="sxs-lookup"><span data-stu-id="6668c-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="6668c-115">Guide pratique pour joindre des lignes</span><span class="sxs-lookup"><span data-stu-id="6668c-115">How to: Join Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-join-lines.md)  
 <span data-ttu-id="6668c-116">Montre comment joindre deux lignes.</span><span class="sxs-lookup"><span data-stu-id="6668c-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="6668c-117">Guide pratique pour dessiner une ligne en pointillés personnalisée</span><span class="sxs-lookup"><span data-stu-id="6668c-117">How to: Draw a Custom Dashed Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="6668c-118">Décrit comment dessiner une ligne en pointillés.</span><span class="sxs-lookup"><span data-stu-id="6668c-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="6668c-119">Guide pratique pour dessiner une ligne remplie d'une texture</span><span class="sxs-lookup"><span data-stu-id="6668c-119">How to: Draw a Line Filled with a Texture</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="6668c-120">Explique comment dessiner une ligne remplie de texture.</span><span class="sxs-lookup"><span data-stu-id="6668c-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6668c-121">Référence</span><span class="sxs-lookup"><span data-stu-id="6668c-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="6668c-122">Décrit cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="6668c-122">Describes this class and has links to all its members.</span></span>
