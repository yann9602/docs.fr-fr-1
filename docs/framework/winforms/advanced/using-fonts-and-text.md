---
title: Utilisation de polices et de texte
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4febeed6aff2c18b5040020c2c1d3ee6cf59a52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="657fa-102">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="657fa-102">Using Fonts and Text</span></span>
<span data-ttu-id="657fa-103">Il existe plusieurs classes sont offertes par [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pour dessiner du texte dans les Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="657fa-103">There are several classes offered by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text on Windows Forms.</span></span> <span data-ttu-id="657fa-104">Le [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> classe dispose de plusieurs <xref:System.Drawing.Graphics.DrawString%2A> méthodes qui vous permettent de spécifier diverses fonctionnalités de texte, comme l’emplacement, le rectangle englobant, police et le format.</span><span class="sxs-lookup"><span data-stu-id="657fa-104">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="657fa-105">En outre, vous pouvez dessiner et mesurer le texte avec [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] à l’aide de la méthode statique <xref:System.Windows.Forms.TextRenderer.DrawText%2A> et <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> méthodes offertes par la `TextRenderer` classe.</span><span class="sxs-lookup"><span data-stu-id="657fa-105">In addition, you can draw and measure text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="657fa-106">Le [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] méthodes vous permettent également de spécifier la police, l’emplacement et le format.</span><span class="sxs-lookup"><span data-stu-id="657fa-106">The [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="657fa-107">Vous pouvez choisir le [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] ou [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pour le rendu de texte ; Toutefois, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] offre généralement de meilleures performances et une mesure de texte plus précis.</span><span class="sxs-lookup"><span data-stu-id="657fa-107">You can choose either [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] or [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] for text rendering; however, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="657fa-108">Incluent d’autres classes qui contribuent au rendu de texte `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, et `TextFormatFlags`.</span><span class="sxs-lookup"><span data-stu-id="657fa-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="657fa-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="657fa-109">In This Section</span></span>  
 [<span data-ttu-id="657fa-110">Guide pratique pour construire des familles de polices et des polices</span><span class="sxs-lookup"><span data-stu-id="657fa-110">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="657fa-111">Montre comment créer `Font` et `FontFamily` objets.</span><span class="sxs-lookup"><span data-stu-id="657fa-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="657fa-112">Guide pratique pour écrire du texte à un emplacement spécifié</span><span class="sxs-lookup"><span data-stu-id="657fa-112">How to: Draw Text at a Specified Location</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="657fa-113">Décrit comment dessiner du texte dans un certain emplacement à l’aide [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="657fa-113">Describes how to draw text in a certain location using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="657fa-114">Guide pratique pour écrire du texte renvoyé à la ligne dans un rectangle</span><span class="sxs-lookup"><span data-stu-id="657fa-114">How to: Draw Wrapped Text in a Rectangle</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="657fa-115">Explique comment dessiner du texte dans un rectangle à l’aide de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="657fa-115">Explains how to draw text in a rectangle using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="657fa-116">Guide pratique pour écrire du texte avec GDI</span><span class="sxs-lookup"><span data-stu-id="657fa-116">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="657fa-117">Montre comment utiliser [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pour dessiner du texte.</span><span class="sxs-lookup"><span data-stu-id="657fa-117">Demonstrates how to use [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text.</span></span>  
  
 [<span data-ttu-id="657fa-118">Guide pratique pour aligner le texte écrit</span><span class="sxs-lookup"><span data-stu-id="657fa-118">How to: Align Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 <span data-ttu-id="657fa-119">Montre comment mettre en forme [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] texte.</span><span class="sxs-lookup"><span data-stu-id="657fa-119">Shows how to format [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.</span></span>  
  
 [<span data-ttu-id="657fa-120">Guide pratique pour créer du texte vertical</span><span class="sxs-lookup"><span data-stu-id="657fa-120">How to: Create Vertical Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 <span data-ttu-id="657fa-121">Décrit comment dessiner du texte aligné verticalement avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="657fa-121">Describes how to draw vertically aligned text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="657fa-122">Guide pratique pour définir des taquets de tabulation dans du texte dessiné</span><span class="sxs-lookup"><span data-stu-id="657fa-122">How to: Set Tab Stops in Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="657fa-123">Montre comment dessiner du texte avec des taquets de tabulation avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="657fa-123">Shows how draw text with tab stops with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="657fa-124">Guide pratique pour énumérer les polices installées</span><span class="sxs-lookup"><span data-stu-id="657fa-124">How to: Enumerate Installed Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="657fa-125">Explique comment répertorier les noms de polices installées.</span><span class="sxs-lookup"><span data-stu-id="657fa-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="657fa-126">Guide pratique pour créer une collection de polices privées</span><span class="sxs-lookup"><span data-stu-id="657fa-126">How to: Create a Private Font Collection</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="657fa-127">Décrit comment créer un <xref:System.Drawing.Text.PrivateFontCollection> objet.</span><span class="sxs-lookup"><span data-stu-id="657fa-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="657fa-128">Guide pratique pour obtenir la métrique des polices</span><span class="sxs-lookup"><span data-stu-id="657fa-128">How to: Obtain Font Metrics</span></span>](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 <span data-ttu-id="657fa-129">Montre comment obtenir des métriques de police telles que la hauteur de cellule et de profondeur.</span><span class="sxs-lookup"><span data-stu-id="657fa-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="657fa-130">Guide pratique pour utiliser l‘anticrénelage avec du texte</span><span class="sxs-lookup"><span data-stu-id="657fa-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="657fa-131">Explique comment utiliser l’anticrénelage lors du dessin de texte.</span><span class="sxs-lookup"><span data-stu-id="657fa-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="657fa-132">Référence</span><span class="sxs-lookup"><span data-stu-id="657fa-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="657fa-133">Décrit cette classe et contient des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="657fa-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="657fa-134">Décrit cette classe et contient des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="657fa-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="657fa-135">Décrit cette classe et contient des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="657fa-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="657fa-136">Décrit cette classe et contient des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="657fa-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="657fa-137">Décrit cette classe et contient des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="657fa-137">Describes this class and contains links to all of its members.</span></span>
