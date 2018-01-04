---
title: "StatusBar, contrôle (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 945d9a658dd3d75dd0edb9f4eaca78334ee4d652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="49502-102">StatusBar, contrôle (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="49502-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="49502-103">Le contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> remplace le contrôle <xref:System.Windows.Forms.StatusBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.StatusBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="49502-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="49502-104">Le contrôle <xref:System.Windows.Forms.StatusBar> Windows Forms est utilisé dans les formulaires tels que les zones, qui s'affichent habituellement au bas d'une fenêtre, et dans lesquelles une application peut afficher différents types d'informations d'état.</span><span class="sxs-lookup"><span data-stu-id="49502-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="49502-105"><xref:System.Windows.Forms.StatusBar>les contrôles peuvent avoir des panneaux de barre d’état sur les qui affichent des icônes pour indiquer l’état, ou une série d’icônes dans une animation indiquant qu’un processus fonctionne ; par exemple, Microsoft Word indiquant que le document est en cours enregistré.</span><span class="sxs-lookup"><span data-stu-id="49502-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49502-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="49502-106">In This Section</span></span>  
 [<span data-ttu-id="49502-107">Vue d’ensemble du contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="49502-107">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="49502-108">Présente les concepts généraux de le <xref:System.Windows.Forms.StatusBar> contrôle, ce qui permet aux utilisateurs d’afficher des informations pertinentes pour le contrôle qui a le focus.</span><span class="sxs-lookup"><span data-stu-id="49502-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="49502-109">Guide pratique pour ajouter des panneaux à un contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="49502-109">How to: Add Panels to a StatusBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="49502-110">Explique comment ajouter des panneaux programmables à le <xref:System.Windows.Forms.StatusBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="49502-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="49502-111">Guide pratique pour déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l’utilisateur a cliqué</span><span class="sxs-lookup"><span data-stu-id="49502-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="49502-112">Explique comment gérer <xref:System.Windows.Forms.Control.Click> les événements déclenchés à partir de la <xref:System.Windows.Forms.StatusBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="49502-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="49502-113">Guide pratique pour définir la taille des panneaux de la barre d'état</span><span class="sxs-lookup"><span data-stu-id="49502-113">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="49502-114">Fournit des détails sur les propriétés qui contrôlent la largeur et de redimensionnement le comportement des volets de barre d’état en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="49502-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="49502-115">Procédure pas à pas : mise à jour des informations de barre d'état au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="49502-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="49502-116">Explique comment contrôler par programme les données dans des panneaux de barre d’état.</span><span class="sxs-lookup"><span data-stu-id="49502-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="49502-117">Référence</span><span class="sxs-lookup"><span data-stu-id="49502-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="49502-118">Fournit des informations de référence sur la classe et ses membres.</span><span class="sxs-lookup"><span data-stu-id="49502-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="49502-119">Remplace et ajoute des fonctionnalités à la <xref:System.Windows.Forms.StatusBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="49502-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="49502-120">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="49502-120">Related Sections</span></span>  
 [<span data-ttu-id="49502-121">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49502-121">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="49502-122">Fournit une liste complète de contrôles Windows Forms, avec des liens vers des informations sur leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="49502-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
