---
title: "&lt;entrées&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b6d8d1c3797d60b26443e07cc527ea8b86f526e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltentriesgt"></a><span data-ttu-id="de829-102">&lt;entrées&gt;</span><span class="sxs-lookup"><span data-stu-id="de829-102">&lt;entries&gt;</span></span>
<span data-ttu-id="de829-103">Entrée de routage qui contient des mappages entre les filtres de routage et les points de terminaison cibles vers lesquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="de829-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="de829-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="de829-104">\<system.serviceModel></span></span>  
<span data-ttu-id="de829-105">\<routage ></span><span class="sxs-lookup"><span data-stu-id="de829-105">\<routing></span></span>  
<span data-ttu-id="de829-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="de829-106">\<routingTables></span></span>  
<span data-ttu-id="de829-107">\<table ></span><span class="sxs-lookup"><span data-stu-id="de829-107">\<table></span></span>  
<span data-ttu-id="de829-108">\<entrées ></span><span class="sxs-lookup"><span data-stu-id="de829-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de829-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de829-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="de829-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="de829-110">Attributes and Elements</span></span>  
 <span data-ttu-id="de829-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="de829-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de829-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="de829-112">Attributes</span></span>  
 <span data-ttu-id="de829-113">Aucun</span><span class="sxs-lookup"><span data-stu-id="de829-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de829-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="de829-114">Child Elements</span></span>  
  
|<span data-ttu-id="de829-115">Élément</span><span class="sxs-lookup"><span data-stu-id="de829-115">Element</span></span>|<span data-ttu-id="de829-116">Description</span><span class="sxs-lookup"><span data-stu-id="de829-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de829-117">\<filtres ></span><span class="sxs-lookup"><span data-stu-id="de829-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="de829-118">Mappe un filtre à un point de terminaison client précédemment défini.</span><span class="sxs-lookup"><span data-stu-id="de829-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="de829-119">Les messages correspondant à ce filtre sont envoyés à cette destination.</span><span class="sxs-lookup"><span data-stu-id="de829-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de829-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="de829-120">Parent Elements</span></span>  
  
|<span data-ttu-id="de829-121">Élément</span><span class="sxs-lookup"><span data-stu-id="de829-121">Element</span></span>|<span data-ttu-id="de829-122">Description</span><span class="sxs-lookup"><span data-stu-id="de829-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de829-123">\<routage ></span><span class="sxs-lookup"><span data-stu-id="de829-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="de829-124">Section de configuration qui contient une table de routage.</span><span class="sxs-lookup"><span data-stu-id="de829-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de829-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de829-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
