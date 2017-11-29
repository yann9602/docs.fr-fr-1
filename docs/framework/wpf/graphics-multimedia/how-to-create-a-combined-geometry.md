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
ms.openlocfilehash: 2be0471f27d26b145cc29847a08bf3bc3b1d51ff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-combined-geometry"></a><span data-ttu-id="521c2-102">Comment : créer une géométrie combinée</span><span class="sxs-lookup"><span data-stu-id="521c2-102">How to: Create a Combined Geometry</span></span>
<span data-ttu-id="521c2-103">Cet exemple montre comment combiner des géométries.</span><span class="sxs-lookup"><span data-stu-id="521c2-103">This example shows how to combine geometries.</span></span> <span data-ttu-id="521c2-104">Pour combiner deux géométries, utilisez un <xref:System.Windows.Media.CombinedGeometry> objet.</span><span class="sxs-lookup"><span data-stu-id="521c2-104">To combine two geometries, use a <xref:System.Windows.Media.CombinedGeometry> object.</span></span> <span data-ttu-id="521c2-105">Définir son <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> propriétés avec les deux géométries à combiner et attribuez le <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> propriété qui détermine la façon dont les géométries seront combinées ensemble, à `Union`, `Intersect`, `Exclude`, ou `Xor`.</span><span class="sxs-lookup"><span data-stu-id="521c2-105">Set its <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> properties  with the two geometries to combine, and set the <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> property, which determines how the geometries will be combined together, to `Union`, `Intersect`, `Exclude`, or `Xor`.</span></span>  
  
 <span data-ttu-id="521c2-106">Pour créer une géométrie composite à partir de deux ou plusieurs des géométries, utilisez un <xref:System.Windows.Media.GeometryGroup>.</span><span class="sxs-lookup"><span data-stu-id="521c2-106">To create a composite geometry from two or more geometries, use a <xref:System.Windows.Media.GeometryGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="521c2-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="521c2-107">Example</span></span>  
 <span data-ttu-id="521c2-108">Dans l’exemple suivant, un <xref:System.Windows.Media.CombinedGeometry> est défini avec un mode de géométrie combinée `Exclude`.</span><span class="sxs-lookup"><span data-stu-id="521c2-108">In the following example, a <xref:System.Windows.Media.CombinedGeometry> is defined with a geometry combine mode of `Exclude`.</span></span>  <span data-ttu-id="521c2-109">Les deux <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définies comme des cercles de même rayon mais avec un décalage de centres de 50.</span><span class="sxs-lookup"><span data-stu-id="521c2-109">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 <span data-ttu-id="521c2-110">![Mode de combinaison des résultats de l’exclusion](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span><span class="sxs-lookup"><span data-stu-id="521c2-110">![Results of the Exclude combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span></span>  
<span data-ttu-id="521c2-111">Géométrie combinée Exclude</span><span class="sxs-lookup"><span data-stu-id="521c2-111">Combined Geometry Exclude</span></span>  
  
 <span data-ttu-id="521c2-112">Dans le balisage suivant, un <xref:System.Windows.Media.CombinedGeometry> est défini avec un mode combiné de `Intersect`.</span><span class="sxs-lookup"><span data-stu-id="521c2-112">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Intersect`.</span></span>  <span data-ttu-id="521c2-113">Les deux <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définies comme des cercles de même rayon mais avec un décalage de centres de 50.</span><span class="sxs-lookup"><span data-stu-id="521c2-113">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 <span data-ttu-id="521c2-114">![Mode de combinaison des résultats de l’intersection](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span><span class="sxs-lookup"><span data-stu-id="521c2-114">![Results of the Intersect combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span></span>  
<span data-ttu-id="521c2-115">Géométrie combinée Intersect</span><span class="sxs-lookup"><span data-stu-id="521c2-115">Combined Geometry Intersect</span></span>  
  
 <span data-ttu-id="521c2-116">Dans le balisage suivant, un <xref:System.Windows.Media.CombinedGeometry> est défini avec un mode combiné de `Union`.</span><span class="sxs-lookup"><span data-stu-id="521c2-116">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Union`.</span></span>  <span data-ttu-id="521c2-117">Les deux <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définies comme des cercles de même rayon mais avec un décalage de centres de 50.</span><span class="sxs-lookup"><span data-stu-id="521c2-117">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 <span data-ttu-id="521c2-118">![Résultats du mode d’association Union](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span><span class="sxs-lookup"><span data-stu-id="521c2-118">![Results of the Union combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span></span>  
<span data-ttu-id="521c2-119">Géométrie combinée Union</span><span class="sxs-lookup"><span data-stu-id="521c2-119">Combined Geometry Union</span></span>  
  
 <span data-ttu-id="521c2-120">Dans le balisage suivant, un <xref:System.Windows.Media.CombinedGeometry> est défini avec un mode combiné de `Xor`.</span><span class="sxs-lookup"><span data-stu-id="521c2-120">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Xor`.</span></span>  <span data-ttu-id="521c2-121">Les deux <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> et <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> sont définies comme des cercles de même rayon mais avec un décalage de centres de 50.</span><span class="sxs-lookup"><span data-stu-id="521c2-121">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 <span data-ttu-id="521c2-122">![Résultats du mode d’association Xor](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span><span class="sxs-lookup"><span data-stu-id="521c2-122">![Results of the Xor combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span></span>  
<span data-ttu-id="521c2-123">Géométrie combinée Xor</span><span class="sxs-lookup"><span data-stu-id="521c2-123">Combined Geometry Xor</span></span>
