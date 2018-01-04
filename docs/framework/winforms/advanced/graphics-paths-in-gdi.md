---
title: "Tracés graphiques dans GDI+"
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
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 022a591a1d646b154c2bd59a2f2ab21b78b9dbda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-paths-in-gdi"></a><span data-ttu-id="fd9ea-102">Tracés graphiques dans GDI+</span><span class="sxs-lookup"><span data-stu-id="fd9ea-102">Graphics Paths in GDI+</span></span>
<span data-ttu-id="fd9ea-103">Chemins d’accès sont formées en combinant des lignes, des rectangles et des courbes simples.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-103">Paths are formed by combining lines, rectangles, and simple curves.</span></span> <span data-ttu-id="fd9ea-104">Rappelez la [vue d’ensemble des graphiques vectoriels](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) que les blocs de construction de base suivantes se sont avérés les plus utiles pour dessiner des images :</span><span class="sxs-lookup"><span data-stu-id="fd9ea-104">Recall from the [Vector Graphics Overview](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) that the following basic building blocks have proven to be the most useful for drawing pictures:</span></span>  
  
-   <span data-ttu-id="fd9ea-105">Lignes</span><span class="sxs-lookup"><span data-stu-id="fd9ea-105">Lines</span></span>  
  
-   <span data-ttu-id="fd9ea-106">Rectangles</span><span class="sxs-lookup"><span data-stu-id="fd9ea-106">Rectangles</span></span>  
  
-   <span data-ttu-id="fd9ea-107">Points de suspension</span><span class="sxs-lookup"><span data-stu-id="fd9ea-107">Ellipses</span></span>  
  
-   <span data-ttu-id="fd9ea-108">Arcs de cercle</span><span class="sxs-lookup"><span data-stu-id="fd9ea-108">Arcs</span></span>  
  
-   <span data-ttu-id="fd9ea-109">Polygones</span><span class="sxs-lookup"><span data-stu-id="fd9ea-109">Polygons</span></span>  
  
-   <span data-ttu-id="fd9ea-110">Splines cardinales</span><span class="sxs-lookup"><span data-stu-id="fd9ea-110">Cardinal splines</span></span>  
  
-   <span data-ttu-id="fd9ea-111">Splines de Bézier</span><span class="sxs-lookup"><span data-stu-id="fd9ea-111">Bézier splines</span></span>  
  
 <span data-ttu-id="fd9ea-112">Dans GDI +, le <xref:System.Drawing.Drawing2D.GraphicsPath> objet vous permet de collecter une séquence de ces blocs de construction en une seule unité.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-112">In GDI+, the <xref:System.Drawing.Drawing2D.GraphicsPath> object allows you to collect a sequence of these building blocks into a single unit.</span></span> <span data-ttu-id="fd9ea-113">L’ensemble de lignes, rectangles, polygones et courbes peut ensuite être dessinée avec un seul appel à la <xref:System.Drawing.Graphics.DrawPath%2A> méthode de la <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-113">The entire sequence of lines, rectangles, polygons, and curves can then be drawn with one call to the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="fd9ea-114">L’illustration suivante montre un chemin d’accès créé en combinant une ligne, un arc, une spline de Bézier et une spline cardinale.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-114">The following illustration shows a path created by combining a line, an arc, a Bézier spline, and a cardinal spline.</span></span>  
  
 <span data-ttu-id="fd9ea-115">![Chemin d’accès](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span><span class="sxs-lookup"><span data-stu-id="fd9ea-115">![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span></span>  
  
## <a name="using-a-path"></a><span data-ttu-id="fd9ea-116">À l’aide d’un chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="fd9ea-116">Using a Path</span></span>  
 <span data-ttu-id="fd9ea-117">Le <xref:System.Drawing.Drawing2D.GraphicsPath> classe fournit les méthodes suivantes pour créer une séquence d’éléments à dessiner : <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (pour les splines cardinales) et <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-117">The <xref:System.Drawing.Drawing2D.GraphicsPath> class provides the following methods for creating a sequence of items to be drawn: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (for cardinal splines), and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span></span> <span data-ttu-id="fd9ea-118">Chacune de ces méthodes est surchargée ; Autrement dit, chaque méthode prend en charge plusieurs listes de paramètres différentes.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-118">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="fd9ea-119">Par exemple, une variante de la <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> reçoit quatre entiers et une autre variante de la <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> méthode reçoit deux <xref:System.Drawing.Point> objets.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-119">For example, one variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives four integers, and another variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="fd9ea-120">Les méthodes d’ajout des lignes, des rectangles et des splines de Bézier à un chemin d’accès ont des méthodes au pluriel qui ajoutent plusieurs éléments pour le chemin d’accès dans un seul appel : <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, et <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-120">The methods for adding lines, rectangles, and Bézier splines to a path have plural companion methods that add several items to the path in a single call: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span></span> <span data-ttu-id="fd9ea-121">En outre, le <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> et <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> méthodes ont des méthodes, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> et <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, qui ajoutent une courbe fermée ou un graphique à secteurs pour le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-121">Also, the <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> methods have companion methods, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, that add a closed curve or pie to the path.</span></span>  
  
 <span data-ttu-id="fd9ea-122">Pour dessiner un tracé, vous avez besoin une <xref:System.Drawing.Graphics> objet, un <xref:System.Drawing.Pen> objet et un <xref:System.Drawing.Drawing2D.GraphicsPath> objet.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-122">To draw a path, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="fd9ea-123">Le <xref:System.Drawing.Graphics> objet fournit les <xref:System.Drawing.Graphics.DrawPath%2A> (méthode) et le <xref:System.Drawing.Pen> objet stocke des attributs, tels que la largeur et la couleur, de la ligne utilisée pour afficher le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-123">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPath%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the path.</span></span> <span data-ttu-id="fd9ea-124">Le <xref:System.Drawing.Drawing2D.GraphicsPath> objet stocke la séquence de lignes et des courbes qui composent le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-124">The <xref:System.Drawing.Drawing2D.GraphicsPath> object stores the sequence of lines and curves that make up the path.</span></span> <span data-ttu-id="fd9ea-125">Le <xref:System.Drawing.Pen> objet et la <xref:System.Drawing.Drawing2D.GraphicsPath> objet sont passés comme arguments à la <xref:System.Drawing.Graphics.DrawPath%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="fd9ea-125">The <xref:System.Drawing.Pen> object and the <xref:System.Drawing.Drawing2D.GraphicsPath> object are passed as arguments to the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="fd9ea-126">L’exemple suivant dessine un chemin d’accès qui se compose d’une ligne, une ellipse et d’une spline de Bézier :</span><span class="sxs-lookup"><span data-stu-id="fd9ea-126">The following example draws a path that consists of a line, an ellipse, and a Bézier spline:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 <span data-ttu-id="fd9ea-127">L’illustration suivante montre le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-127">The following illustration shows the path.</span></span>  
  
 <span data-ttu-id="fd9ea-128">![Chemin d’accès](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span><span class="sxs-lookup"><span data-stu-id="fd9ea-128">![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span></span>  
  
 <span data-ttu-id="fd9ea-129">Outre l’ajout des lignes, des rectangles et des courbes à un chemin d’accès, vous pouvez ajouter des chemins d’accès à un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-129">In addition to adding lines, rectangles, and curves to a path, you can add paths to a path.</span></span> <span data-ttu-id="fd9ea-130">Cela vous permet de combiner des tracés existants pour former des chemins d’accès volumineuses et complexes.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-130">This allows you to combine existing paths to form large, complex paths.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 <span data-ttu-id="fd9ea-131">Il existe deux autres éléments que vous pouvez ajouter à un chemin d’accès : chaînes et des secteurs.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-131">There are two other items you can add to a path: strings and pies.</span></span> <span data-ttu-id="fd9ea-132">Un graphique à secteurs est une partie de l’intérieur d’une ellipse.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-132">A pie is a portion of the interior of an ellipse.</span></span> <span data-ttu-id="fd9ea-133">L’exemple suivant crée un chemin d’accès à partir d’un arc, une spline cardinale, une chaîne et un graphique en secteurs :</span><span class="sxs-lookup"><span data-stu-id="fd9ea-133">The following example creates a path from an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 <span data-ttu-id="fd9ea-134">L’illustration suivante montre le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-134">The following illustration shows the path.</span></span> <span data-ttu-id="fd9ea-135">Notez qu’un chemin d’accès ne dispose pas être connectés ; l’arc, une spline cardinale, chaîne et à secteurs sont séparés.</span><span class="sxs-lookup"><span data-stu-id="fd9ea-135">Note that a path does not have to be connected; the arc, cardinal spline, string, and pie are separated.</span></span>  
  
 <span data-ttu-id="fd9ea-136">![Chemins d’accès](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span><span class="sxs-lookup"><span data-stu-id="fd9ea-136">![Paths](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd9ea-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd9ea-137">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [<span data-ttu-id="fd9ea-138">Lignes, courbes et formes</span><span class="sxs-lookup"><span data-stu-id="fd9ea-138">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="fd9ea-139">Guide pratique pour créer des objets graphiques pour le dessin</span><span class="sxs-lookup"><span data-stu-id="fd9ea-139">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="fd9ea-140">Génération et dessin de tracés</span><span class="sxs-lookup"><span data-stu-id="fd9ea-140">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
