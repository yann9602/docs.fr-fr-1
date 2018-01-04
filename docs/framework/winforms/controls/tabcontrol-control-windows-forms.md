---
title: "TabControl, contrôle (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TabControl control [Windows Forms]
- tab controls
- tab controls [Windows Forms], creating
- multipage dialog boxes
- dialog boxes [Windows Forms], creating multipage
- property pages [Windows Forms], creating
- tab dialog boxes
ms.assetid: 915091af-93ac-4d3d-8283-738dd2d21ea7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 705f9dbb8ea7f4d462a2b19cc0c6b845ae8f578b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="tabcontrol-control-windows-forms"></a><span data-ttu-id="5cfce-102">TabControl, contrôle (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5cfce-102">TabControl Control (Windows Forms)</span></span>
<span data-ttu-id="5cfce-103">Le `TabControl` Windows Forms affiche plusieurs onglets comparables aux intercalaires d'un agenda ou aux étiquettes d'un ensemble de dossiers dans un classeur.</span><span class="sxs-lookup"><span data-stu-id="5cfce-103">The Windows Forms `TabControl` displays multiple tabs, like dividers in a notebook or labels in a set of folders in a filing cabinet.</span></span> <span data-ttu-id="5cfce-104">Les onglets peuvent contenir des images et d'autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="5cfce-104">The tabs can contain pictures and other controls.</span></span> <span data-ttu-id="5cfce-105">Utilisez le `TabControl` pour créer des pages de propriétés.</span><span class="sxs-lookup"><span data-stu-id="5cfce-105">Use the `TabControl` to create property pages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5cfce-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5cfce-106">In This Section</span></span>  
 [<span data-ttu-id="5cfce-107">Vue d’ensemble du contrôle TabControl</span><span class="sxs-lookup"><span data-stu-id="5cfce-107">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="5cfce-108">Décrit ce contrôle et ses principales fonctionnalités et propriétés.</span><span class="sxs-lookup"><span data-stu-id="5cfce-108">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="5cfce-109">Guide pratique pour ajouter un contrôle à une page d'onglet</span><span class="sxs-lookup"><span data-stu-id="5cfce-109">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 <span data-ttu-id="5cfce-110">Explique comment afficher des contrôles sur des pages d'onglets.</span><span class="sxs-lookup"><span data-stu-id="5cfce-110">Gives directions for displaying controls on tab pages.</span></span>  
  
 [<span data-ttu-id="5cfce-111">Guide pratique pour ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cfce-111">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="5cfce-112">Explique comment ajouter et supprimer des onglets dans le concepteur ou dans le code.</span><span class="sxs-lookup"><span data-stu-id="5cfce-112">Gives directions for adding and removing tabs in the designer or in code.</span></span>  
  
 [<span data-ttu-id="5cfce-113">Guide pratique pour modifier l'apparence du contrôle TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cfce-113">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="5cfce-114">Explique comment définir les propriétés qui affectent l'apparence des différents onglets.</span><span class="sxs-lookup"><span data-stu-id="5cfce-114">Gives directions for adjusting properties that affect the appearance of individual tabs.</span></span>  
  
 [<span data-ttu-id="5cfce-115">Guide pratique pour désactiver les pages d'onglets</span><span class="sxs-lookup"><span data-stu-id="5cfce-115">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 <span data-ttu-id="5cfce-116">Explique comment restreindre l'accès à une page d'onglet, éventuellement en fonction des informations d'identification de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5cfce-116">Explains how to restrict access to a tab page, possibly based on user credentials.</span></span>  
  
 <span data-ttu-id="5cfce-117">Consultez également [Comment : ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms à l’aide du concepteur](http://msdn.microsoft.com/library/ms233654\(v=vs.110\)), [Comment : ajouter un contrôle à une Page onglet à l’aide du Concepteur](http://msdn.microsoft.com/library/ms233668\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="5cfce-117">Also see [How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer](http://msdn.microsoft.com/library/ms233654\(v=vs.110\)), [How to: Add a Control to a Tab Page Using the Designer](http://msdn.microsoft.com/library/ms233668\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5cfce-118">Référence</span><span class="sxs-lookup"><span data-stu-id="5cfce-118">Reference</span></span>  
 <span data-ttu-id="5cfce-119">Classe <xref:System.Windows.Forms.TabControl></span><span class="sxs-lookup"><span data-stu-id="5cfce-119"><xref:System.Windows.Forms.TabControl> class</span></span>  
 <span data-ttu-id="5cfce-120">Décrit cette classe et fournit des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="5cfce-120">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5cfce-121">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="5cfce-121">Related Sections</span></span>  
 [<span data-ttu-id="5cfce-122">Boîtes de dialogue dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cfce-122">Dialog Boxes in Windows Forms</span></span>](../../../../docs/framework/winforms/dialog-boxes-in-windows-forms.md)  
 <span data-ttu-id="5cfce-123">Fournit une liste de tâches pour les boîtes de dialogue, qui contiennent souvent des onglets.</span><span class="sxs-lookup"><span data-stu-id="5cfce-123">Provides a list of tasks for dialog boxes, which often display tabs.</span></span>  
  
 [<span data-ttu-id="5cfce-124">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cfce-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="5cfce-125">Fournit une liste complète de contrôles Windows Forms, avec des liens vers des informations sur leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="5cfce-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
