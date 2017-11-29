---
title: "Comment : créer plusieurs sous-chemins dans un PathGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a9a233df95f69a68c5410c5836dacd5ab2c239a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="4b665-102">Comment : créer plusieurs sous-chemins dans un PathGeometry</span><span class="sxs-lookup"><span data-stu-id="4b665-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="4b665-103">Cet exemple montre comment créer plusieurs sous-chemins dans un <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="4b665-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="4b665-104">Pour créer plusieurs sous-chemins, vous créez un <xref:System.Windows.Media.PathFigure> de chaque sous-tracé.</span><span class="sxs-lookup"><span data-stu-id="4b665-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b665-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b665-105">Example</span></span>  
 <span data-ttu-id="4b665-106">L’exemple suivant crée deux sous-chemins, chacun un triangle.</span><span class="sxs-lookup"><span data-stu-id="4b665-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="4b665-107">L’exemple suivant montre comment créer plusieurs sous-chemins à l’aide un <xref:System.Windows.Shapes.Path> et [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] la syntaxe d’attribut.</span><span class="sxs-lookup"><span data-stu-id="4b665-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="4b665-108">Chaque `M` crée un sous-chemin de sorte que l’exemple crée deux sous-chemins qui dessinent chacun un triangle.</span><span class="sxs-lookup"><span data-stu-id="4b665-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="4b665-109">(Notez que cette syntaxe d’attribut crée en fait un <xref:System.Windows.Media.StreamGeometry>, une version légère d’un <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="4b665-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="4b665-110">(Pour plus d’informations, consultez la page [Syntaxe XAML pour les tracés](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md).)</span><span class="sxs-lookup"><span data-stu-id="4b665-110">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b665-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b665-111">See Also</span></span>  
 [<span data-ttu-id="4b665-112">Vue d’ensemble de Geometry</span><span class="sxs-lookup"><span data-stu-id="4b665-112">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
