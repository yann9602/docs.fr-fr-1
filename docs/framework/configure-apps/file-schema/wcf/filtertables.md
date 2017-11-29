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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75e06b0258f2e4f65d441c25b5081cf7a6627518
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="761a0-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="761a0-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="761a0-103">Représente une section de configuration permettant de définir des tables de routage qui contiennent des mappages entre les filtres de routage et les points de terminaison cibles auxquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="761a0-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="761a0-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="761a0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="761a0-105">\<routage ></span><span class="sxs-lookup"><span data-stu-id="761a0-105">\<routing></span></span>  
<span data-ttu-id="761a0-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="761a0-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="761a0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="761a0-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="761a0-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="761a0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="761a0-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="761a0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="761a0-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="761a0-110">Attributes</span></span>  
 <span data-ttu-id="761a0-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="761a0-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="761a0-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="761a0-112">Child Elements</span></span>  
  
|<span data-ttu-id="761a0-113">Élément</span><span class="sxs-lookup"><span data-stu-id="761a0-113">Element</span></span>|<span data-ttu-id="761a0-114">Description</span><span class="sxs-lookup"><span data-stu-id="761a0-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="761a0-115">\<filtres ></span><span class="sxs-lookup"><span data-stu-id="761a0-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="761a0-116">Table de routage qui contient des mappages entre les filtres de routage et les points de terminaison cibles vers lesquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="761a0-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="761a0-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="761a0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="761a0-118">Élément</span><span class="sxs-lookup"><span data-stu-id="761a0-118">Element</span></span>|<span data-ttu-id="761a0-119">Description</span><span class="sxs-lookup"><span data-stu-id="761a0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="761a0-120">\<routage ></span><span class="sxs-lookup"><span data-stu-id="761a0-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="761a0-121">Section de configuration qui contient des filtres de routage et des tables de routage.</span><span class="sxs-lookup"><span data-stu-id="761a0-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="761a0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="761a0-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
