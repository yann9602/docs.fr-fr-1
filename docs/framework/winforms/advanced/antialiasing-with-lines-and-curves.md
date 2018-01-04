---
title: "Anticrénelage avec des lignes et des courbes"
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
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8552f185a93b688555dbcfab3da9d28d9bfde6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="antialiasing-with-lines-and-curves"></a><span data-ttu-id="329cd-102">Anticrénelage avec des lignes et des courbes</span><span class="sxs-lookup"><span data-stu-id="329cd-102">Antialiasing with Lines and Curves</span></span>
<span data-ttu-id="329cd-103">Lorsque vous utilisez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pour dessiner une ligne, vous fournissez le point de départ et le point de fin de la ligne, mais il est inutile de fournir des informations sur les pixels individuels sur la ligne.</span><span class="sxs-lookup"><span data-stu-id="329cd-103">When you use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to draw a line, you provide the starting point and ending point of the line, but you do not have to provide any information about the individual pixels on the line.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="329cd-104">fonctionne en association avec le logiciel de pilote d’affichage pour déterminer quels pixels seront activées pour afficher la ligne sur un périphérique d’affichage particulier.</span><span class="sxs-lookup"><span data-stu-id="329cd-104"> works in conjunction with the display driver software to determine which pixels will be turned on to show the line on a particular display device.</span></span>  
  
## <a name="aliasing"></a><span data-ttu-id="329cd-105">Utilisation d’alias</span><span class="sxs-lookup"><span data-stu-id="329cd-105">Aliasing</span></span>  
 <span data-ttu-id="329cd-106">Envisagez la ligne droite rouge qui va du point (4, 2) au point (16, 10).</span><span class="sxs-lookup"><span data-stu-id="329cd-106">Consider the straight red line that goes from the point (4, 2) to the point (16, 10).</span></span> <span data-ttu-id="329cd-107">Supposons que le système de coordonnées a son origine dans le coin supérieur gauche et que l’unité de mesure est le pixel.</span><span class="sxs-lookup"><span data-stu-id="329cd-107">Assume the coordinate system has its origin in the upper-left corner and that the unit of measure is the pixel.</span></span> <span data-ttu-id="329cd-108">Supposons également que l’axe des x point vers la droite et les points de l’axe des y vers le bas.</span><span class="sxs-lookup"><span data-stu-id="329cd-108">Also assume that the x-axis points to the right and the y-axis points down.</span></span> <span data-ttu-id="329cd-109">L’illustration suivante montre une vue agrandie de la ligne rouge dessinée sur un arrière-plan multicolore.</span><span class="sxs-lookup"><span data-stu-id="329cd-109">The following illustration shows an enlarged view of the red line drawn on a multicolored background.</span></span>  
  
 <span data-ttu-id="329cd-110">![Ligne, sans anticrénelage](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span><span class="sxs-lookup"><span data-stu-id="329cd-110">![Line, no antialiasing](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span></span>  
  
 <span data-ttu-id="329cd-111">Les pixels rouges utilisés pour rendre la ligne sont opaques.</span><span class="sxs-lookup"><span data-stu-id="329cd-111">The red pixels used to render the line are opaque.</span></span> <span data-ttu-id="329cd-112">Il n’y a aucun pixel partiellement transparent dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="329cd-112">There are no partially transparent pixels in the line.</span></span> <span data-ttu-id="329cd-113">Ce type de rendu donne une apparence en escalier à la ligne et la ligne ressemble escalier.</span><span class="sxs-lookup"><span data-stu-id="329cd-113">This type of line rendering gives the line a jagged appearance, and the line looks somewhat like a staircase.</span></span> <span data-ttu-id="329cd-114">Cette technique qui représente une ligne comme un escalier est appelée crénelage ; l’escalier est un alias pour la ligne théorique.</span><span class="sxs-lookup"><span data-stu-id="329cd-114">This technique of representing a line with a staircase is called aliasing; the staircase is an alias for the theoretical line.</span></span>  
  
## <a name="antialiasing"></a><span data-ttu-id="329cd-115">anticrénelage</span><span class="sxs-lookup"><span data-stu-id="329cd-115">Antialiasing</span></span>  
 <span data-ttu-id="329cd-116">Une technique plus sophistiquée pour le rendu d’une ligne implique l’utilisation de pixels partiellement transparents et pixels opaques.</span><span class="sxs-lookup"><span data-stu-id="329cd-116">A more sophisticated technique for rendering a line involves using partially transparent pixels along with opaque pixels.</span></span> <span data-ttu-id="329cd-117">Pixels sont définies sur rouge pur, ou un mélange de rouge et de la couleur d’arrière-plan, en fonction de leur proximité qu’ils sont à la ligne.</span><span class="sxs-lookup"><span data-stu-id="329cd-117">Pixels are set to pure red, or to some blend of red and the background color, depending on how close they are to the line.</span></span> <span data-ttu-id="329cd-118">Ce type de rendu est appelé anticrénelage et donne une ligne le œil humain perçoit plus lisse.</span><span class="sxs-lookup"><span data-stu-id="329cd-118">This type of rendering is called antialiasing and results in a line that the human eye perceives as more smooth.</span></span> <span data-ttu-id="329cd-119">L’illustration suivante montre comment certains pixels sont fusionnés avec l’arrière-plan pour produire une ligne non crénelé.</span><span class="sxs-lookup"><span data-stu-id="329cd-119">The following illustration shows how certain pixels are blended with the background to produce an antialiased line.</span></span>  
  
 <span data-ttu-id="329cd-120">![Anticrénelage d’une ligne](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span><span class="sxs-lookup"><span data-stu-id="329cd-120">![Antialiasing a Line](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span></span>  
  
 <span data-ttu-id="329cd-121">L’anticrénelage, également appelé lissage, peut également être appliqué aux courbes.</span><span class="sxs-lookup"><span data-stu-id="329cd-121">Antialiasing, also called smoothing, can also be applied to curves.</span></span> <span data-ttu-id="329cd-122">L’illustration suivante montre une vue agrandie d’une ellipse lissée.</span><span class="sxs-lookup"><span data-stu-id="329cd-122">The following illustration shows an enlarged view of a smoothed ellipse.</span></span>  
  
 <span data-ttu-id="329cd-123">![Anticrénelage de courbes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span><span class="sxs-lookup"><span data-stu-id="329cd-123">![Antialiasing Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span></span>  
  
 <span data-ttu-id="329cd-124">L’illustration suivante montre la même ellipse en taille réelle, sans anticrénelage et avec anticrénelage.</span><span class="sxs-lookup"><span data-stu-id="329cd-124">The following illustration shows the same ellipse in its actual size, once without antialiasing and once with antialiasing.</span></span>  
  
 <span data-ttu-id="329cd-125">![Exemple d’anticrénelage](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span><span class="sxs-lookup"><span data-stu-id="329cd-125">![Antialiasing example](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span></span>  
  
 <span data-ttu-id="329cd-126">Pour dessiner des lignes et des courbes qui utilisent l’anticrénelage, créez une instance de la <xref:System.Drawing.Graphics> puis définissez son <xref:System.Drawing.Graphics.SmoothingMode%2A> propriété <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> ou <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span><span class="sxs-lookup"><span data-stu-id="329cd-126">To draw lines and curves that use antialiasing, create an instance of the <xref:System.Drawing.Graphics> class and set its <xref:System.Drawing.Graphics.SmoothingMode%2A> property to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> or <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span></span> <span data-ttu-id="329cd-127">Appelez ensuite l’une des méthodes de dessin de ce même <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="329cd-127">Then call one of the drawing methods of that same <xref:System.Drawing.Graphics> class.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a><span data-ttu-id="329cd-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="329cd-128">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>  
 [<span data-ttu-id="329cd-129">Lignes, courbes et formes</span><span class="sxs-lookup"><span data-stu-id="329cd-129">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="329cd-130">Guide pratique pour utiliser l‘anticrénelage avec du texte</span><span class="sxs-lookup"><span data-stu-id="329cd-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)
