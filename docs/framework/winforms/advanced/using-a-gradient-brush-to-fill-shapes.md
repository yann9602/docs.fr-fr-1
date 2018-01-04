---
title: "Utilisation d'un pinceau à dégradé pour remplir des formes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a84a68f9082d00559938c2710b6574690fa6ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a><span data-ttu-id="046e4-102">Utilisation d'un pinceau à dégradé pour remplir des formes</span><span class="sxs-lookup"><span data-stu-id="046e4-102">Using a Gradient Brush to Fill Shapes</span></span>
<span data-ttu-id="046e4-103">Vous pouvez utiliser un pinceau de dégradé pour remplir une forme avec une couleur.</span><span class="sxs-lookup"><span data-stu-id="046e4-103">You can use a gradient brush to fill a shape with a gradually changing color.</span></span> <span data-ttu-id="046e4-104">Par exemple, vous pouvez utiliser un dégradé horizontal pour remplir une forme avec une couleur qui change progressivement à mesure que vous déplacez le bord gauche de la forme sur le bord droit.</span><span class="sxs-lookup"><span data-stu-id="046e4-104">For example, you can use a horizontal gradient to fill a shape with color that changes gradually as you move from the left edge of the shape to the right edge.</span></span> <span data-ttu-id="046e4-105">Imaginez un rectangle avec un bord gauche noirs (représenté par les composants rouges, verts et bleus 0, 0, 0) et un bord droit de couleur rouge (représenté par 255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="046e4-105">Imagine a rectangle with a left edge that is black (represented by red, green, and blue components 0, 0, 0) and a right edge that is red (represented by 255, 0, 0).</span></span> <span data-ttu-id="046e4-106">Si le rectangle est 256 pixels de large, le composant rouge d’un pixel donné sera supérieure à la composante rouge du pixel situé à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="046e4-106">If the rectangle is 256 pixels wide, the red component of a given pixel will be one greater than the red component of the pixel to its left.</span></span> <span data-ttu-id="046e4-107">Le pixel le plus à gauche dans une ligne a des composants de couleur (0, 0, 0), le deuxième pixel a (1, 0, 0), le troisième pixel (2, 0, 0) et ainsi de suite jusqu'à ce que vous obtenez au pixel plus à droite, ce qui a RVB (255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="046e4-107">The leftmost pixel in a row has color components (0, 0, 0), the second pixel has (1, 0, 0), the third pixel has (2, 0, 0), and so on, until you get to the rightmost pixel, which has color components (255, 0, 0).</span></span> <span data-ttu-id="046e4-108">Ces valeurs de couleur interpolée composent le dégradé de couleur.</span><span class="sxs-lookup"><span data-stu-id="046e4-108">These interpolated color values make up the color gradient.</span></span>  
  
 <span data-ttu-id="046e4-109">Un dégradé linéaire change de couleur quand vous déplacez horizontalement, verticalement ou parallèlement à une ligne inclinée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="046e4-109">A linear gradient changes color as you move horizontally, vertically, or parallel to a specified slanted line.</span></span> <span data-ttu-id="046e4-110">Un dégradé de tracé change de couleur lorsque vous déplacez sur l’intérieur et la limite d’un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="046e4-110">A path gradient changes color as you move about the interior and boundary of a path.</span></span> <span data-ttu-id="046e4-111">Vous pouvez personnaliser les dégradés de chemin d’accès pour obtenir un large éventail d’effets.</span><span class="sxs-lookup"><span data-stu-id="046e4-111">You can customize path gradients to achieve a wide variety of effects.</span></span>  
  
 <span data-ttu-id="046e4-112">L’illustration suivante montre un rectangle rempli avec un pinceau de dégradé linéaire et une ellipse remplie avec un pinceau de dégradé du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="046e4-112">The following illustration shows a rectangle filled with a linear gradient brush and an ellipse filled with a path gradient brush.</span></span>  
  
 <span data-ttu-id="046e4-113">![Dégradé](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")</span><span class="sxs-lookup"><span data-stu-id="046e4-113">![Gradient](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="046e4-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="046e4-114">In This Section</span></span>  
 [<span data-ttu-id="046e4-115">Guide pratique pour créer un dégradé linéaire</span><span class="sxs-lookup"><span data-stu-id="046e4-115">How to: Create a Linear Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 <span data-ttu-id="046e4-116">Montre comment créer un dégradé linéaire en utilisant la <xref:System.Drawing.Drawing2D.LinearGradientBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="046e4-116">Shows how to create a linear gradient using the <xref:System.Drawing.Drawing2D.LinearGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="046e4-117">Guide pratique pour créer un dégradé de tracé</span><span class="sxs-lookup"><span data-stu-id="046e4-117">How to: Create a Path Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 <span data-ttu-id="046e4-118">Décrit comment créer un dégradé de chemin d’accès à l’aide la <xref:System.Drawing.Drawing2D.PathGradientBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="046e4-118">Describes how to create a path gradient using the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="046e4-119">Guide pratique pour appliquer une correction gamma à un dégradé</span><span class="sxs-lookup"><span data-stu-id="046e4-119">How to: Apply Gamma Correction to a Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 <span data-ttu-id="046e4-120">Explique comment utiliser la correction gamma avec un pinceau de dégradé.</span><span class="sxs-lookup"><span data-stu-id="046e4-120">Explains how to use gamma correction with a gradient brush.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="046e4-121">Référence</span><span class="sxs-lookup"><span data-stu-id="046e4-121">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="046e4-122">Contient une description de cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="046e4-122">Contains a description of this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="046e4-123">Contient une description de cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="046e4-123">Contains a description of this class and has links to all of its members.</span></span>
