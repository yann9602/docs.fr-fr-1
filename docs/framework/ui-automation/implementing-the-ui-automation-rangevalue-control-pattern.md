---
title: "Implémentation du modèle de contrôle RangeValue d'UI Automation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9ae70f1dfc4c0a8d97d2fbcfd23822450727e59e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="81334-102">Implémentation du modèle de contrôle RangeValue d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="81334-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="81334-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="81334-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="81334-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="81334-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="81334-105">Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IRangeValueProvider>, notamment des informations sur les événements et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="81334-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="81334-106">Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="81334-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="81334-107">Le modèle de contrôle <xref:System.Windows.Automation.RangeValuePattern> est utilisé pour prendre en charge les contrôles auxquels vous pouvez affecter une valeur comprise dans une plage.</span><span class="sxs-lookup"><span data-stu-id="81334-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="81334-108">Pour obtenir des exemples de contrôles qui implémentent ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="81334-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="81334-109">Conventions et directives d'implémentation</span><span class="sxs-lookup"><span data-stu-id="81334-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="81334-110">Quand vous implémentez le modèle de contrôle RangeValue, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="81334-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="81334-111">Les contrôles autorisent le réétalonnage de leurs propriétés prises en charge en fonction des paramètres régionaux ou des préférences de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="81334-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="81334-112">Par exemple, vous pouvez définir un contrôle de thermomètre pour afficher la température en degrés Fahrenheit ou Celsius.</span><span class="sxs-lookup"><span data-stu-id="81334-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
-   <span data-ttu-id="81334-113">Les contrôles qui ont des valeurs de plage ambiguës, telles que les barres de progression ou les curseurs, doivent normaliser ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="81334-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="81334-114">![Barre de progression. ] (../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="81334-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="81334-115">Exemple d’une barre de progression où la valeur est de type entier, et où les valeurs de propriété minimale et maximale sont normalisées à 0 et 100, respectivement</span><span class="sxs-lookup"><span data-stu-id="81334-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="81334-116">Membres obligatoires pour IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="81334-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="81334-117">Membre obligatoire</span><span class="sxs-lookup"><span data-stu-id="81334-117">Required member</span></span>|<span data-ttu-id="81334-118">Type de membre</span><span class="sxs-lookup"><span data-stu-id="81334-118">Member type</span></span>|<span data-ttu-id="81334-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="81334-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="81334-120">Propriété</span><span class="sxs-lookup"><span data-stu-id="81334-120">Property</span></span>|<span data-ttu-id="81334-121">Aucun</span><span class="sxs-lookup"><span data-stu-id="81334-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="81334-122">Propriété</span><span class="sxs-lookup"><span data-stu-id="81334-122">Property</span></span>|<span data-ttu-id="81334-123">Aucun</span><span class="sxs-lookup"><span data-stu-id="81334-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="81334-124">Propriété</span><span class="sxs-lookup"><span data-stu-id="81334-124">Property</span></span>|<span data-ttu-id="81334-125">Aucun</span><span class="sxs-lookup"><span data-stu-id="81334-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="81334-126">Propriété</span><span class="sxs-lookup"><span data-stu-id="81334-126">Property</span></span>|<span data-ttu-id="81334-127">Aucun</span><span class="sxs-lookup"><span data-stu-id="81334-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="81334-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="81334-128">Property</span></span>|<span data-ttu-id="81334-129">Aucun</span><span class="sxs-lookup"><span data-stu-id="81334-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="81334-130">Propriété</span><span class="sxs-lookup"><span data-stu-id="81334-130">Property</span></span>|<span data-ttu-id="81334-131">Aucun</span><span class="sxs-lookup"><span data-stu-id="81334-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="81334-132">Méthodes</span><span class="sxs-lookup"><span data-stu-id="81334-132">Methods</span></span>|<span data-ttu-id="81334-133">Aucun</span><span class="sxs-lookup"><span data-stu-id="81334-133">None</span></span>|  
  
 <span data-ttu-id="81334-134">Ce modèle de contrôle n’est associé aucun événement.</span><span class="sxs-lookup"><span data-stu-id="81334-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="81334-135">Exceptions</span><span class="sxs-lookup"><span data-stu-id="81334-135">Exceptions</span></span>  
 <span data-ttu-id="81334-136">Les fournisseurs doivent lever les exceptions suivantes.</span><span class="sxs-lookup"><span data-stu-id="81334-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="81334-137">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="81334-137">Exception type</span></span>|<span data-ttu-id="81334-138">Condition</span><span class="sxs-lookup"><span data-stu-id="81334-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="81334-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> est appelé avec une valeur supérieure à <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> , ou inférieure à <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="81334-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81334-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81334-140">See Also</span></span>  
 [<span data-ttu-id="81334-141">Vue d’ensemble du modèles contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="81334-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="81334-142">Prise en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="81334-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="81334-143">Modèles de contrôle UI Automation pour les Clients</span><span class="sxs-lookup"><span data-stu-id="81334-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="81334-144">Vue d’ensemble d’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="81334-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="81334-145">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="81334-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
