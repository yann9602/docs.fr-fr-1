---
title: "Comment : partitionner l'espace à l'aide de l'élément DockPanel"
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
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 056aeaf1dfb7db420ce5359849a9a409dcd3fe13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="c7e48-102">Comment : partitionner l'espace à l'aide de l'élément DockPanel</span><span class="sxs-lookup"><span data-stu-id="c7e48-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="c7e48-103">L’exemple suivant crée un simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] à l’aide du framework un <xref:System.Windows.Controls.DockPanel> élément.</span><span class="sxs-lookup"><span data-stu-id="c7e48-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="c7e48-104">Le <xref:System.Windows.Controls.DockPanel> partitionne l’espace disponible pour ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="c7e48-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7e48-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="c7e48-105">Example</span></span>  
 <span data-ttu-id="c7e48-106">Cet exemple utilise le <xref:System.Windows.Controls.DockPanel.Dock%2A> propriété, qui est une propriété jointe, pour ancrer deux identiques <xref:System.Windows.Controls.Border> éléments à la <xref:System.Windows.Controls.Dock.Top> de l’espace partitionné.</span><span class="sxs-lookup"><span data-stu-id="c7e48-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="c7e48-107">Une troisième <xref:System.Windows.Controls.Border> élément est ancré à le <xref:System.Windows.Controls.Dock.Left>, avec sa largeur définie sur 200 pixels.</span><span class="sxs-lookup"><span data-stu-id="c7e48-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="c7e48-108">Un quatrième <xref:System.Windows.Controls.Border> est ancré sur le <xref:System.Windows.Controls.Dock.Bottom> de l’écran.</span><span class="sxs-lookup"><span data-stu-id="c7e48-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="c7e48-109">La dernière <xref:System.Windows.Controls.Border> élément remplit automatiquement l’espace restant.</span><span class="sxs-lookup"><span data-stu-id="c7e48-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  <span data-ttu-id="c7e48-110">Par défaut, le dernier enfant d’un <xref:System.Windows.Controls.DockPanel> élément remplit l’espace non alloué restant.</span><span class="sxs-lookup"><span data-stu-id="c7e48-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="c7e48-111">Si ce comportement ne vous convient pas, définissez `LastChildFill="False"`.</span><span class="sxs-lookup"><span data-stu-id="c7e48-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="c7e48-112">L’application compilée produit une nouvelle IU qui ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="c7e48-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="c7e48-113">![Scénario classique d’utilisation de l’élément DockPanel.](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="c7e48-113">![A typical DockPanel scenario.](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e48-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7e48-114">See Also</span></span>  
 <xref:System.Windows.Controls.DockPanel>  
 [<span data-ttu-id="c7e48-115">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="c7e48-115">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
