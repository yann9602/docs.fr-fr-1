---
title: "Implémentation du modèle de contrôle Window d'UI Automation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 3f1b44184f1a241943d9fa9d60a62a703dbaf0d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="6e6fb-102">Implémentation du modèle de contrôle Window d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="6e6fb-102">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="6e6fb-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6e6fb-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="6e6fb-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="6e6fb-105">Cette rubrique présente des conventions et des directives pour implémenter <xref:System.Windows.Automation.Provider.IWindowProvider>, notamment des informations sur les propriétés, méthodes et événements <xref:System.Windows.Automation.WindowPattern> .</span><span class="sxs-lookup"><span data-stu-id="6e6fb-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="6e6fb-106">Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="6e6fb-107">Le modèle de contrôle <xref:System.Windows.Automation.WindowPattern> est utilisé pour prendre en charge les contrôles qui fournissent une fonctionnalité de fenêtre fondamentale dans une [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)]traditionnelle.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-107">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)].</span></span> <span data-ttu-id="6e6fb-108">Les contrôles qui doivent implémenter ce modèle de contrôle sont notamment les fenêtres d’application de niveau supérieur, les fenêtres enfants de l’ [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] , les contrôles de volet de fractionnement redimensionnables, les boîtes de dialogue modales et les fenêtres d’info-bulle.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-108">Examples of controls that must implement this control pattern include top-level application windows, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="6e6fb-109">Conventions et recommandations en matière d'implémentation</span><span class="sxs-lookup"><span data-stu-id="6e6fb-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="6e6fb-110">Quand vous implémentez le modèle de contrôle Window, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6e6fb-110">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="6e6fb-111">Pour prendre en charge la possibilité de modifier la taille de la fenêtre et la position de l’écran à l’aide d’UI Automation, un contrôle doit implémenter <xref:System.Windows.Automation.Provider.ITransformProvider> en plus de <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-111">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="6e6fb-112">Les contrôles qui contiennent des barres de titre et des éléments de barre de titre qui permettent de déplacer, redimensionner, agrandir, réduire ou fermer le contrôle sont généralement obligatoires pour implémenter <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-112">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="6e6fb-113">En général, les contrôles tels que les info-bulles contextuelles, les zones de liste modifiable ou les menus déroulants n’implémentent pas <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-113">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="6e6fb-114">Les fenêtres d’info-bulle se distinguent des info-bulles contextuelles de base par un bouton Fermer identique à celui des fenêtres.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-114">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
-   <span data-ttu-id="6e6fb-115">Le mode plein écran n’est pas pris en charge par IWindowProvider, car il est propre à la fonctionnalité d’une application et n’est pas un comportement standard de fenêtre.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-115">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="6e6fb-116">Membres obligatoires pour IWindowProvider</span><span class="sxs-lookup"><span data-stu-id="6e6fb-116">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="6e6fb-117">Les propriétés, méthodes et événements suivants sont obligatoires pour l’interface IWindowProvider.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-117">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="6e6fb-118">Membre obligatoire</span><span class="sxs-lookup"><span data-stu-id="6e6fb-118">Required member</span></span>|<span data-ttu-id="6e6fb-119">Type de membre</span><span class="sxs-lookup"><span data-stu-id="6e6fb-119">Member type</span></span>|<span data-ttu-id="6e6fb-120">Notes</span><span class="sxs-lookup"><span data-stu-id="6e6fb-120">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="6e6fb-121">Propriété</span><span class="sxs-lookup"><span data-stu-id="6e6fb-121">Property</span></span>|<span data-ttu-id="6e6fb-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="6e6fb-123">Propriété</span><span class="sxs-lookup"><span data-stu-id="6e6fb-123">Property</span></span>|<span data-ttu-id="6e6fb-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="6e6fb-125">Propriété</span><span class="sxs-lookup"><span data-stu-id="6e6fb-125">Property</span></span>|<span data-ttu-id="6e6fb-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="6e6fb-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="6e6fb-127">Property</span></span>|<span data-ttu-id="6e6fb-128">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="6e6fb-129">Propriété</span><span class="sxs-lookup"><span data-stu-id="6e6fb-129">Property</span></span>|<span data-ttu-id="6e6fb-130">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="6e6fb-131">Propriété</span><span class="sxs-lookup"><span data-stu-id="6e6fb-131">Property</span></span>|<span data-ttu-id="6e6fb-132">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="6e6fb-133">Méthode</span><span class="sxs-lookup"><span data-stu-id="6e6fb-133">Method</span></span>|<span data-ttu-id="6e6fb-134">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="6e6fb-135">Méthode</span><span class="sxs-lookup"><span data-stu-id="6e6fb-135">Method</span></span>|<span data-ttu-id="6e6fb-136">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="6e6fb-137">Méthode</span><span class="sxs-lookup"><span data-stu-id="6e6fb-137">Method</span></span>|<span data-ttu-id="6e6fb-138">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-138">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="6e6fb-139">événement</span><span class="sxs-lookup"><span data-stu-id="6e6fb-139">Event</span></span>|<span data-ttu-id="6e6fb-140">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="6e6fb-141">événement</span><span class="sxs-lookup"><span data-stu-id="6e6fb-141">Event</span></span>|<span data-ttu-id="6e6fb-142">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="6e6fb-143">événement</span><span class="sxs-lookup"><span data-stu-id="6e6fb-143">Event</span></span>|<span data-ttu-id="6e6fb-144">N’est pas nécessairement défini sur <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="6e6fb-144">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="6e6fb-145">Exceptions</span><span class="sxs-lookup"><span data-stu-id="6e6fb-145">Exceptions</span></span>  
 <span data-ttu-id="6e6fb-146">Les fournisseurs doivent lever les exceptions suivantes.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-146">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="6e6fb-147">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="6e6fb-147">Exception type</span></span>|<span data-ttu-id="6e6fb-148">Condition</span><span class="sxs-lookup"><span data-stu-id="6e6fb-148">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="6e6fb-149">-Lorsqu’un contrôle ne prend pas en charge un comportement demandé.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-149">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="6e6fb-150">-Lorsque le paramètre n’est pas un nombre valide.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-150">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e6fb-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e6fb-151">See Also</span></span>  
 [<span data-ttu-id="6e6fb-152">Vue d’ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="6e6fb-152">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="6e6fb-153">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="6e6fb-153">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="6e6fb-154">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="6e6fb-154">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="6e6fb-155">Présentation de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="6e6fb-155">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="6e6fb-156">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="6e6fb-156">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
