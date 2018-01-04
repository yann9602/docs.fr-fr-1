---
title: "Vue d'ensemble du contrôle ToolStripProgressBar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripProgressBar
helpviewer_keywords:
- toolbars [Windows Forms], progress bars
- progress controls [Windows Forms]
- ToolStripProgressBar control [Windows Forms], about ToolStripProgressBar control
ms.assetid: ec3ab522-5fe4-4b4d-a551-bc19e84f4774
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ee73d87a65e9febed6ebd5ad981dcd548fc2404
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="toolstripprogressbar-control-overview"></a><span data-ttu-id="8f59a-102">Vue d'ensemble du contrôle ToolStripProgressBar</span><span class="sxs-lookup"><span data-stu-id="8f59a-102">ToolStripProgressBar Control Overview</span></span>
<span data-ttu-id="8f59a-103">Le <xref:System.Windows.Forms.ToolStripProgressBar> combine le rafting et les fonctionnalités de rendu de tous les <xref:System.Windows.Forms.ToolStrip> contrôles avec ses fonctionnalités de suivi de processus typiques.</span><span class="sxs-lookup"><span data-stu-id="8f59a-103">The <xref:System.Windows.Forms.ToolStripProgressBar> combines the rafting and rendering functionality of all <xref:System.Windows.Forms.ToolStrip> controls with its typical process-tracking functionality.</span></span> <span data-ttu-id="8f59a-104">A <xref:System.Windows.Forms.ToolStripProgressBar> est le plus souvent hébergée par <xref:System.Windows.Forms.StatusStrip>et moins souvent par une <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="8f59a-104">A <xref:System.Windows.Forms.ToolStripProgressBar> is most usually hosted by <xref:System.Windows.Forms.StatusStrip>, and less frequently by a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="8f59a-105">Bien que <xref:System.Windows.Forms.ToolStripProgressBar> remplace et ajoute des fonctionnalités pour le contrôle dans les versions précédentes, <xref:System.Windows.Forms.ToolStripProgressBar> est conservé pour la compatibilité descendante et l’utilisation future si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="8f59a-105">Although <xref:System.Windows.Forms.ToolStripProgressBar> replaces and adds functionality to the control in previous versions, <xref:System.Windows.Forms.ToolStripProgressBar> is retained for both backward compatibility and future use if desired.</span></span>  
  
### <a name="important-toolstripprogressbar-members"></a><span data-ttu-id="8f59a-106">Membres ToolStripProgressBar importants</span><span class="sxs-lookup"><span data-stu-id="8f59a-106">Important ToolStripProgressBar Members</span></span>  
  
|<span data-ttu-id="8f59a-107">Name</span><span class="sxs-lookup"><span data-stu-id="8f59a-107">Name</span></span>|<span data-ttu-id="8f59a-108">Description</span><span class="sxs-lookup"><span data-stu-id="8f59a-108">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripProgressBar.MarqueeAnimationSpeed%2A>|<span data-ttu-id="8f59a-109">Obtient ou définit une valeur représentant le délai entre chaque <xref:System.Windows.Forms.ProgressBarStyle.Marquee> afficher la mise à jour, en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="8f59a-109">Gets or sets a value representing the delay between each <xref:System.Windows.Forms.ProgressBarStyle.Marquee> display update, in milliseconds.</span></span>|  
|<xref:System.Windows.Forms.ProgressBar.Maximum%2A>|<span data-ttu-id="8f59a-110">Obtient ou définit la limite supérieure de la plage qui est définie pour ce <xref:System.Windows.Forms.ToolStripProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="8f59a-110">Gets or sets the upper bound of the range that is defined for this <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Minimum%2A>|<span data-ttu-id="8f59a-111">Obtient ou définit la limite inférieure de la plage définie pour ce <xref:System.Windows.Forms.ToolStripProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="8f59a-111">Gets or sets the lower bound of the range that is defined for this <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Style%2A>|<span data-ttu-id="8f59a-112">Obtient ou définit le style qui le <xref:System.Windows.Forms.ToolStripProgressBar> utilise pour afficher la progression d’une opération.</span><span class="sxs-lookup"><span data-stu-id="8f59a-112">Gets or sets the style that the <xref:System.Windows.Forms.ToolStripProgressBar> uses to display the progress of an operation.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Value%2A>|<span data-ttu-id="8f59a-113">Obtient ou définit la valeur actuelle de la <xref:System.Windows.Forms.ToolStripProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="8f59a-113">Gets or sets the current value of the <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.PerformStep%2A>|<span data-ttu-id="8f59a-114">Avance la position actuelle de la barre de progression de la quantité de la <xref:System.Windows.Forms.ToolStripProgressBar.Step%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="8f59a-114">Advances the current position of the progress bar by the amount of the <xref:System.Windows.Forms.ToolStripProgressBar.Step%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f59a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f59a-115">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripProgressBar>
