---
title: "Utilisation de classes graphiques managées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI+, managed classes
- graphics [Windows Forms], using in Windows Forms
- graphics [Windows Forms], managed classes
ms.assetid: e6d1a42d-2100-46aa-97e6-a5ddc0baaae5
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a34e2726182c194882d94fe4b8d1164993d8284
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-managed-graphics-classes"></a><span data-ttu-id="dac7f-102">Utilisation de classes graphiques managées</span><span class="sxs-lookup"><span data-stu-id="dac7f-102">Using Managed Graphics Classes</span></span>
<span data-ttu-id="dac7f-103">Les rubriques suivantes décrivent comment utiliser le [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API dans le cadre de la classe managée.</span><span class="sxs-lookup"><span data-stu-id="dac7f-103">The following topics describe how to use the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API in the managed class framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dac7f-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dac7f-104">In This Section</span></span>  
 [<span data-ttu-id="dac7f-105">Mise en route de la programmation graphique</span><span class="sxs-lookup"><span data-stu-id="dac7f-105">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 <span data-ttu-id="dac7f-106">Décrit comment effectuer des tâches de base avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dac7f-106">Describes how to accomplish basic tasks with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="dac7f-107">Utilisation d'un stylet pour dessiner des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="dac7f-107">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 <span data-ttu-id="dac7f-108">Montre comment construire un stylet et l’utiliser pour dessiner une variété de formes et de lignes.</span><span class="sxs-lookup"><span data-stu-id="dac7f-108">Demonstrates how to construct a pen and use it to draw a variety of lines and shapes.</span></span>  
  
 [<span data-ttu-id="dac7f-109">Utilisation d'un pinceau pour remplir des formes</span><span class="sxs-lookup"><span data-stu-id="dac7f-109">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)  
 <span data-ttu-id="dac7f-110">Montre comment construire un pinceau et remplir des formes avec différents effets.</span><span class="sxs-lookup"><span data-stu-id="dac7f-110">Demonstrates how to construct a brush and fill shapes with a variety of effects.</span></span>  
  
 [<span data-ttu-id="dac7f-111">Utilisation d'un pinceau à dégradé pour remplir des formes</span><span class="sxs-lookup"><span data-stu-id="dac7f-111">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 <span data-ttu-id="dac7f-112">Montre comment créer et utiliser différents types de pinceaux de dégradé.</span><span class="sxs-lookup"><span data-stu-id="dac7f-112">Shows how to create and use different types of gradient brushes.</span></span>  
  
 [<span data-ttu-id="dac7f-113">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="dac7f-113">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)  
 <span data-ttu-id="dac7f-114">Montre comment construire et manipuler des images.</span><span class="sxs-lookup"><span data-stu-id="dac7f-114">Demonstrates how to construct and manipulate images.</span></span>  
  
 [<span data-ttu-id="dac7f-115">Fusion alpha de lignes et de remplissages</span><span class="sxs-lookup"><span data-stu-id="dac7f-115">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 <span data-ttu-id="dac7f-116">Montre comment obtenir la transparence des formes et des lignes.</span><span class="sxs-lookup"><span data-stu-id="dac7f-116">Demonstrates how to achieve transparency for shapes and lines.</span></span>  
  
 [<span data-ttu-id="dac7f-117">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="dac7f-117">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 <span data-ttu-id="dac7f-118">Montre comment dessiner du texte et utiliser des polices et des familles de polices.</span><span class="sxs-lookup"><span data-stu-id="dac7f-118">Shows how to draw text and use fonts and font families.</span></span>  
  
 [<span data-ttu-id="dac7f-119">Génération et dessin de courbes</span><span class="sxs-lookup"><span data-stu-id="dac7f-119">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)  
 <span data-ttu-id="dac7f-120">Montre comment dessiner des splines cardinales et Bézier.</span><span class="sxs-lookup"><span data-stu-id="dac7f-120">Shows how to draw Cardinal and Bezier splines.</span></span>  
  
 [<span data-ttu-id="dac7f-121">Génération et dessin de tracés</span><span class="sxs-lookup"><span data-stu-id="dac7f-121">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)  
 <span data-ttu-id="dac7f-122">Montre comment créer des figures à l’aide de chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="dac7f-122">Shows how to create figures using paths.</span></span>  
  
 [<span data-ttu-id="dac7f-123">Utilisation des transformations dans GDI+ managé</span><span class="sxs-lookup"><span data-stu-id="dac7f-123">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)  
 <span data-ttu-id="dac7f-124">Montre les transformations de matrices.</span><span class="sxs-lookup"><span data-stu-id="dac7f-124">Demonstrates matrix transformations.</span></span>  
  
 [<span data-ttu-id="dac7f-125">Utilisation de conteneurs graphiques</span><span class="sxs-lookup"><span data-stu-id="dac7f-125">Using Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-graphics-containers.md)  
 <span data-ttu-id="dac7f-126">Montre comment gérer des conteneurs graphiques imbriqués et l’état objet graphiques.</span><span class="sxs-lookup"><span data-stu-id="dac7f-126">Shows how to manage graphics object state and nested graphics containers.</span></span>  
  
 [<span data-ttu-id="dac7f-127">Utilisation de régions</span><span class="sxs-lookup"><span data-stu-id="dac7f-127">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)  
 <span data-ttu-id="dac7f-128">Montre le test d’atteinte et le découpage avec des régions.</span><span class="sxs-lookup"><span data-stu-id="dac7f-128">Demonstrates hit testing and clipping with regions.</span></span>  
  
 [<span data-ttu-id="dac7f-129">Recoloriage des images</span><span class="sxs-lookup"><span data-stu-id="dac7f-129">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 <span data-ttu-id="dac7f-130">Présente les divers aspects de la manipulation des couleurs.</span><span class="sxs-lookup"><span data-stu-id="dac7f-130">Demonstrates various aspects of manipulating colors.</span></span>  
  
 [<span data-ttu-id="dac7f-131">Utilisation d’encodeurs et de décodeurs d’images dans GDI+ managé</span><span class="sxs-lookup"><span data-stu-id="dac7f-131">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 <span data-ttu-id="dac7f-132">Afficher l’utilisation des encodeurs d’image et de décodeurs pour manipuler des images.</span><span class="sxs-lookup"><span data-stu-id="dac7f-132">Show how to use image encoders and decoders to manipulate images.</span></span>  
  
 [<span data-ttu-id="dac7f-133">Graphiques mis deux fois en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="dac7f-133">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 <span data-ttu-id="dac7f-134">Montre comment réduire le scintillement des doubles tampons.</span><span class="sxs-lookup"><span data-stu-id="dac7f-134">Demonstrates how to reduce flicker with double buffering.</span></span>
