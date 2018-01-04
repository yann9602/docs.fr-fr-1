---
title: Structure de l'interface graphique
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43bd899a1dd53dc8cdae4f81e90b1aa74c29cb67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="structure-of-the-graphics-interface"></a><span data-ttu-id="0bd60-102">Structure de l'interface graphique</span><span class="sxs-lookup"><span data-stu-id="0bd60-102">Structure of the Graphics Interface</span></span>
<span data-ttu-id="0bd60-103">L’interface de classe managée à [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] contient environ 60 classes, 50 énumérations et 8 structures.</span><span class="sxs-lookup"><span data-stu-id="0bd60-103">The managed class interface to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] contains about 60 classes, 50 enumerations, and 8 structures.</span></span> <span data-ttu-id="0bd60-104">Le <xref:System.Drawing.Graphics> classe est au cœur de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fonctionnalité ; il s’agit de la classe qui permet de dessiner des lignes, des courbes, des chiffres, des images et texte.</span><span class="sxs-lookup"><span data-stu-id="0bd60-104">The <xref:System.Drawing.Graphics> class is at the core of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] functionality; it is the class that actually draws lines, curves, figures, images, and text.</span></span>  
  
## <a name="important-classes"></a><span data-ttu-id="0bd60-105">Classes importantes</span><span class="sxs-lookup"><span data-stu-id="0bd60-105">Important Classes</span></span>  
 <span data-ttu-id="0bd60-106">De nombreuses classes fonctionnent en collaboration avec la <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="0bd60-106">Many classes work together with the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="0bd60-107">Par exemple, le <xref:System.Drawing.Graphics.DrawLine%2A> méthode reçoit un <xref:System.Drawing.Pen> objet, qui contient les attributs (couleur, largeur, style de ligne, etc.) de la ligne à dessiner.</span><span class="sxs-lookup"><span data-stu-id="0bd60-107">For example, the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object, which holds attributes (color, width, dash style, and the like) of the line to be drawn.</span></span> <span data-ttu-id="0bd60-108">Le <xref:System.Drawing.Graphics.FillRectangle%2A> méthode peut recevoir un pointeur vers un <xref:System.Drawing.Drawing2D.LinearGradientBrush> objet, qui fonctionne avec le <xref:System.Drawing.Graphics> objet pour remplir un rectangle avec une couleur.</span><span class="sxs-lookup"><span data-stu-id="0bd60-108">The <xref:System.Drawing.Graphics.FillRectangle%2A> method can receive a pointer to a <xref:System.Drawing.Drawing2D.LinearGradientBrush> object, which works with the <xref:System.Drawing.Graphics> object to fill a rectangle with a gradually changing color.</span></span> <span data-ttu-id="0bd60-109"><xref:System.Drawing.Font>et <xref:System.Drawing.StringFormat> objets influencent la manière dont un <xref:System.Drawing.Graphics> objet dessine du texte.</span><span class="sxs-lookup"><span data-stu-id="0bd60-109"><xref:System.Drawing.Font> and <xref:System.Drawing.StringFormat> objects influence the way a <xref:System.Drawing.Graphics> object draws text.</span></span> <span data-ttu-id="0bd60-110">A <xref:System.Drawing.Drawing2D.Matrix> objet stocke et manipule la transformation universelle d’un <xref:System.Drawing.Graphics> objet, qui est utilisé pour faire pivoter, de mettre à l’échelle et de retourner des images.</span><span class="sxs-lookup"><span data-stu-id="0bd60-110">A <xref:System.Drawing.Drawing2D.Matrix> object stores and manipulates the world transformation of a <xref:System.Drawing.Graphics> object, which is used to rotate, scale, and flip images.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="0bd60-111">fournit plusieurs structures (par exemple, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, et <xref:System.Drawing.Size>) pour organiser les données de graphique.</span><span class="sxs-lookup"><span data-stu-id="0bd60-111"> provides several structures (for example, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, and <xref:System.Drawing.Size>) for organizing graphics data.</span></span> <span data-ttu-id="0bd60-112">En outre, certaines classes sont des types de données principalement comme structurés.</span><span class="sxs-lookup"><span data-stu-id="0bd60-112">Also, certain classes serve primarily as structured data types.</span></span> <span data-ttu-id="0bd60-113">Par exemple, le <xref:System.Drawing.Imaging.BitmapData> classe est une application d’assistance pour le <xref:System.Drawing.Bitmap> (classe) et le <xref:System.Drawing.Drawing2D.PathData> classe est une application auxiliaire pour la <xref:System.Drawing.Drawing2D.GraphicsPath> classe.</span><span class="sxs-lookup"><span data-stu-id="0bd60-113">For example, the <xref:System.Drawing.Imaging.BitmapData> class is a helper for the <xref:System.Drawing.Bitmap> class, and the <xref:System.Drawing.Drawing2D.PathData> class is a helper for the <xref:System.Drawing.Drawing2D.GraphicsPath> class.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="0bd60-114">définit plusieurs énumérations, qui sont des collections de constantes associées.</span><span class="sxs-lookup"><span data-stu-id="0bd60-114"> defines several enumerations, which are collections of related constants.</span></span> <span data-ttu-id="0bd60-115">Par exemple, le <xref:System.Drawing.Drawing2D.LineJoin> énumération contient les éléments <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, et <xref:System.Drawing.Drawing2D.LineJoin.Round>, qui spécifient les styles qui peuvent être utilisés pour joindre deux lignes.</span><span class="sxs-lookup"><span data-stu-id="0bd60-115">For example, the <xref:System.Drawing.Drawing2D.LineJoin> enumeration contains the elements <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, and <xref:System.Drawing.Drawing2D.LineJoin.Round>, which specify styles that can be used to join two lines.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd60-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bd60-116">See Also</span></span>  
 [<span data-ttu-id="0bd60-117">Vue d’ensemble des graphismes</span><span class="sxs-lookup"><span data-stu-id="0bd60-117">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [<span data-ttu-id="0bd60-118">À propos du code managé GDI+</span><span class="sxs-lookup"><span data-stu-id="0bd60-118">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [<span data-ttu-id="0bd60-119">Utilisation de classes graphiques managées</span><span class="sxs-lookup"><span data-stu-id="0bd60-119">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
