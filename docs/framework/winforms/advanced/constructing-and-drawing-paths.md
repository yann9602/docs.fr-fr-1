---
title: "Génération et dessin de tracés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- paths [Windows Forms], drawing
- drawing paths [Windows Forms]
- graphics paths [Windows Forms], creating
- graphics paths [Windows Forms], drawing
- examples [Windows Forms], drawing paths
ms.assetid: f16ec921-56cf-46d1-9741-d7316ad06b23
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50d1952632b29450a441d3cf0c7d66bffc000ea5
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="constructing-and-drawing-paths"></a><span data-ttu-id="5b2f6-102">Génération et dessin de tracés</span><span class="sxs-lookup"><span data-stu-id="5b2f6-102">Constructing and Drawing Paths</span></span>
<span data-ttu-id="5b2f6-103">Un chemin d’accès est une séquence de primitives graphiques (lignes, rectangles, courbes, texte, etc.) qui peuvent être manipulées et dessiné comme une unité unique.</span><span class="sxs-lookup"><span data-stu-id="5b2f6-103">A path is a sequence of graphics primitives (lines, rectangles, curves, text, and the like) that can be manipulated and drawn as a single unit.</span></span> <span data-ttu-id="5b2f6-104">Un chemin d’accès peut être divisé en *chiffres* qui sont ouverts ou fermés.</span><span class="sxs-lookup"><span data-stu-id="5b2f6-104">A path can be divided into *figures* that are either open or closed.</span></span> <span data-ttu-id="5b2f6-105">Un graphique peut contenir plusieurs primitives.</span><span class="sxs-lookup"><span data-stu-id="5b2f6-105">A figure can contain several primitives.</span></span>  
  
 <span data-ttu-id="5b2f6-106">Vous pouvez dessiner un tracé en appelant le <xref:System.Drawing.Graphics.DrawPath%2A> méthode de la <xref:System.Drawing.Graphics> classe et que vous pouvez remplir un chemin d’accès en appelant le <xref:System.Drawing.Graphics.FillPath%2A> méthode de la <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="5b2f6-106">You can draw a path by calling the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class, and you can fill a path by calling the <xref:System.Drawing.Graphics.FillPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b2f6-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5b2f6-107">In This Section</span></span>  
 [<span data-ttu-id="5b2f6-108">Guide pratique pour créer des figures à partir de lignes, de courbes et de formes</span><span class="sxs-lookup"><span data-stu-id="5b2f6-108">How to: Create Figures from Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-figures-from-lines-curves-and-shapes.md)  
 <span data-ttu-id="5b2f6-109">Montre comment utiliser un <xref:System.Drawing.Drawing2D.GraphicsPath> pour créer des illustrations.</span><span class="sxs-lookup"><span data-stu-id="5b2f6-109">Shows how to use a <xref:System.Drawing.Drawing2D.GraphicsPath> to create figures.</span></span>  
  
 [<span data-ttu-id="5b2f6-110">Guide pratique pour remplir des figures ouvertes</span><span class="sxs-lookup"><span data-stu-id="5b2f6-110">How to: Fill Open Figures</span></span>](../../../../docs/framework/winforms/advanced/how-to-fill-open-figures.md)  
 <span data-ttu-id="5b2f6-111">Explique comment remplir un <xref:System.Drawing.Drawing2D.GraphicsPath>.</span><span class="sxs-lookup"><span data-stu-id="5b2f6-111">Explains how to fill a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
 [<span data-ttu-id="5b2f6-112">Guide pratique pour aplanir un tracé courbé en une ligne</span><span class="sxs-lookup"><span data-stu-id="5b2f6-112">How to: Flatten a Curved Path into a Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-flatten-a-curved-path-into-a-line.md)  
 <span data-ttu-id="5b2f6-113">Indique comment aplatir un <xref:System.Drawing.Drawing2D.GraphicsPath>.</span><span class="sxs-lookup"><span data-stu-id="5b2f6-113">Shows how to flatten a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5b2f6-114">Référence</span><span class="sxs-lookup"><span data-stu-id="5b2f6-114">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 <span data-ttu-id="5b2f6-115">Décrit cette classe et contient des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="5b2f6-115">Describes this class and contains links to all of its members.</span></span>
