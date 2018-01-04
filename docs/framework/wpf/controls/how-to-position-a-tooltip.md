---
title: "Comment : positionner une info-bulle"
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
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62e86f2adfbe8f8aac000d653e955555c7def750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="c6f47-102">Comment : positionner une info-bulle</span><span class="sxs-lookup"><span data-stu-id="c6f47-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="c6f47-103">Cet exemple montre comment spécifier la position d’une info-bulle sur l’écran.</span><span class="sxs-lookup"><span data-stu-id="c6f47-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6f47-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6f47-104">Example</span></span>  
 <span data-ttu-id="c6f47-105">Vous pouvez positionner une info-bulle à l’aide d’un ensemble de cinq propriétés définies dans les deux le <xref:System.Windows.Controls.ToolTip> et <xref:System.Windows.Controls.ToolTipService> classes.</span><span class="sxs-lookup"><span data-stu-id="c6f47-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="c6f47-106">Le tableau suivant illustre ces deux jeux de cinq propriétés et fournit des liens vers leur documentation de référence en fonction de la classe.</span><span class="sxs-lookup"><span data-stu-id="c6f47-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="c6f47-107">Propriétés d’info-bulle correspondant en fonction de classe</span><span class="sxs-lookup"><span data-stu-id="c6f47-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="c6f47-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>propriétés de classe</span><span class="sxs-lookup"><span data-stu-id="c6f47-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="c6f47-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>propriétés de classe</span><span class="sxs-lookup"><span data-stu-id="c6f47-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="c6f47-110">Si vous définissez le contenu d’une info-bulle à l’aide un <xref:System.Windows.Controls.ToolTip> de l’objet, vous pouvez utiliser les propriétés des deux classes ; Toutefois, le <xref:System.Windows.Controls.ToolTipService> propriétés sont prioritaires.</span><span class="sxs-lookup"><span data-stu-id="c6f47-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="c6f47-111">Utilisez le <xref:System.Windows.Controls.ToolTipService> propriétés pour les info-bulles qui ne sont pas définies comme <xref:System.Windows.Controls.ToolTip> objets.</span><span class="sxs-lookup"><span data-stu-id="c6f47-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="c6f47-112">Les illustrations suivantes montrent comment positionner une info-bulle à l’aide de ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="c6f47-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="c6f47-113">Bien que, le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemples de ces illustrations montrent comment définir les propriétés qui sont définies par le <xref:System.Windows.Controls.ToolTip> classe, les propriétés correspondantes de la <xref:System.Windows.Controls.ToolTipService> classe suivent les mêmes règles de disposition.</span><span class="sxs-lookup"><span data-stu-id="c6f47-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="c6f47-114">Pour plus d’informations sur les valeurs possibles pour la propriété de Placement, consultez [comportement de positionnement Popup](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="c6f47-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span></span>  
  
 <span data-ttu-id="c6f47-115">![Positionnement de ToolTip](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span><span class="sxs-lookup"><span data-stu-id="c6f47-115">![ToolTip placement](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span></span>  
<span data-ttu-id="c6f47-116">Sélection élective de l’info-bulle à l’aide de la propriété de Placement</span><span class="sxs-lookup"><span data-stu-id="c6f47-116">ToolTip placement by using the Placement property</span></span>  
  
 <span data-ttu-id="c6f47-117">![Placer une info-bulle à l’aide d’un rectangle de sélection élective](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span><span class="sxs-lookup"><span data-stu-id="c6f47-117">![Placing a ToolTip by using a placement rectangle](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span></span>  
<span data-ttu-id="c6f47-118">Positionnement d’une info-bulle à l’aide des propriétés Placement et PlacementRectangle</span><span class="sxs-lookup"><span data-stu-id="c6f47-118">ToolTip placement by using the Placement and PlacementRectangle properties</span></span>  
  
 <span data-ttu-id="c6f47-119">![Diagramme de positionnement de ToolTip](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span><span class="sxs-lookup"><span data-stu-id="c6f47-119">![ToolTip placement diagram](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span></span>  
<span data-ttu-id="c6f47-120">Sélection élective de l’info-bulle à l’aide des propriétés Placement, PlacementRectangle et Offset</span><span class="sxs-lookup"><span data-stu-id="c6f47-120">ToolTip placement by using the Placement, PlacementRectangle, and Offset properties</span></span>  
  
 <span data-ttu-id="c6f47-121">L’exemple suivant montre comment utiliser le <xref:System.Windows.Controls.ToolTip> propriétés pour spécifier la position d’une info-bulle dont le contenu est un <xref:System.Windows.Controls.ToolTip> objet.</span><span class="sxs-lookup"><span data-stu-id="c6f47-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="c6f47-122">L’exemple suivant montre comment utiliser le <xref:System.Windows.Controls.ToolTipService> propriétés pour spécifier la position d’une info-bulle dont le contenu n’est pas un <xref:System.Windows.Controls.ToolTip> objet.</span><span class="sxs-lookup"><span data-stu-id="c6f47-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="c6f47-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6f47-123">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="c6f47-124">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="c6f47-124">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="c6f47-125">Vue d’ensemble de l’info-bulle</span><span class="sxs-lookup"><span data-stu-id="c6f47-125">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)  
 [<span data-ttu-id="c6f47-126">Utiliser les ContextMenuService ToolTipService</span><span class="sxs-lookup"><span data-stu-id="c6f47-126">Use the ContextMenuService and ToolTipService</span></span>](http://msdn.microsoft.com/en-us/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
