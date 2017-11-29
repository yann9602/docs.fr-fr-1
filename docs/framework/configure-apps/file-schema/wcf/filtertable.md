---
title: '&lt;filterTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04780d51cfd1d1d0049fc608cf7bd304be382b9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="f65ec-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="f65ec-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="f65ec-103">Représente une table de routage qui contient une liste de filtres pour évaluer des messages et router les messages vers le point de terminaison client si le filtre a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="f65ec-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="f65ec-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f65ec-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f65ec-105">\<routage ></span><span class="sxs-lookup"><span data-stu-id="f65ec-105">\<routing></span></span>  
<span data-ttu-id="f65ec-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="f65ec-106">\<routingTables></span></span>  
<span data-ttu-id="f65ec-107">\<table ></span><span class="sxs-lookup"><span data-stu-id="f65ec-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f65ec-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f65ec-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f65ec-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f65ec-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f65ec-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f65ec-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f65ec-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="f65ec-111">Attributes</span></span>  
  
|<span data-ttu-id="f65ec-112">Élément</span><span class="sxs-lookup"><span data-stu-id="f65ec-112">Element</span></span>|<span data-ttu-id="f65ec-113">Description</span><span class="sxs-lookup"><span data-stu-id="f65ec-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f65ec-114">name</span><span class="sxs-lookup"><span data-stu-id="f65ec-114">name</span></span>|<span data-ttu-id="f65ec-115">Chaîne qui contient le nom unique de cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="f65ec-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f65ec-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f65ec-116">Child Elements</span></span>  
  
|<span data-ttu-id="f65ec-117">Élément</span><span class="sxs-lookup"><span data-stu-id="f65ec-117">Element</span></span>|<span data-ttu-id="f65ec-118">Description</span><span class="sxs-lookup"><span data-stu-id="f65ec-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f65ec-119">\<filtres ></span><span class="sxs-lookup"><span data-stu-id="f65ec-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="f65ec-120">Mappages entre les filtres de routage et les points de terminaison cibles auxquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="f65ec-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f65ec-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f65ec-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f65ec-122">Élément</span><span class="sxs-lookup"><span data-stu-id="f65ec-122">Element</span></span>|<span data-ttu-id="f65ec-123">Description</span><span class="sxs-lookup"><span data-stu-id="f65ec-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f65ec-124">\<routage ></span><span class="sxs-lookup"><span data-stu-id="f65ec-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="f65ec-125">Section de configuration qui contient des tables de routage.</span><span class="sxs-lookup"><span data-stu-id="f65ec-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f65ec-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f65ec-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
