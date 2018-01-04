---
title: "Types de systèmes de coordonnées"
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
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 287b1c9eddef882041d9e4eac44a06190f3585a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="bc114-102">Types de systèmes de coordonnées</span><span class="sxs-lookup"><span data-stu-id="bc114-102">Types of Coordinate Systems</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="bc114-103">utilise trois espaces de coordonnées : monde, page et périphérique.</span><span class="sxs-lookup"><span data-stu-id="bc114-103"> uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="bc114-104">Coordonnées universelles sont les coordonnées utilisées pour modéliser un environnement graphique particulier et les coordonnées que vous passez aux méthodes dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bc114-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="bc114-105">Les coordonnées de page font référence au système de coordonnées utilisé par une surface de dessin, comme un formulaire ou un contrôle.</span><span class="sxs-lookup"><span data-stu-id="bc114-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="bc114-106">Coordonnées de périphérique sont les coordonnées utilisées par le périphérique physique qui est dessiné, tel qu’un écran ou une feuille de papier.</span><span class="sxs-lookup"><span data-stu-id="bc114-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="bc114-107">Lorsque vous effectuez l’appel `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, les points que vous passez à la <xref:System.Drawing.Graphics.DrawLine%2A> méthode —`(0, 0)` et `(160, 80)`, se trouvent dans l’espace de coordonnées universelles.</span><span class="sxs-lookup"><span data-stu-id="bc114-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="bc114-108">Avant de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] peut dessiner la ligne à l’écran, les coordonnées passent par une séquence de transformations.</span><span class="sxs-lookup"><span data-stu-id="bc114-108">Before [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="bc114-109">Une transformation, appelée la transformation universelle, convertit les coordonnées universelles en coordonnées de page, et une autre transformation, appelée la transformation de page, convertit les coordonnées de page en coordonnées de périphérique.</span><span class="sxs-lookup"><span data-stu-id="bc114-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="bc114-110">Les transformations et les systèmes de coordonnées</span><span class="sxs-lookup"><span data-stu-id="bc114-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="bc114-111">Supposons que vous souhaitez travailler avec un système de coordonnées qui a son origine dans le corps de la zone cliente plutôt que dans le coin supérieur gauche.</span><span class="sxs-lookup"><span data-stu-id="bc114-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="bc114-112">Imaginons, par exemple, que vous vouliez d’origine située à 100 pixels du bord gauche de la zone cliente et à 50 pixels à partir du haut de la zone cliente.</span><span class="sxs-lookup"><span data-stu-id="bc114-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="bc114-113">L’illustration suivante montre un système de coordonnées.</span><span class="sxs-lookup"><span data-stu-id="bc114-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="bc114-114">![Système de coordonnées](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="bc114-114">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="bc114-115">Lorsque vous effectuez l’appel `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, vous obtenez la ligne représentée dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="bc114-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="bc114-116">![Système de coordonnées](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="bc114-116">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="bc114-117">Les coordonnées des points de terminaison de la ligne dans les trois espaces de coordonnées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bc114-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc114-118">World</span><span class="sxs-lookup"><span data-stu-id="bc114-118">World</span></span>|<span data-ttu-id="bc114-119">(0, 0) à (160, 80)</span><span class="sxs-lookup"><span data-stu-id="bc114-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="bc114-120">Page</span><span class="sxs-lookup"><span data-stu-id="bc114-120">Page</span></span>|<span data-ttu-id="bc114-121">(100, 50) à (260, 130)</span><span class="sxs-lookup"><span data-stu-id="bc114-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="bc114-122">Appareil</span><span class="sxs-lookup"><span data-stu-id="bc114-122">Device</span></span>|<span data-ttu-id="bc114-123">(100, 50) à (260, 130)</span><span class="sxs-lookup"><span data-stu-id="bc114-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="bc114-124">Notez que l’espace de coordonnées de page a son origine dans le coin supérieur gauche de la zone cliente ; Ce sera toujours le cas.</span><span class="sxs-lookup"><span data-stu-id="bc114-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="bc114-125">Notez également que, car l’unité de mesure est le pixel, les coordonnées de périphérique sont les mêmes que les coordonnées de page.</span><span class="sxs-lookup"><span data-stu-id="bc114-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="bc114-126">Si vous définissez l’unité de mesure avec une valeur différente de pixels (par exemple, pouces), puis les coordonnées de périphérique sera différentes de coordonnées de la page.</span><span class="sxs-lookup"><span data-stu-id="bc114-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="bc114-127">La transformation universelle, qui mappe les coordonnées universelles aux coordonnées de page, est conservée dans le <xref:System.Drawing.Graphics.Transform%2A> propriété de la <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="bc114-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="bc114-128">Dans l’exemple précédent, la transformation universelle est une translation de 100 unités dans la direction x et de 50 unités sur l’axe y.</span><span class="sxs-lookup"><span data-stu-id="bc114-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="bc114-129">L’exemple suivant définit la transformation universelle d’un <xref:System.Drawing.Graphics> de l’objet, puis l’utilise <xref:System.Drawing.Graphics> objet à dessiner la ligne illustrée dans la figure précédente :</span><span class="sxs-lookup"><span data-stu-id="bc114-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="bc114-130">La transformation de page mappe les coordonnées de page aux coordonnées de périphérique.</span><span class="sxs-lookup"><span data-stu-id="bc114-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="bc114-131">Le <xref:System.Drawing.Graphics> classe fournit le <xref:System.Drawing.Graphics.PageUnit%2A> et <xref:System.Drawing.Graphics.PageScale%2A> propriétés pour la manipulation de la transformation de page.</span><span class="sxs-lookup"><span data-stu-id="bc114-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="bc114-132">Le <xref:System.Drawing.Graphics> classe fournit également deux propriétés en lecture seule, <xref:System.Drawing.Graphics.DpiX%2A> et <xref:System.Drawing.Graphics.DpiY%2A>, pour examiner les points par pouce du périphérique d’affichage horizontales et verticales.</span><span class="sxs-lookup"><span data-stu-id="bc114-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="bc114-133">Vous pouvez utiliser la <xref:System.Drawing.Graphics.PageUnit%2A> propriété de la <xref:System.Drawing.Graphics> classe pour spécifier une unité de mesure autre que le pixel.</span><span class="sxs-lookup"><span data-stu-id="bc114-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc114-134">Vous ne pouvez pas définir le <xref:System.Drawing.Graphics.PageUnit%2A> propriété <xref:System.Drawing.GraphicsUnit.World>, comme cela n’est pas une unité physique et provoquera une exception.</span><span class="sxs-lookup"><span data-stu-id="bc114-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="bc114-135">L’exemple suivant dessine une ligne à partir de (0, 0) à (2, 1), où le point (2, 1) est 2 pouces à droite et 1 pouce vers le bas à partir du point (0, 0) :</span><span class="sxs-lookup"><span data-stu-id="bc114-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  <span data-ttu-id="bc114-136">Si vous ne spécifiez la largeur du stylet lorsque vous construisez le stylet, l’exemple précédent Dessine une ligne d’un pouce de large.</span><span class="sxs-lookup"><span data-stu-id="bc114-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="bc114-137">Vous pouvez spécifier la largeur du stylet dans le deuxième argument de la <xref:System.Drawing.Pen> constructeur :</span><span class="sxs-lookup"><span data-stu-id="bc114-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="bc114-138">Si nous partons du principe que le périphérique d’affichage comporte 96 points par pouce dans la direction horizontale et 96 points par pouce dans le sens vertical, les points de terminaison de la ligne dans l’exemple précédent ont les coordonnées suivantes dans les trois espaces de coordonnées :</span><span class="sxs-lookup"><span data-stu-id="bc114-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc114-139">World</span><span class="sxs-lookup"><span data-stu-id="bc114-139">World</span></span>|<span data-ttu-id="bc114-140">(0, 0) à (2, 1)</span><span class="sxs-lookup"><span data-stu-id="bc114-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="bc114-141">Page</span><span class="sxs-lookup"><span data-stu-id="bc114-141">Page</span></span>|<span data-ttu-id="bc114-142">(0, 0) à (2, 1)</span><span class="sxs-lookup"><span data-stu-id="bc114-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="bc114-143">Appareil</span><span class="sxs-lookup"><span data-stu-id="bc114-143">Device</span></span>|<span data-ttu-id="bc114-144">(0, 0, à (192, 96)</span><span class="sxs-lookup"><span data-stu-id="bc114-144">(0, 0, to (192, 96)</span></span>|  
  
 <span data-ttu-id="bc114-145">Notez que l’origine de l’espace de coordonnées universelles étant à l’angle supérieur gauche de la zone cliente, les coordonnées de page sont les mêmes que les coordonnées de monde.</span><span class="sxs-lookup"><span data-stu-id="bc114-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="bc114-146">Vous pouvez combiner les transformations universelles et de page pour obtenir divers effets.</span><span class="sxs-lookup"><span data-stu-id="bc114-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="bc114-147">Par exemple, supposons que vous souhaitez utiliser pouces comme unité de mesure et que vous souhaitez l’origine de votre système de coordonnées à 2 pouces du bord gauche de la zone cliente et le 1/2 pouce à partir du haut de la zone cliente.</span><span class="sxs-lookup"><span data-stu-id="bc114-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="bc114-148">L’exemple suivant définit les transformations universelles et de page d’un <xref:System.Drawing.Graphics> de l’objet, puis dessine une ligne à partir de (0, 0) à (2, 1) :</span><span class="sxs-lookup"><span data-stu-id="bc114-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="bc114-149">L’illustration suivante montre la ligne et le système de coordonnées.</span><span class="sxs-lookup"><span data-stu-id="bc114-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="bc114-150">![Système de coordonnées](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="bc114-150">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="bc114-151">Si nous partons du principe que le périphérique d’affichage comporte 96 points par pouce dans la direction horizontale et 96 points par pouce dans le sens vertical, les points de terminaison de la ligne dans l’exemple précédent ont les coordonnées suivantes dans les trois espaces de coordonnées :</span><span class="sxs-lookup"><span data-stu-id="bc114-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc114-152">World</span><span class="sxs-lookup"><span data-stu-id="bc114-152">World</span></span>|<span data-ttu-id="bc114-153">(0, 0) à (2, 1)</span><span class="sxs-lookup"><span data-stu-id="bc114-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="bc114-154">Page</span><span class="sxs-lookup"><span data-stu-id="bc114-154">Page</span></span>|<span data-ttu-id="bc114-155">(2, 0,5) à (4, 1.5)</span><span class="sxs-lookup"><span data-stu-id="bc114-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="bc114-156">Appareil</span><span class="sxs-lookup"><span data-stu-id="bc114-156">Device</span></span>|<span data-ttu-id="bc114-157">(192, 48) à (384, 144)</span><span class="sxs-lookup"><span data-stu-id="bc114-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc114-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc114-158">See Also</span></span>  
 [<span data-ttu-id="bc114-159">Systèmes de coordonnées et transformations</span><span class="sxs-lookup"><span data-stu-id="bc114-159">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="bc114-160">Représentation matricielle des transformations</span><span class="sxs-lookup"><span data-stu-id="bc114-160">Matrix Representation of Transformations</span></span>](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)
