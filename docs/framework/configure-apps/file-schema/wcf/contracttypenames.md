---
title: '&lt;contractTypeNames&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5ac3a4af54d9f470a1cbd50096731b23d28b0c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="482f8-102">&lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="482f8-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="482f8-103">Section de configuration qui spécifie une liste de noms de type de contrat, qui sont les noms de contrat des services recherchés, et les critères généralement utilisés lors de la recherche d'un service.</span><span class="sxs-lookup"><span data-stu-id="482f8-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="482f8-104">Si plusieurs noms de contrat sont spécifiés, seuls les points de terminaison de service correspondant à TOUS les contrats répondent.</span><span class="sxs-lookup"><span data-stu-id="482f8-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="482f8-105">Notez que dans [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], un point de terminaison ne peut prendre en charge qu'un seul contrat.</span><span class="sxs-lookup"><span data-stu-id="482f8-105">Note that in [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="482f8-106">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="482f8-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="482f8-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="482f8-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="482f8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="482f8-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" 
                        maxResults="Integer" 
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="482f8-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="482f8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="482f8-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="482f8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="482f8-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="482f8-111">Attributes</span></span>  
 <span data-ttu-id="482f8-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="482f8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="482f8-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="482f8-113">Child Elements</span></span>  
  
|<span data-ttu-id="482f8-114">Élément</span><span class="sxs-lookup"><span data-stu-id="482f8-114">Element</span></span>|<span data-ttu-id="482f8-115">Description</span><span class="sxs-lookup"><span data-stu-id="482f8-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="482f8-116">\<add></span><span class="sxs-lookup"><span data-stu-id="482f8-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="482f8-117">Un nom de type de contrat est une propriété qui fait référence au jeu de critères utilisé en général au cours de la recherche d'un service.</span><span class="sxs-lookup"><span data-stu-id="482f8-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="482f8-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="482f8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="482f8-119">Élément</span><span class="sxs-lookup"><span data-stu-id="482f8-119">Element</span></span>|<span data-ttu-id="482f8-120">Description</span><span class="sxs-lookup"><span data-stu-id="482f8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="482f8-121">\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="482f8-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="482f8-122">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="482f8-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="482f8-123">Critères peuvent être regroupés en critères de recherche (spécifiant les services que vous recherchez) et recherchez les critères d’arrêt (la durée pendant laquelle la recherche).</span><span class="sxs-lookup"><span data-stu-id="482f8-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="482f8-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="482f8-124">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
