---
title: "Vue d'ensemble du contrôle ToolStripContainer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a1a4c9c77e1f347f95c0a5e17ab0d37e0013d6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="48acd-102">Vue d'ensemble du contrôle ToolStripContainer</span><span class="sxs-lookup"><span data-stu-id="48acd-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="48acd-103">A <xref:System.Windows.Forms.ToolStripContainer> a des panneaux sur sa gauche, droite, haut et quatre côtés pour le positionnement et le rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, et <xref:System.Windows.Forms.StatusStrip> contrôles.</span><span class="sxs-lookup"><span data-stu-id="48acd-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="48acd-104">Plusieurs contrôles <xref:System.Windows.Forms.ToolStrip> s'empilent verticalement si vous les placez dans le <xref:System.Windows.Forms.ToolStripContainer> de gauche ou de droite.</span><span class="sxs-lookup"><span data-stu-id="48acd-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="48acd-105">Ils s'empilent horizontalement si vous les placez dans le <xref:System.Windows.Forms.ToolStripContainer> du haut ou du bas.</span><span class="sxs-lookup"><span data-stu-id="48acd-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="48acd-106">Vous pouvez utiliser le <xref:System.Windows.Forms.ToolStripContentPanel> central du <xref:System.Windows.Forms.ToolStripContainer> pour positionner les contrôles traditionnels sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="48acd-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="48acd-107">Tous les contrôles <xref:System.Windows.Forms.ToolStripContainer> sont directement sélectionnables au moment du design et peuvent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="48acd-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="48acd-108">Chaque panneau de configuration d’un <xref:System.Windows.Forms.ToolStripContainer> est extensible et réductible et peut être redimensionné avec les contrôles qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="48acd-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="48acd-109">Membres ToolStripContainer importants</span><span class="sxs-lookup"><span data-stu-id="48acd-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="48acd-110">Name</span><span class="sxs-lookup"><span data-stu-id="48acd-110">Name</span></span>|<span data-ttu-id="48acd-111">Description</span><span class="sxs-lookup"><span data-stu-id="48acd-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="48acd-112">Obtient le panneau inférieur de la <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="48acd-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="48acd-113">Obtient ou définit une valeur indiquant si le panneau inférieur de la <xref:System.Windows.Forms.ToolStripContainer> est visible.</span><span class="sxs-lookup"><span data-stu-id="48acd-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="48acd-114">Obtient le panneau gauche de la <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="48acd-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="48acd-115">Obtient ou définit une valeur indiquant si le panneau gauche de la <xref:System.Windows.Forms.ToolStripContainer> est visible.</span><span class="sxs-lookup"><span data-stu-id="48acd-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="48acd-116">Obtient le panneau droit de la <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="48acd-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="48acd-117">Obtient ou définit une valeur indiquant si le volet droit de la <xref:System.Windows.Forms.ToolStripContainer> est visible.</span><span class="sxs-lookup"><span data-stu-id="48acd-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="48acd-118">Obtient le panneau supérieur de la <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="48acd-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="48acd-119">Obtient ou définit une valeur indiquant si le panneau supérieur de la <xref:System.Windows.Forms.ToolStripContainer> est visible.</span><span class="sxs-lookup"><span data-stu-id="48acd-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48acd-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48acd-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>
