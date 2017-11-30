---
title: "Implémentation du modèle de contrôle Table d'UI Automation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4a1fbe175abf07eaccfd177c6e32f5515e88c4ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="8270e-102">Implémentation du modèle de contrôle Table d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="8270e-102">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="8270e-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="8270e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8270e-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="8270e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8270e-105">Cette rubrique présente les conventions et directives à respecter pour implémenter <xref:System.Windows.Automation.Provider.ITableProvider>, notamment les informations sur les propriétés, les méthodes et les événements.</span><span class="sxs-lookup"><span data-stu-id="8270e-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="8270e-106">Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.</span><span class="sxs-lookup"><span data-stu-id="8270e-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="8270e-107">Le <xref:System.Windows.Automation.TablePattern> modèle de contrôle est utilisé pour prendre en charge les contrôles qui agissent comme conteneurs pour une collection d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="8270e-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="8270e-108">Les enfants de cet élément doivent implémenter <xref:System.Windows.Automation.Provider.ITableItemProvider> et être organisés dans un système de coordonnées logiques à deux dimensions qui peut être parcouru par ligne et colonne.</span><span class="sxs-lookup"><span data-stu-id="8270e-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="8270e-109">Ce modèle de contrôle est analogue à <xref:System.Windows.Automation.Provider.IGridProvider>, à la différence que tout contrôle implémentant <xref:System.Windows.Automation.Provider.ITableProvider> doit également exposer une relation d’en-tête de colonne et/ou de ligne pour chaque élément enfant.</span><span class="sxs-lookup"><span data-stu-id="8270e-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="8270e-110">Pour obtenir des exemples de contrôles qui implémentent ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8270e-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8270e-111">Conventions et recommandations en matière d'implémentation</span><span class="sxs-lookup"><span data-stu-id="8270e-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8270e-112">Quand vous implémentez le modèle de contrôle Table, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8270e-112">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="8270e-113">Accès au contenu des cellules individuelles se fait via un système de coordonnées logiques à deux dimensions ou un tableau fourni par l’implémentation simultanée requise de <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="8270e-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
-   <span data-ttu-id="8270e-114">Un en-tête de colonne ou de ligne peut figurer dans un objet table ou être un objet d’en-tête séparé, associé à un objet table.</span><span class="sxs-lookup"><span data-stu-id="8270e-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
-   <span data-ttu-id="8270e-115">Les en-têtes de colonne et de ligne peuvent inclure un en-tête principal et des en-têtes de prise en charge quelconques.</span><span class="sxs-lookup"><span data-stu-id="8270e-115">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8270e-116">Ce concept est visible dans un [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] feuille de calcul dans laquelle un utilisateur a défini une colonne « Prénom ».</span><span class="sxs-lookup"><span data-stu-id="8270e-116">This concept becomes evident in a [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="8270e-117">Cette colonne a désormais deux en-têtes : l’en-tête « Prénom » défini par l’utilisateur et la désignation alphanumérique de cette colonne affectée par l’application.</span><span class="sxs-lookup"><span data-stu-id="8270e-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
-   <span data-ttu-id="8270e-118">Consultez [implémentant le modèle de contrôle Grid d’UI Automation](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) pour les fonctionnalités de grille associées.</span><span class="sxs-lookup"><span data-stu-id="8270e-118">See [Implementing the UI Automation Grid Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="8270e-119">![Table avec éléments d’en-tête complexes. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="8270e-119">![Table with complex header items.](../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="8270e-120">Exemple de table avec des en-têtes de colonne complexes</span><span class="sxs-lookup"><span data-stu-id="8270e-120">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="8270e-121">![Table avec propriété RowOrColumnMajor ambiguë. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="8270e-121">![Table with ambiguous RowOrColumnMajor property.](../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="8270e-122">Exemple de table avec une propriété RowOrColumnMajor ambiguë</span><span class="sxs-lookup"><span data-stu-id="8270e-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="8270e-123">Membres requis pour ITableProvider</span><span class="sxs-lookup"><span data-stu-id="8270e-123">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="8270e-124">Les propriétés et les méthodes suivantes sont requises pour l’interface ITableProvider.</span><span class="sxs-lookup"><span data-stu-id="8270e-124">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="8270e-125">Membres nécessaires</span><span class="sxs-lookup"><span data-stu-id="8270e-125">Required members</span></span>|<span data-ttu-id="8270e-126">Type de membre</span><span class="sxs-lookup"><span data-stu-id="8270e-126">Member type</span></span>|<span data-ttu-id="8270e-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="8270e-127">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="8270e-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="8270e-128">Property</span></span>|<span data-ttu-id="8270e-129">Aucune</span><span class="sxs-lookup"><span data-stu-id="8270e-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="8270e-130">Méthode</span><span class="sxs-lookup"><span data-stu-id="8270e-130">Method</span></span>|<span data-ttu-id="8270e-131">Aucune</span><span class="sxs-lookup"><span data-stu-id="8270e-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="8270e-132">Méthode</span><span class="sxs-lookup"><span data-stu-id="8270e-132">Method</span></span>|<span data-ttu-id="8270e-133">Aucune</span><span class="sxs-lookup"><span data-stu-id="8270e-133">None</span></span>|  
  
 <span data-ttu-id="8270e-134">Ce modèle de contrôle n’est associé aucun événement.</span><span class="sxs-lookup"><span data-stu-id="8270e-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="8270e-135">Exceptions</span><span class="sxs-lookup"><span data-stu-id="8270e-135">Exceptions</span></span>  
 <span data-ttu-id="8270e-136">Ce modèle de contrôle n’est associé à aucune exception.</span><span class="sxs-lookup"><span data-stu-id="8270e-136">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8270e-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8270e-137">See Also</span></span>  
 [<span data-ttu-id="8270e-138">Vue d’ensemble du modèles contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="8270e-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="8270e-139">Prise en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="8270e-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="8270e-140">Modèles de contrôle UI Automation pour les Clients</span><span class="sxs-lookup"><span data-stu-id="8270e-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="8270e-141">Implémentation du modèle de contrôle TableItem d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="8270e-141">Implementing the UI Automation TableItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [<span data-ttu-id="8270e-142">Implémenter le modèle de contrôle Grid d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="8270e-142">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [<span data-ttu-id="8270e-143">Vue d’ensemble d’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="8270e-143">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="8270e-144">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="8270e-144">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
