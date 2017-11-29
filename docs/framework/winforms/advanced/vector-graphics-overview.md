---
title: Vue d'ensemble des graphismes vectoriels
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
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7bb3247f531a0dac83657e118fb53ebaf708ec9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="vector-graphics-overview"></a><span data-ttu-id="ede1f-102">Vue d'ensemble des graphismes vectoriels</span><span class="sxs-lookup"><span data-stu-id="ede1f-102">Vector Graphics Overview</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="ede1f-103">Dessine des lignes, rectangles et autres formes sur un système de coordonnées.</span><span class="sxs-lookup"><span data-stu-id="ede1f-103"> draws lines, rectangles, and other shapes on a coordinate system.</span></span> <span data-ttu-id="ede1f-104">Vous pouvez choisir parmi une variété de systèmes de coordonnées, mais le système de coordonnées par défaut a l’origine dans le coin supérieur gauche avec l’axe des x pointant vers la droite et l’axe des y pointant vers le bas.</span><span class="sxs-lookup"><span data-stu-id="ede1f-104">You can choose from a variety of coordinate systems, but the default coordinate system has the origin in the upper-left corner with the x-axis pointing to the right and the y-axis pointing down.</span></span> <span data-ttu-id="ede1f-105">L’unité de mesure dans le système de coordonnées par défaut est le pixel.</span><span class="sxs-lookup"><span data-stu-id="ede1f-105">The unit of measure in the default coordinate system is the pixel.</span></span>  
  
## <a name="the-building-blocks-of-gdi"></a><span data-ttu-id="ede1f-106">Les blocs de construction de GDI +</span><span class="sxs-lookup"><span data-stu-id="ede1f-106">The Building Blocks of GDI+</span></span>  
 <span data-ttu-id="ede1f-107">![Graphique vectoriel](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.gif "AboutGdip02_Art01")</span><span class="sxs-lookup"><span data-stu-id="ede1f-107">![Vector graphic](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.gif "AboutGdip02_Art01")</span></span>  
  
 <span data-ttu-id="ede1f-108">Un moniteur d’ordinateur crée son affichage sur un tableau rectangulaire de points appelés pixels.</span><span class="sxs-lookup"><span data-stu-id="ede1f-108">A computer monitor creates its display on a rectangular array of dots called picture elements or pixels.</span></span> <span data-ttu-id="ede1f-109">Le nombre de pixels qui apparaissent sur l’écran varie d’un moniteur à l’autre, et le nombre de pixels qui apparaissent sur un seul écran peut généralement être configuré dans une certaine mesure par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ede1f-109">The number of pixels that appear on the screen varies from one monitor to the next, and the number of pixels that appear on an individual monitor can usually be configured to some extent by the user.</span></span>  
  
 <span data-ttu-id="ede1f-110">![Graphique vectoriel](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.gif "AboutGdip02_Art02")</span><span class="sxs-lookup"><span data-stu-id="ede1f-110">![Vector graphic](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.gif "AboutGdip02_Art02")</span></span>  
  
 <span data-ttu-id="ede1f-111">Lorsque vous utilisez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pour dessiner une ligne, un rectangle ou une courbe, vous fournissez des informations essentielles sur l’élément à dessiner.</span><span class="sxs-lookup"><span data-stu-id="ede1f-111">When you use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to draw a line, rectangle, or curve, you provide certain key information about the item to be drawn.</span></span> <span data-ttu-id="ede1f-112">Par exemple, vous pouvez spécifier une ligne en fournissant deux points, et vous pouvez spécifier un rectangle en fournissant un point, une hauteur et une largeur.</span><span class="sxs-lookup"><span data-stu-id="ede1f-112">For example, you can specify a line by providing two points, and you can specify a rectangle by providing a point, a height, and a width.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="ede1f-113">fonctionne en association avec le logiciel de pilote d’affichage pour déterminer quels pixels doivent être activées pour afficher la ligne, un rectangle ou une courbe.</span><span class="sxs-lookup"><span data-stu-id="ede1f-113"> works in conjunction with the display driver software to determine which pixels must be turned on to show the line, rectangle, or curve.</span></span> <span data-ttu-id="ede1f-114">L’illustration suivante montre les pixels qui sont sous tension pour afficher une ligne à partir du point (4, 2) au point (12, 8).</span><span class="sxs-lookup"><span data-stu-id="ede1f-114">The following illustration shows the pixels that are turned on to display a line from the point (4, 2) to the point (12, 8).</span></span>  
  
 <span data-ttu-id="ede1f-115">![Graphique vectoriel](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.gif "AboutGdip02_Art03")</span><span class="sxs-lookup"><span data-stu-id="ede1f-115">![Vector graphic](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.gif "AboutGdip02_Art03")</span></span>  
  
 <span data-ttu-id="ede1f-116">Au fil du temps, certains blocs de construction ayant prouvé les plus utiles pour la création d’images à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="ede1f-116">Over time, certain basic building blocks have proven to be the most useful for creating two-dimensional pictures.</span></span> <span data-ttu-id="ede1f-117">Ces blocs de construction, qui sont toutes prises en charge par [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], figurent dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="ede1f-117">These building blocks, which are all supported by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], are given in the following list:</span></span>  
  
-   <span data-ttu-id="ede1f-118">Lignes</span><span class="sxs-lookup"><span data-stu-id="ede1f-118">Lines</span></span>  
  
-   <span data-ttu-id="ede1f-119">Rectangles</span><span class="sxs-lookup"><span data-stu-id="ede1f-119">Rectangles</span></span>  
  
-   <span data-ttu-id="ede1f-120">Points de suspension</span><span class="sxs-lookup"><span data-stu-id="ede1f-120">Ellipses</span></span>  
  
-   <span data-ttu-id="ede1f-121">Arcs de cercle</span><span class="sxs-lookup"><span data-stu-id="ede1f-121">Arcs</span></span>  
  
-   <span data-ttu-id="ede1f-122">Polygones</span><span class="sxs-lookup"><span data-stu-id="ede1f-122">Polygons</span></span>  
  
-   <span data-ttu-id="ede1f-123">Splines cardinales</span><span class="sxs-lookup"><span data-stu-id="ede1f-123">Cardinal splines</span></span>  
  
-   <span data-ttu-id="ede1f-124">splines de Bézier</span><span class="sxs-lookup"><span data-stu-id="ede1f-124">Bezier splines</span></span>  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a><span data-ttu-id="ede1f-125">Méthodes de dessin à un objet Graphics</span><span class="sxs-lookup"><span data-stu-id="ede1f-125">Methods For Drawing with a Graphics Object</span></span>  
 <span data-ttu-id="ede1f-126">Le <xref:System.Drawing.Graphics> classe dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit les méthodes suivantes pour dessiner les éléments de la liste précédente : <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (pour les splines cardinales), et <xref:System.Drawing.Graphics.DrawBezier%2A>.</span><span class="sxs-lookup"><span data-stu-id="ede1f-126">The <xref:System.Drawing.Graphics> class in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides the following methods for drawing the items in the previous list: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (for cardinal splines), and <xref:System.Drawing.Graphics.DrawBezier%2A>.</span></span> <span data-ttu-id="ede1f-127">Chacune de ces méthodes est surchargée ; Autrement dit, chaque méthode prend en charge plusieurs listes de paramètres différentes.</span><span class="sxs-lookup"><span data-stu-id="ede1f-127">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="ede1f-128">Par exemple, une variante de la <xref:System.Drawing.Graphics.DrawLine%2A> méthode reçoit un <xref:System.Drawing.Pen> objet et quatre entiers lors d’une autre variante de la <xref:System.Drawing.Graphics.DrawLine%2A> méthode reçoit un <xref:System.Drawing.Pen> objet et deux <xref:System.Drawing.Point> objets.</span><span class="sxs-lookup"><span data-stu-id="ede1f-128">For example, one variation of the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object and four integers, while another variation of the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object and two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="ede1f-129">Les méthodes pour dessiner des lignes, des rectangles et des splines de Bézier ont des méthodes au pluriel qui dessinent plusieurs éléments dans un seul appel : <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, et <xref:System.Drawing.Graphics.DrawBeziers%2A>.</span><span class="sxs-lookup"><span data-stu-id="ede1f-129">The methods for drawing lines, rectangles, and Bézier splines have plural companion methods that draw several items in a single call: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, and <xref:System.Drawing.Graphics.DrawBeziers%2A>.</span></span> <span data-ttu-id="ede1f-130">En outre, le <xref:System.Drawing.Graphics.DrawCurve%2A> méthode a une méthode d’accompagnement, <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, que le point d’une courbe en vous connectant le point de fin de la courbe de début se ferme.</span><span class="sxs-lookup"><span data-stu-id="ede1f-130">Also, the <xref:System.Drawing.Graphics.DrawCurve%2A> method has a companion method, <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, that closes a curve by connecting the ending point of the curve to the starting point.</span></span>  
  
 <span data-ttu-id="ede1f-131">Toutes les méthodes de dessin de le <xref:System.Drawing.Graphics> classe fonctionnent conjointement avec un <xref:System.Drawing.Pen> objet.</span><span class="sxs-lookup"><span data-stu-id="ede1f-131">All of the drawing methods of the <xref:System.Drawing.Graphics> class work in conjunction with a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="ede1f-132">Pour dessiner quoi que ce soit, vous devez créer au moins deux objets : un <xref:System.Drawing.Graphics> objet et un <xref:System.Drawing.Pen> objet.</span><span class="sxs-lookup"><span data-stu-id="ede1f-132">To draw anything, you must create at least two objects: a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="ede1f-133">Le <xref:System.Drawing.Pen> objet stocke des attributs, tels que la largeur de ligne et de couleur, de l’élément à dessiner.</span><span class="sxs-lookup"><span data-stu-id="ede1f-133">The <xref:System.Drawing.Pen> object stores attributes, such as line width and color, of the item to be drawn.</span></span> <span data-ttu-id="ede1f-134">Le <xref:System.Drawing.Pen> objet est passé comme argument à la méthode de dessin.</span><span class="sxs-lookup"><span data-stu-id="ede1f-134">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the drawing method.</span></span> <span data-ttu-id="ede1f-135">Par exemple, une variante de la <xref:System.Drawing.Graphics.DrawLine%2A> méthode reçoit un <xref:System.Drawing.Pen> objet et quatre entiers comme indiqué dans l’exemple suivant, qui dessine un rectangle avec une largeur de 100 et une hauteur de 50 un coin supérieur gauche de (20, 10) :</span><span class="sxs-lookup"><span data-stu-id="ede1f-135">For example, one variation of the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object and four integers as shown in the following example, which draws a rectangle with a width of 100, a height of 50 and an upper-left corner of (20, 10):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="ede1f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ede1f-136">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="ede1f-137">Lignes, courbes et formes</span><span class="sxs-lookup"><span data-stu-id="ede1f-137">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="ede1f-138">Guide pratique pour créer des objets graphiques pour le dessin</span><span class="sxs-lookup"><span data-stu-id="ede1f-138">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
