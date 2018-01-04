---
title: "Vue d'ensemble du contrôle TrackBar (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e62fc49a8a08c79138df080246b99b6fe891162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="trackbar-control-overview-windows-forms"></a><span data-ttu-id="37215-102">Vue d'ensemble du contrôle TrackBar (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="37215-102">TrackBar Control Overview (Windows Forms)</span></span>
<span data-ttu-id="37215-103">Windows Forms <xref:System.Windows.Forms.TrackBar> contrôle (parfois également appelé contrôle « slider ») est utilisé pour naviguer dans une grande quantité d’informations ou d’ajuster visuellement un paramètre numérique.</span><span class="sxs-lookup"><span data-stu-id="37215-103">The Windows Forms <xref:System.Windows.Forms.TrackBar> control (also sometimes called a "slider" control) is used for navigating through a large amount of information or for visually adjusting a numeric setting.</span></span> <span data-ttu-id="37215-104">Le <xref:System.Windows.Forms.TrackBar> contrôle comporte deux parties : le curseur de défilement, également appelé un curseur et les marques de graduation.</span><span class="sxs-lookup"><span data-stu-id="37215-104">The <xref:System.Windows.Forms.TrackBar> control has two parts: the thumb, also known as a slider, and the tick marks.</span></span> <span data-ttu-id="37215-105">Le curseur est la partie qui peut être ajustée.</span><span class="sxs-lookup"><span data-stu-id="37215-105">The thumb is the part that can be adjusted.</span></span> <span data-ttu-id="37215-106">Sa position correspond à la <xref:System.Windows.Forms.TrackBar.Value%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="37215-106">Its position corresponds to the <xref:System.Windows.Forms.TrackBar.Value%2A> property.</span></span> <span data-ttu-id="37215-107">Les graduations sont des indicateurs visuels qui sont exécutées à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="37215-107">The tick marks are visual indicators that are spaced at regular intervals.</span></span> <span data-ttu-id="37215-108">La barre de suivi se déplace dans les incréments que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="37215-108">The trackbar moves in increments that you specify and can be aligned horizontally or vertically.</span></span> <span data-ttu-id="37215-109">Par exemple, vous pouvez utiliser la barre de suivi pour contrôler la souris ou le taux de clignotement du curseur pour un système.</span><span class="sxs-lookup"><span data-stu-id="37215-109">For example, you might use the track bar to control the cursor blink rate or mouse speed for a system.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="37215-110">Propriétés de clé</span><span class="sxs-lookup"><span data-stu-id="37215-110">Key Properties</span></span>  
 <span data-ttu-id="37215-111">Les propriétés de clé de la <xref:System.Windows.Forms.TrackBar> contrôle sont <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, et <xref:System.Windows.Forms.TrackBar.Maximum%2A>.</span><span class="sxs-lookup"><span data-stu-id="37215-111">The key properties of the <xref:System.Windows.Forms.TrackBar> control are <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, and <xref:System.Windows.Forms.TrackBar.Maximum%2A>.</span></span> <span data-ttu-id="37215-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A>correspond à l’espacement des graduations.</span><span class="sxs-lookup"><span data-stu-id="37215-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A> is the spacing of the ticks.</span></span> <span data-ttu-id="37215-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A>et <xref:System.Windows.Forms.TrackBar.Maximum%2A> sont les valeurs minimale et maximale pouvant être représentées sur la barre de suivi.</span><span class="sxs-lookup"><span data-stu-id="37215-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A> and <xref:System.Windows.Forms.TrackBar.Maximum%2A> are the smallest and largest values that can be represented on the track bar.</span></span>  
  
 <span data-ttu-id="37215-114">Deux autres propriétés importantes sont <xref:System.Windows.Forms.TrackBar.SmallChange%2A> et <xref:System.Windows.Forms.TrackBar.LargeChange%2A>.</span><span class="sxs-lookup"><span data-stu-id="37215-114">Two other important properties are <xref:System.Windows.Forms.TrackBar.SmallChange%2A> and <xref:System.Windows.Forms.TrackBar.LargeChange%2A>.</span></span> <span data-ttu-id="37215-115">La valeur de la <xref:System.Windows.Forms.TrackBar.SmallChange%2A> propriété est le nombre de positions le curseur se déplace en réponse à disposer de la touche gauche ou droite.</span><span class="sxs-lookup"><span data-stu-id="37215-115">The value of the <xref:System.Windows.Forms.TrackBar.SmallChange%2A> property is the number of positions the thumb moves in response to having the LEFT or RIGHT ARROW key pressed.</span></span> <span data-ttu-id="37215-116">La valeur de la <xref:System.Windows.Forms.TrackBar.LargeChange%2A> propriété est le nombre de positions le curseur se déplace en réponse lorsque la PAGE précédente ou PAGE suivante touche ou en réponse à la souris clique sur la barre de suivi de chaque côté du curseur.</span><span class="sxs-lookup"><span data-stu-id="37215-116">The value of the <xref:System.Windows.Forms.TrackBar.LargeChange%2A> property is the number of positions the thumb moves in response to having the PAGE UP or PAGE DOWN key pressed, or in response to mouse clicks on the track bar on either side of the thumb.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37215-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37215-117">See Also</span></span>  
 <xref:System.Windows.Forms.TrackBar>  
 [<span data-ttu-id="37215-118">TrackBar, contrôle</span><span class="sxs-lookup"><span data-stu-id="37215-118">TrackBar Control</span></span>](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
