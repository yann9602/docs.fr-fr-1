---
title: "Comment : effectuer un test de positionnement avec Geometry comme paramètre"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b5c5bb47e3f435419bcf3c472f052260adec7c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="c1540-102">Comment : effectuer un test de positionnement avec Geometry comme paramètre</span><span class="sxs-lookup"><span data-stu-id="c1540-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="c1540-103">Cet exemple montre comment effectuer un test de positionnement sur un objet visuel à l’aide un <xref:System.Windows.Media.Geometry> comme un accès au paramètre de test.</span><span class="sxs-lookup"><span data-stu-id="c1540-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1540-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="c1540-104">Example</span></span>  
 <span data-ttu-id="c1540-105">L’exemple suivant montre comment configurer un test de positionnement à l’aide de <xref:System.Windows.Media.GeometryHitTestParameters> pour la <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c1540-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="c1540-106">Le <xref:System.Windows.Point> valeur qui est passée à la `OnMouseDown` méthode est utilisée pour créer un <xref:System.Windows.Media.Geometry> objet afin d’étendre la plage du test d’atteinte.</span><span class="sxs-lookup"><span data-stu-id="c1540-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="c1540-107">Le <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> propriété du <xref:System.Windows.Media.GeometryHitTestResult> fournit des informations sur les résultats d’un test de positionnement qui utilise un <xref:System.Windows.Media.Geometry> comme un accès au paramètre de test.</span><span class="sxs-lookup"><span data-stu-id="c1540-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="c1540-108">L’illustration suivante montre la relation entre la géométrie du test de positionnement (le cercle bleu) et le contenu restitué de l’objet visuel cible (le carré rouge).</span><span class="sxs-lookup"><span data-stu-id="c1540-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 <span data-ttu-id="c1540-109">![Diagramme du IntersectionDetail utilisé dans le test de positionnement](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span><span class="sxs-lookup"><span data-stu-id="c1540-109">![Diagram of IntersectionDetail used in hit testing](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span></span>  
<span data-ttu-id="c1540-110">Intersection entre la géométrie du test de positionnement et l’objet visuel cible</span><span class="sxs-lookup"><span data-stu-id="c1540-110">Intersection between hit test geometry and target visual object</span></span>  
  
 <span data-ttu-id="c1540-111">L’exemple suivant montre comment implémenter un rappel de test de positionnement lorsqu’un <xref:System.Windows.Media.Geometry> est utilisé comme un paramètre de test de positionnement.</span><span class="sxs-lookup"><span data-stu-id="c1540-111">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="c1540-112">Le `result` paramètre est effectué en une <xref:System.Windows.Media.GeometryHitTestResult> afin de récupérer la valeur de la <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c1540-112">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="c1540-113">La valeur de propriété vous permet de déterminer si le <xref:System.Windows.Media.Geometry> paramètre de test de positionnement est complètement ou partiellement contenu dans le contenu affiché de la cible de test de positionnement.</span><span class="sxs-lookup"><span data-stu-id="c1540-113">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="c1540-114">Dans ce cas, l’exemple de code ajoute à la liste les résultats du test de positionnement uniquement pour les objets visuels qui sont entièrement contenus dans les limites de la cible.</span><span class="sxs-lookup"><span data-stu-id="c1540-114">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <span data-ttu-id="c1540-115">Le <xref:System.Windows.Media.HitTestResult> rappel ne doit pas être appelé lorsque le détail d’intersection est <xref:System.Windows.Media.IntersectionDetail.Empty>.</span><span class="sxs-lookup"><span data-stu-id="c1540-115">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1540-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1540-116">See Also</span></span>  
 [<span data-ttu-id="c1540-117">Test de positionnement dans la couche visuelle</span><span class="sxs-lookup"><span data-stu-id="c1540-117">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="c1540-118">Effectuer un test de positionnement avec Geometry dans un Visual</span><span class="sxs-lookup"><span data-stu-id="c1540-118">Hit Test Geometry in a Visual</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)
