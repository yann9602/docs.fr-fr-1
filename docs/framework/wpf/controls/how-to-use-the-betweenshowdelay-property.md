---
title: "Comment : utiliser la propriété BetweenShowDelay"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dca6dc7c6238ef4accc921818090237d17ce1cbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-betweenshowdelay-property"></a><span data-ttu-id="a0a47-102">Comment : utiliser la propriété BetweenShowDelay</span><span class="sxs-lookup"><span data-stu-id="a0a47-102">How to: Use the BetweenShowDelay Property</span></span>
<span data-ttu-id="a0a47-103">Cet exemple montre comment utiliser le <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriété temporelle afin que les info-bulles apparaissent rapidement, avec peu ou pas de délai, lorsqu’un utilisateur déplace le pointeur de la souris à partir d’une info-bulle directement à un autre.</span><span class="sxs-lookup"><span data-stu-id="a0a47-103">This example shows how to use the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> time property so that tooltips appear quickly—with little or no delay—when a user moves the mouse pointer from one tooltip directly to another.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0a47-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="a0a47-104">Example</span></span>  
 <span data-ttu-id="a0a47-105">Dans l’exemple suivant, la <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> est définie sur une seconde (1000 millisecondes) et le <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> est défini à deux secondes (2 000 millisecondes) pour les info-bulles des deux <xref:System.Windows.Shapes.Ellipse> contrôles.</span><span class="sxs-lookup"><span data-stu-id="a0a47-105">In the following example, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> property is set to one second (1000 milliseconds) and the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> is set to two seconds (2000 milliseconds) for the tooltips of both <xref:System.Windows.Shapes.Ellipse> controls.</span></span> <span data-ttu-id="a0a47-106">Si vous l’info-bulle pour l’une des ellipses et puis déplacez le pointeur de la souris à un autre ellipse dans les deux secondes et pause sur celle-ci, l’info-bulle de la deuxième ellipse s’affiche immédiatement.</span><span class="sxs-lookup"><span data-stu-id="a0a47-106">If you display the tooltip for one of the ellipses and then move the mouse pointer to another ellipse within two seconds and pause on it, the tooltip of the second ellipse displays immediately.</span></span>  
  
 <span data-ttu-id="a0a47-107">Dans un des scénarios suivants, le <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> s’applique, ce qui entraîne l’info-bulle de la deuxième ellipse à attendre une seconde avant d’apparaître :</span><span class="sxs-lookup"><span data-stu-id="a0a47-107">In either of the following scenarios, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> applies, which causes the tooltip for the second ellipse to wait one second before it appears:</span></span>  
  
-   <span data-ttu-id="a0a47-108">Si le temps nécessaire pour atteindre le deuxième bouton est plus de deux secondes.</span><span class="sxs-lookup"><span data-stu-id="a0a47-108">If the time it takes to move to the second button is more than two seconds.</span></span>  
  
-   <span data-ttu-id="a0a47-109">Si l’info-bulle n’est pas visible au début de l’intervalle de temps pour la première ellipse.</span><span class="sxs-lookup"><span data-stu-id="a0a47-109">If the tooltip is not visible at the beginning of the time interval for the first ellipse.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="a0a47-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0a47-110">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="a0a47-111">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="a0a47-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="a0a47-112">Vue d’ensemble de l’info-bulle</span><span class="sxs-lookup"><span data-stu-id="a0a47-112">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)
