---
title: "Vue d'ensemble du contrôle Splitter (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Splitter
helpviewer_keywords: Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32d8829e7303ce23a22d0a01f2428a889ce4ae0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="f0afc-102">Vue d'ensemble du contrôle Splitter (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f0afc-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="f0afc-103">Bien que <xref:System.Windows.Forms.SplitContainer> remplace et ajoute des fonctionnalités à la <xref:System.Windows.Forms.Splitter> contrôle des versions antérieures, <xref:System.Windows.Forms.Splitter> est conservé pour la compatibilité descendante et l’utilisation future si vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="f0afc-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="f0afc-104">Windows Forms <xref:System.Windows.Forms.Splitter> permettent de redimensionner des contrôles ancrés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f0afc-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="f0afc-105">Le <xref:System.Windows.Forms.Splitter> contrôle est souvent utilisé dans les formulaires dont les contrôles qui ont différentes longueurs de données à présent, comme l’Explorateur Windows, dont les volets de données contiennent des informations de longueur différente à différents moments.</span><span class="sxs-lookup"><span data-stu-id="f0afc-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="f0afc-106">Utilisation du contrôle Splitter</span><span class="sxs-lookup"><span data-stu-id="f0afc-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="f0afc-107">Lorsque l’utilisateur pointe le pointeur de la souris sur le bord non ancré d’un contrôle qui peut être redimensionné par un contrôle splitter, le pointeur change d’apparence pour indiquer que le contrôle peut être redimensionné.</span><span class="sxs-lookup"><span data-stu-id="f0afc-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="f0afc-108">Le contrôle splitter, l’utilisateur peut redimensionner le contrôle ancré qui précède immédiatement.</span><span class="sxs-lookup"><span data-stu-id="f0afc-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="f0afc-109">Par conséquent, pour permettre à l’utilisateur de redimensionner un contrôle ancré au moment de l’exécution, ancrez le contrôle doit être redimensionné à un bord d’un conteneur et Ancrez ensuite un contrôle splitter sur le même côté de ce conteneur.</span><span class="sxs-lookup"><span data-stu-id="f0afc-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0afc-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0afc-110">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="f0afc-111">Guide pratique pour fixer des contrôles sur des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f0afc-111">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [<span data-ttu-id="f0afc-112">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f0afc-112">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
