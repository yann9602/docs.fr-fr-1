---
title: Transformations globales et locales
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
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 432402fefc6c958fbab0b1450a429d9b130b8239
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="global-and-local-transformations"></a><span data-ttu-id="f0c54-102">Transformations globales et locales</span><span class="sxs-lookup"><span data-stu-id="f0c54-102">Global and Local Transformations</span></span>
<span data-ttu-id="f0c54-103">Une transformation globale est une transformation qui s’applique à tous les éléments dessinés par une donnée <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="f0c54-103">A global transformation is a transformation that applies to every item drawn by a given <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="f0c54-104">En revanche, une transformation locale est une transformation qui s’applique à un élément spécifique doit être dessiné.</span><span class="sxs-lookup"><span data-stu-id="f0c54-104">In contrast, a local transformation is a transformation that applies to a specific item to be drawn.</span></span>  
  
## <a name="global-transformations"></a><span data-ttu-id="f0c54-105">Transformations globales</span><span class="sxs-lookup"><span data-stu-id="f0c54-105">Global Transformations</span></span>  
 <span data-ttu-id="f0c54-106">Pour créer une transformation globale, construisez un <xref:System.Drawing.Graphics> de l’objet et ensuite manipuler son <xref:System.Drawing.Graphics.Transform%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="f0c54-106">To create a global transformation, construct a <xref:System.Drawing.Graphics> object, and then manipulate its <xref:System.Drawing.Graphics.Transform%2A> property.</span></span> <span data-ttu-id="f0c54-107">Le <xref:System.Drawing.Graphics.Transform%2A> propriété est un <xref:System.Drawing.Drawing2D.Matrix> objet, elle peut contenir n’importe quelle séquence de transformations affines.</span><span class="sxs-lookup"><span data-stu-id="f0c54-107">The <xref:System.Drawing.Graphics.Transform%2A> property is a <xref:System.Drawing.Drawing2D.Matrix> object, so it can hold any sequence of affine transformations.</span></span> <span data-ttu-id="f0c54-108">La transformation stockée dans le <xref:System.Drawing.Graphics.Transform%2A> propriété est appelée la transformation universelle.</span><span class="sxs-lookup"><span data-stu-id="f0c54-108">The transformation stored in the <xref:System.Drawing.Graphics.Transform%2A> property is called the world transformation.</span></span> <span data-ttu-id="f0c54-109">Le <xref:System.Drawing.Graphics> classe fournit plusieurs méthodes pour créer une transformation universelle composite : <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, et <xref:System.Drawing.Graphics.TranslateTransform%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0c54-109">The <xref:System.Drawing.Graphics> class provides several methods for building up a composite world transformation: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, and <xref:System.Drawing.Graphics.TranslateTransform%2A>.</span></span> <span data-ttu-id="f0c54-110">L’exemple suivant dessine une ellipse à deux reprises : une fois avant la création d’une transformation universelle et une fois après.</span><span class="sxs-lookup"><span data-stu-id="f0c54-110">The following example draws an ellipse twice: once before creating a world transformation and once after.</span></span> <span data-ttu-id="f0c54-111">La transformation tout d’abord mettre à l’échelle par un facteur de 0,5 dans la direction y, puis convertit 50 unités dans la direction x et puis pivote de 30 degrés.</span><span class="sxs-lookup"><span data-stu-id="f0c54-111">The transformation first scales by a factor of 0.5 in the y direction, then translates 50 units in the x direction, and then rotates 30 degrees.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 <span data-ttu-id="f0c54-112">L’illustration suivante montre les matrices de cette transformation.</span><span class="sxs-lookup"><span data-stu-id="f0c54-112">The following illustration shows the matrices involved in the transformation.</span></span>  
  
 <span data-ttu-id="f0c54-113">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")</span><span class="sxs-lookup"><span data-stu-id="f0c54-113">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0c54-114">Dans l’exemple précédent, l’ellipse autour de l’origine du système de coordonnées, qui se trouve à l’angle supérieur gauche de la zone cliente.</span><span class="sxs-lookup"><span data-stu-id="f0c54-114">In the preceding example, the ellipse is rotated about the origin of the coordinate system, which is at the upper-left corner of the client area.</span></span> <span data-ttu-id="f0c54-115">Cela produit le même résultat que la rotation de l’ellipse autour de son propre centre.</span><span class="sxs-lookup"><span data-stu-id="f0c54-115">This produces a different result than rotating the ellipse about its own center.</span></span>  
  
## <a name="local-transformations"></a><span data-ttu-id="f0c54-116">Transformations locales</span><span class="sxs-lookup"><span data-stu-id="f0c54-116">Local Transformations</span></span>  
 <span data-ttu-id="f0c54-117">Une transformation locale s’applique à un élément spécifique doit être dessiné.</span><span class="sxs-lookup"><span data-stu-id="f0c54-117">A local transformation applies to a specific item to be drawn.</span></span> <span data-ttu-id="f0c54-118">Par exemple, un <xref:System.Drawing.Drawing2D.GraphicsPath> objet a un <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> méthode qui vous permet de transformer les points de données de ce chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="f0c54-118">For example, a <xref:System.Drawing.Drawing2D.GraphicsPath> object has a <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> method that allows you to transform the data points of that path.</span></span> <span data-ttu-id="f0c54-119">L’exemple suivant dessine un rectangle sans transformation et un chemin d’accès avec une transformation de rotation.</span><span class="sxs-lookup"><span data-stu-id="f0c54-119">The following example draws a rectangle with no transformation and a path with a rotation transformation.</span></span> <span data-ttu-id="f0c54-120">(En supposant qu’il n’existe aucune transformation universelle).</span><span class="sxs-lookup"><span data-stu-id="f0c54-120">(Assume that there is no world transformation.)</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 <span data-ttu-id="f0c54-121">Vous pouvez combiner la transformation universelle avec des transformations locales pour atteindre une variété de résultats.</span><span class="sxs-lookup"><span data-stu-id="f0c54-121">You can combine the world transformation with local transformations to achieve a variety of results.</span></span> <span data-ttu-id="f0c54-122">Par exemple, vous pouvez utiliser la transformation universelle pour réviser le système de coordonnées et transformations locales pour faire pivoter et mettre à l’échelle des objets dessinés sur le nouveau système de coordonnées.</span><span class="sxs-lookup"><span data-stu-id="f0c54-122">For example, you can use the world transformation to revise the coordinate system and use local transformations to rotate and scale objects drawn on the new coordinate system.</span></span>  
  
 <span data-ttu-id="f0c54-123">Supposons que vous souhaitiez un système de coordonnées qui a ses 200 pixels d’origine à partir du bord gauche de la zone cliente et à 150 pixels à partir du haut de la zone cliente.</span><span class="sxs-lookup"><span data-stu-id="f0c54-123">Suppose you want a coordinate system that has its origin 200 pixels from the left edge of the client area and 150 pixels from the top of the client area.</span></span> <span data-ttu-id="f0c54-124">En outre, supposons que vous souhaitez que l’unité de mesure le pixel, avec l’axe des x pointant vers la droite et l’axe des y pointant vers le haut.</span><span class="sxs-lookup"><span data-stu-id="f0c54-124">Furthermore, assume that you want the unit of measure to be the pixel, with the x-axis pointing to the right and the y-axis pointing up.</span></span> <span data-ttu-id="f0c54-125">Le système de coordonnées par défaut est l’axe des y pointant vers le bas, vous devez effectuer une réflexion sur l’axe horizontal.</span><span class="sxs-lookup"><span data-stu-id="f0c54-125">The default coordinate system has the y-axis pointing down, so you need to perform a reflection across the horizontal axis.</span></span> <span data-ttu-id="f0c54-126">L’illustration suivante montre la matrice de ce type de réflexion.</span><span class="sxs-lookup"><span data-stu-id="f0c54-126">The following illustration shows the matrix of such a reflection.</span></span>  
  
 <span data-ttu-id="f0c54-127">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")</span><span class="sxs-lookup"><span data-stu-id="f0c54-127">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")</span></span>  
  
 <span data-ttu-id="f0c54-128">Ensuite, supposons que vous devez effectuer une translation de 200 unités vers la droite et 150 unités vers le bas.</span><span class="sxs-lookup"><span data-stu-id="f0c54-128">Next, assume you need to perform a translation 200 units to the right and 150 units down.</span></span>  
  
 <span data-ttu-id="f0c54-129">L’exemple suivant établit le système de coordonnées vient d’être décrit en définissant la transformation universelle d’un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="f0c54-129">The following example establishes the coordinate system just described by setting the world transformation of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 <span data-ttu-id="f0c54-130">Le code suivant (placé à la fin de l’exemple précédent) crée un chemin d’accès qui se compose d’un rectangle avec son coin inférieur gauche à l’origine du nouveau système de coordonnées.</span><span class="sxs-lookup"><span data-stu-id="f0c54-130">The following code (placed at the end of the preceding example) creates a path that consists of a single rectangle with its lower-left corner at the origin of the new coordinate system.</span></span> <span data-ttu-id="f0c54-131">Le rectangle est rempli qu’une seule fois sans transformation locale et une fois avec une transformation locale.</span><span class="sxs-lookup"><span data-stu-id="f0c54-131">The rectangle is filled once with no local transformation and once with a local transformation.</span></span> <span data-ttu-id="f0c54-132">La transformation locale se compose d’une mise à l’échelle horizontale par un facteur de 2 suivie d’une rotation de 30 degrés.</span><span class="sxs-lookup"><span data-stu-id="f0c54-132">The local transformation consists of a horizontal scaling by a factor of 2 followed by a 30-degree rotation.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 <span data-ttu-id="f0c54-133">L’illustration suivante montre le nouveau système de coordonnées et les deux rectangles.</span><span class="sxs-lookup"><span data-stu-id="f0c54-133">The following illustration shows the new coordinate system and the two rectangles.</span></span>  
  
 <span data-ttu-id="f0c54-134">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")</span><span class="sxs-lookup"><span data-stu-id="f0c54-134">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c54-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0c54-135">See Also</span></span>  
 [<span data-ttu-id="f0c54-136">Systèmes de coordonnées et transformations</span><span class="sxs-lookup"><span data-stu-id="f0c54-136">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="f0c54-137">Utilisation des transformations dans GDI+ managé</span><span class="sxs-lookup"><span data-stu-id="f0c54-137">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
