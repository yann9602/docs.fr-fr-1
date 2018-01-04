---
title: "Comment : créer un effet de substitution à l'aide d'événements"
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
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fc65c9342cc86d4ceebd65e91c05cc1bea464e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="62bee-102">Comment : créer un effet de substitution à l'aide d'événements</span><span class="sxs-lookup"><span data-stu-id="62bee-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="62bee-103">Cet exemple montre comment modifier la couleur d’un élément que le pointeur de la souris entre et sort de la zone occupée par l’élément.</span><span class="sxs-lookup"><span data-stu-id="62bee-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="62bee-104">Cet exemple se compose d’un [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier et un fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="62bee-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62bee-105">Cet exemple montre comment utiliser des événements, mais la méthode recommandée pour parvenir à ce même effet consiste à utiliser un <xref:System.Windows.Trigger> dans un style.</span><span class="sxs-lookup"><span data-stu-id="62bee-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="62bee-106">Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="62bee-106">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62bee-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="62bee-107">Example</span></span>  
 <span data-ttu-id="62bee-108">Les éléments suivants [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] crée l’interface utilisateur, qui se compose de <xref:System.Windows.Controls.Border> autour un <xref:System.Windows.Controls.TextBlock>et l’attache le <xref:System.Windows.Input.Mouse.MouseEnter> et <xref:System.Windows.UIElement.MouseLeave> gestionnaires d’événements pour le <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="62bee-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="62bee-109">Le code-behind suivant crée le <xref:System.Windows.UIElement.MouseEnter> et <xref:System.Windows.UIElement.MouseLeave> gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="62bee-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="62bee-110">Lorsque le pointeur de la souris entre dans le <xref:System.Windows.Controls.Border>, l’arrière-plan de la <xref:System.Windows.Controls.Border> est modifié en rouge.</span><span class="sxs-lookup"><span data-stu-id="62bee-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="62bee-111">Lorsque le pointeur de la souris quitte le <xref:System.Windows.Controls.Border>, l’arrière-plan de la <xref:System.Windows.Controls.Border> repasse au blanc.</span><span class="sxs-lookup"><span data-stu-id="62bee-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
