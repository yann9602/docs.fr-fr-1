---
title: "Comment : créer une géométrie combinée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee77da00604b7e4965cc376748606b6bd0e92ad8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-combined-geometry"></a><span data-ttu-id="870b1-102">Comment : créer une géométrie combinée</span><span class="sxs-lookup"><span data-stu-id="870b1-102">How to: Create a Combined Geometry</span></span>
<span data-ttu-id="870b1-103">Cet exemple montre comment combiner des géométries.</span><span class="sxs-lookup"><span data-stu-id="870b1-103">This example shows how to combine geometries.</span></span> <span data-ttu-id="870b1-104">Pour combiner deux géométries, utilisez un <xref:System.Windows.Media.CombinedGeometry> objet.</span><span class="sxs-lookup"><span data-stu-id="870b1-104">To combine two geometries, use a <xref:System.Windows.Media.CombinedGeometry> object.</span></span> <span data-ttu-id="870b1-105">Définir son <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> propriétés avec les deux géométries à combiner et attribuez le <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> propriété qui détermine la façon dont les géométries seront combinées ensemble, à `Union`, `Intersect`, `Exclude`, ou `Xor`.</span><span class="sxs-lookup"><span data-stu-id="870b1-105">Set its <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> properties  with the two geometries to combine, and set the <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> property, which determines how the geometries will be combined together, to `Union`, `Intersect`, `Exclude`, or `Xor`.</span></span>  
  
 <span data-ttu-id="870b1-106">Pour créer une géométrie composite à partir de deux ou plusieurs des géométries, utilisez un <xref:System.Windows.Media.GeometryGroup>.</span><span class="sxs-lookup"><span data-stu-id="870b1-106">To create a composite geometry from two or more geometries, use a <xref:System.Windows.Media.GeometryGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="870b1-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="870b1-107">Example</span></span>  
 <span data-ttu-id="870b1-108">Dans l’exemple suivant, un <xref:System.Windows.Media.CombinedGeometry> est défini avec un mode de géométrie combinée `Exclude`.</span><span class="sxs-lookup"><span data-stu-id="870b1-108">In the following example, a <xref:System.Windows.Media.CombinedGeometry> is defined with a geometry combine mode of `Exclude`.</span></span>  <span data-ttu-id="870b1-109">Les deux <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définies comme des cercles de même rayon mais avec un décalage de centres de 50.</span><span class="sxs-lookup"><span data-stu-id="870b1-109">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 <span data-ttu-id="870b1-110">![Mode de combinaison des résultats de l’exclusion](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span><span class="sxs-lookup"><span data-stu-id="870b1-110">![Results of the Exclude combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span></span>  
<span data-ttu-id="870b1-111">Géométrie combinée Exclude</span><span class="sxs-lookup"><span data-stu-id="870b1-111">Combined Geometry Exclude</span></span>  
  
 <span data-ttu-id="870b1-112">Dans le balisage suivant, un <xref:System.Windows.Media.CombinedGeometry> est défini avec un mode combiné de `Intersect`.</span><span class="sxs-lookup"><span data-stu-id="870b1-112">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Intersect`.</span></span>  <span data-ttu-id="870b1-113">Les deux <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définies comme des cercles de même rayon mais avec un décalage de centres de 50.</span><span class="sxs-lookup"><span data-stu-id="870b1-113">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 <span data-ttu-id="870b1-114">![Mode de combinaison des résultats de l’intersection](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span><span class="sxs-lookup"><span data-stu-id="870b1-114">![Results of the Intersect combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span></span>  
<span data-ttu-id="870b1-115">Géométrie combinée Intersect</span><span class="sxs-lookup"><span data-stu-id="870b1-115">Combined Geometry Intersect</span></span>  
  
 <span data-ttu-id="870b1-116">Dans le balisage suivant, un <xref:System.Windows.Media.CombinedGeometry> est défini avec un mode combiné de `Union`.</span><span class="sxs-lookup"><span data-stu-id="870b1-116">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Union`.</span></span>  <span data-ttu-id="870b1-117">Les deux <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définies comme des cercles de même rayon mais avec un décalage de centres de 50.</span><span class="sxs-lookup"><span data-stu-id="870b1-117">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 <span data-ttu-id="870b1-118">![Résultats du mode d’association Union](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span><span class="sxs-lookup"><span data-stu-id="870b1-118">![Results of the Union combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span></span>  
<span data-ttu-id="870b1-119">Géométrie combinée Union</span><span class="sxs-lookup"><span data-stu-id="870b1-119">Combined Geometry Union</span></span>  
  
 <span data-ttu-id="870b1-120">Dans le balisage suivant, un <xref:System.Windows.Media.CombinedGeometry> est défini avec un mode combiné de `Xor`.</span><span class="sxs-lookup"><span data-stu-id="870b1-120">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Xor`.</span></span>  <span data-ttu-id="870b1-121">Les deux <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définies comme des cercles de même rayon mais avec un décalage de centres de 50.</span><span class="sxs-lookup"><span data-stu-id="870b1-121">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 <span data-ttu-id="870b1-122">![Résultats du mode d’association Xor](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span><span class="sxs-lookup"><span data-stu-id="870b1-122">![Results of the Xor combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span></span>  
<span data-ttu-id="870b1-123">Géométrie combinée Xor</span><span class="sxs-lookup"><span data-stu-id="870b1-123">Combined Geometry Xor</span></span>
