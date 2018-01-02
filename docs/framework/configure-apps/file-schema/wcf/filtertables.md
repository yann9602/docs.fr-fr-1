---
title: '&lt;filterTables&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 05c8d3f5ce5a01e5a88f37fce43f3b4f8d260812
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="a7f95-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="a7f95-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="a7f95-103">Représente une section de configuration permettant de définir des tables de routage qui contiennent des mappages entre les filtres de routage et les points de terminaison cibles auxquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="a7f95-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="a7f95-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a7f95-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a7f95-105">\<routage ></span><span class="sxs-lookup"><span data-stu-id="a7f95-105">\<routing></span></span>  
<span data-ttu-id="a7f95-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="a7f95-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f95-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7f95-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a7f95-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a7f95-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a7f95-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a7f95-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7f95-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="a7f95-110">Attributes</span></span>  
 <span data-ttu-id="a7f95-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a7f95-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a7f95-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a7f95-112">Child Elements</span></span>  
  
|<span data-ttu-id="a7f95-113">Élément</span><span class="sxs-lookup"><span data-stu-id="a7f95-113">Element</span></span>|<span data-ttu-id="a7f95-114">Description</span><span class="sxs-lookup"><span data-stu-id="a7f95-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7f95-115">\<filtres ></span><span class="sxs-lookup"><span data-stu-id="a7f95-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="a7f95-116">Table de routage qui contient des mappages entre les filtres de routage et les points de terminaison cibles vers lesquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="a7f95-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7f95-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a7f95-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a7f95-118">Élément</span><span class="sxs-lookup"><span data-stu-id="a7f95-118">Element</span></span>|<span data-ttu-id="a7f95-119">Description</span><span class="sxs-lookup"><span data-stu-id="a7f95-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7f95-120">\<routage ></span><span class="sxs-lookup"><span data-stu-id="a7f95-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="a7f95-121">Section de configuration qui contient des filtres de routage et des tables de routage.</span><span class="sxs-lookup"><span data-stu-id="a7f95-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7f95-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7f95-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
