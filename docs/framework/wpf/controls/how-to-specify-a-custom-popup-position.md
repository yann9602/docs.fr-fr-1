---
title: "Comment : spécifier une position de menu contextuel personnalisée"
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
helpviewer_keywords: Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae10153f31b79a220b84cae7a6525eca0ce0bd9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="b02b0-102">Comment : spécifier une position de menu contextuel personnalisée</span><span class="sxs-lookup"><span data-stu-id="b02b0-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="b02b0-103">Cet exemple montre comment spécifier un emplacement personnalisé pour un <xref:System.Windows.Controls.Primitives.Popup> contrôle lorsque le <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est définie sur <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="b02b0-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b02b0-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b02b0-104">Example</span></span>  
 <span data-ttu-id="b02b0-105">Lorsque le <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est définie sur <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, le <xref:System.Windows.Controls.Primitives.Popup> appelle une instance définie de la <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> déléguer.</span><span class="sxs-lookup"><span data-stu-id="b02b0-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="b02b0-106">Ce délégué retourne un jeu de points possibles relatives à l’angle supérieur gauche de la zone cible et l’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="b02b0-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="b02b0-107">Le <xref:System.Windows.Controls.Primitives.Popup> la sélection élective se produit au point qui fournit la meilleure visibilité.</span><span class="sxs-lookup"><span data-stu-id="b02b0-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="b02b0-108">L’exemple suivant montre comment définir la position d’un <xref:System.Windows.Controls.Primitives.Popup> en définissant le <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="b02b0-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="b02b0-109">Il montre également comment créer et affecter un <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> délégué afin de positionner le <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="b02b0-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="b02b0-110">Le délégué de rappel retourne deux <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objets.</span><span class="sxs-lookup"><span data-stu-id="b02b0-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="b02b0-111">Si le <xref:System.Windows.Controls.Primitives.Popup> est masqué par un bord de l’écran à la première position, la <xref:System.Windows.Controls.Primitives.Popup> est placé à la deuxième position.</span><span class="sxs-lookup"><span data-stu-id="b02b0-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="b02b0-112">Pour obtenir un exemple complet, consultez [Positionnement Popup, exemple](http://go.microsoft.com/fwlink/?LinkID=160032).</span><span class="sxs-lookup"><span data-stu-id="b02b0-112">For the complete sample, see [Popup Placement Sample](http://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b02b0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b02b0-113">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="b02b0-114">Vue d’ensemble de Popup</span><span class="sxs-lookup"><span data-stu-id="b02b0-114">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [<span data-ttu-id="b02b0-115">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="b02b0-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
