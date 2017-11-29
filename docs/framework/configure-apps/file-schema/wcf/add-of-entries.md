---
title: '&lt;add&gt; de &lt;entries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d62236c604cd91c2dfe4b92cfaac4004fc18d439
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltentriesgt"></a><span data-ttu-id="d1914-102">&lt;add&gt; de &lt;entries&gt;</span><span class="sxs-lookup"><span data-stu-id="d1914-102">&lt;add&gt; of &lt;entries&gt;</span></span>
<span data-ttu-id="d1914-103">Représente une entrée de routage qui mappe un filtre à un point de terminaison client défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="d1914-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="d1914-104">Les messages correspondant à ce filtre sont envoyés à cette destination.</span><span class="sxs-lookup"><span data-stu-id="d1914-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="d1914-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d1914-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d1914-106">\<routage ></span><span class="sxs-lookup"><span data-stu-id="d1914-106">\<routing></span></span>  
<span data-ttu-id="d1914-107">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="d1914-107">\<routingTables></span></span>  
<span data-ttu-id="d1914-108">\<table ></span><span class="sxs-lookup"><span data-stu-id="d1914-108">\<table></span></span>  
<span data-ttu-id="d1914-109">\<entrées ></span><span class="sxs-lookup"><span data-stu-id="d1914-109">\<entries></span></span>  
<span data-ttu-id="d1914-110">\<add></span><span class="sxs-lookup"><span data-stu-id="d1914-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1914-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1914-111">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1914-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d1914-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d1914-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d1914-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1914-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="d1914-114">Attributes</span></span>  
  
|<span data-ttu-id="d1914-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="d1914-115">Attribute</span></span>|<span data-ttu-id="d1914-116">Description</span><span class="sxs-lookup"><span data-stu-id="d1914-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1914-117">backupList</span><span class="sxs-lookup"><span data-stu-id="d1914-117">backupList</span></span>|<span data-ttu-id="d1914-118">Chaîne qui spécifie une référence à une liste de sauvegarde de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d1914-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="d1914-119">Point de terminaison (endpoint)</span><span class="sxs-lookup"><span data-stu-id="d1914-119">endpoint</span></span>|<span data-ttu-id="d1914-120">Chaîne qui spécifie une référence à un point de terminaison client qui reçoit les messages correspondant au filtre indiqué par l'attribut `filterName`.</span><span class="sxs-lookup"><span data-stu-id="d1914-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="d1914-121">filterName</span><span class="sxs-lookup"><span data-stu-id="d1914-121">filterName</span></span>|<span data-ttu-id="d1914-122">Chaîne qui spécifie une référence à un élément de filtre.</span><span class="sxs-lookup"><span data-stu-id="d1914-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="d1914-123">priority</span><span class="sxs-lookup"><span data-stu-id="d1914-123">priority</span></span>|<span data-ttu-id="d1914-124">Entier qui spécifie la priorité de cette entrée.</span><span class="sxs-lookup"><span data-stu-id="d1914-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="d1914-125">Les entrées dans la table de routage sont évaluées selon leur priorité, 0 correspondant à la priorité la plus basse.</span><span class="sxs-lookup"><span data-stu-id="d1914-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="d1914-126">Toutes les entrées d'une priorité donnée sont évaluées simultanément, si aucune entrée correspondante n'est trouvée pour la priorité actuelle, le niveau de priorité suivant est évalué.</span><span class="sxs-lookup"><span data-stu-id="d1914-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="d1914-127">Cette valeur est facultative.</span><span class="sxs-lookup"><span data-stu-id="d1914-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1914-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d1914-128">Child Elements</span></span>  
 <span data-ttu-id="d1914-129">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d1914-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1914-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d1914-130">Parent Elements</span></span>  
  
|<span data-ttu-id="d1914-131">Élément</span><span class="sxs-lookup"><span data-stu-id="d1914-131">Element</span></span>|<span data-ttu-id="d1914-132">Description</span><span class="sxs-lookup"><span data-stu-id="d1914-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1914-133">\<routage ></span><span class="sxs-lookup"><span data-stu-id="d1914-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="d1914-134">Section de configuration qui contient les entrées de mappage de routage.</span><span class="sxs-lookup"><span data-stu-id="d1914-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1914-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1914-135">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
