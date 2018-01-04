---
title: "Régions dans GDI+"
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
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d3805c2d67f5241425ef72d3802aba996d33cfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="regions-in-gdi"></a><span data-ttu-id="100ac-102">Régions dans GDI+</span><span class="sxs-lookup"><span data-stu-id="100ac-102">Regions in GDI+</span></span>
<span data-ttu-id="100ac-103">Une région est une partie de la zone d’affichage d’un périphérique de sortie.</span><span class="sxs-lookup"><span data-stu-id="100ac-103">A region is a portion of the display area of an output device.</span></span> <span data-ttu-id="100ac-104">Régions peuvent être simple (un rectangle) ou complexe (combinaison de polygones et de courbes fermées).</span><span class="sxs-lookup"><span data-stu-id="100ac-104">Regions can be simple (a single rectangle) or complex (a combination of polygons and closed curves).</span></span> <span data-ttu-id="100ac-105">L’illustration suivante montre deux régions : une construite à partir d’un rectangle et l’autre construite à partir d’un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="100ac-105">The following illustration shows two regions: one constructed from a rectangle, and the other constructed from a path.</span></span>  
  
 <span data-ttu-id="100ac-106">![Régions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span><span class="sxs-lookup"><span data-stu-id="100ac-106">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span></span>  
  
## <a name="using-regions"></a><span data-ttu-id="100ac-107">Utilisation de régions</span><span class="sxs-lookup"><span data-stu-id="100ac-107">Using Regions</span></span>  
 <span data-ttu-id="100ac-108">Les régions sont souvent utilisées pour le découpage et le test de positionnement.</span><span class="sxs-lookup"><span data-stu-id="100ac-108">Regions are often used for clipping and hit testing.</span></span> <span data-ttu-id="100ac-109">Le découpage consiste à restreindre le dessin à une certaine région de la zone d’affichage, généralement la partie qui doit être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="100ac-109">Clipping involves restricting drawing to a certain region of the display area, usually the portion that needs to be updated.</span></span> <span data-ttu-id="100ac-110">Un test de positionnement implique la vérification pour déterminer si le curseur se trouve dans une région donnée de l’écran lorsqu’un bouton de la souris est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="100ac-110">Hit testing involves checking to determine whether the cursor is in a certain region of the screen when a mouse button is pressed.</span></span>  
  
 <span data-ttu-id="100ac-111">Vous pouvez construire une région à partir d’un rectangle ou un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="100ac-111">You can construct a region from a rectangle or a path.</span></span> <span data-ttu-id="100ac-112">Vous pouvez également créer des régions complexes en combinant des régions existantes.</span><span class="sxs-lookup"><span data-stu-id="100ac-112">You can also create complex regions by combining existing regions.</span></span> <span data-ttu-id="100ac-113">Le <xref:System.Drawing.Region> classe fournit les méthodes suivantes pour combiner des régions : <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, et <xref:System.Drawing.Region.Complement%2A>.</span><span class="sxs-lookup"><span data-stu-id="100ac-113">The <xref:System.Drawing.Region> class provides the following methods for combining regions: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, and <xref:System.Drawing.Region.Complement%2A>.</span></span>  
  
 <span data-ttu-id="100ac-114">L’intersection de deux régions est l’ensemble de tous les points qui appartiennent aux deux régions.</span><span class="sxs-lookup"><span data-stu-id="100ac-114">The intersection of two regions is the set of all points belonging to both regions.</span></span> <span data-ttu-id="100ac-115">L’union est l’ensemble de tous les points appartenant à une ou l’autre ou les deux régions.</span><span class="sxs-lookup"><span data-stu-id="100ac-115">The union is the set of all points belonging to one or the other or both regions.</span></span> <span data-ttu-id="100ac-116">Le complément d’une région est l’ensemble de tous les points qui ne sont pas dans la région.</span><span class="sxs-lookup"><span data-stu-id="100ac-116">The complement of a region is the set of all points that are not in the region.</span></span> <span data-ttu-id="100ac-117">L’illustration suivante montre l’intersection et l’union de deux régions indiqué dans l’illustration précédente.</span><span class="sxs-lookup"><span data-stu-id="100ac-117">The following illustration shows the intersection and union of the two regions shown in the preceding illustration.</span></span>  
  
 <span data-ttu-id="100ac-118">![Régions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span><span class="sxs-lookup"><span data-stu-id="100ac-118">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span></span>  
  
 <span data-ttu-id="100ac-119">Le <xref:System.Drawing.Region.Xor%2A> méthode appliquée à deux régions, produit une région qui contient tous les points qui appartiennent à une région ou l’autre, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="100ac-119">The <xref:System.Drawing.Region.Xor%2A> method, applied to a pair of regions, produces a region that contains all points that belong to one region or the other, but not both.</span></span> <span data-ttu-id="100ac-120">Le <xref:System.Drawing.Region.Exclude%2A> méthode appliquée à deux régions, produit une région qui contient tous les points de la première région qui ne sont pas dans la deuxième zone.</span><span class="sxs-lookup"><span data-stu-id="100ac-120">The <xref:System.Drawing.Region.Exclude%2A> method, applied to a pair of regions, produces a region that contains all points in the first region that are not in the second region.</span></span> <span data-ttu-id="100ac-121">L’illustration suivante montre les régions qui résultent de l’application de la <xref:System.Drawing.Region.Xor%2A> et <xref:System.Drawing.Region.Exclude%2A> méthodes aux deux régions illustrées au début de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="100ac-121">The following illustration shows the regions that result from applying the <xref:System.Drawing.Region.Xor%2A> and <xref:System.Drawing.Region.Exclude%2A> methods to the two regions shown at the beginning of this topic.</span></span>  
  
 <span data-ttu-id="100ac-122">![Régions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span><span class="sxs-lookup"><span data-stu-id="100ac-122">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span></span>  
  
 <span data-ttu-id="100ac-123">Pour remplir une région, vous avez besoin une <xref:System.Drawing.Graphics> objet, un <xref:System.Drawing.Brush> objet et un <xref:System.Drawing.Region> objet.</span><span class="sxs-lookup"><span data-stu-id="100ac-123">To fill a region, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Brush> object, and a <xref:System.Drawing.Region> object.</span></span> <span data-ttu-id="100ac-124">Le <xref:System.Drawing.Graphics> objet fournit le <xref:System.Drawing.Graphics.FillRegion%2A> (méthode) et le <xref:System.Drawing.Brush> objet stocke les attributs de remplissage, telles que la couleur ou un motif.</span><span class="sxs-lookup"><span data-stu-id="100ac-124">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.FillRegion%2A> method, and the <xref:System.Drawing.Brush> object stores attributes of the fill, such as color or pattern.</span></span> <span data-ttu-id="100ac-125">L’exemple suivant remplit une zone avec une couleur unie.</span><span class="sxs-lookup"><span data-stu-id="100ac-125">The following example fills a region with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="100ac-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="100ac-126">See Also</span></span>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [<span data-ttu-id="100ac-127">Lignes, courbes et formes</span><span class="sxs-lookup"><span data-stu-id="100ac-127">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="100ac-128">Utilisation de régions</span><span class="sxs-lookup"><span data-stu-id="100ac-128">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
