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
ms.openlocfilehash: a6923017f661cf463b4186e77e825195c6a9124d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="a7f7c-102">&lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="a7f7c-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="a7f7c-103">Section de configuration qui spécifie une liste de noms de type de contrat, qui sont les noms de contrat des services recherchés, et les critères généralement utilisés lors de la recherche d'un service.</span><span class="sxs-lookup"><span data-stu-id="a7f7c-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="a7f7c-104">Si plusieurs noms de contrat sont spécifiés, seuls les points de terminaison de service correspondant à TOUS les contrats répondent.</span><span class="sxs-lookup"><span data-stu-id="a7f7c-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="a7f7c-105">Notez que dans [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], un point de terminaison ne peut prendre en charge qu'un seul contrat.</span><span class="sxs-lookup"><span data-stu-id="a7f7c-105">Note that in [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="a7f7c-106">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a7f7c-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7f7c-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a7f7c-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f7c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7f7c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7f7c-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a7f7c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a7f7c-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a7f7c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7f7c-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a7f7c-111">Attributes</span></span>  
 <span data-ttu-id="a7f7c-112">Aucun</span><span class="sxs-lookup"><span data-stu-id="a7f7c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a7f7c-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a7f7c-113">Child Elements</span></span>  
  
|<span data-ttu-id="a7f7c-114">Élément</span><span class="sxs-lookup"><span data-stu-id="a7f7c-114">Element</span></span>|<span data-ttu-id="a7f7c-115">Description</span><span class="sxs-lookup"><span data-stu-id="a7f7c-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7f7c-116">\<add></span><span class="sxs-lookup"><span data-stu-id="a7f7c-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="a7f7c-117">Un nom de type de contrat est une propriété qui fait référence au jeu de critères utilisé en général au cours de la recherche d'un service.</span><span class="sxs-lookup"><span data-stu-id="a7f7c-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7f7c-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a7f7c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a7f7c-119">Élément</span><span class="sxs-lookup"><span data-stu-id="a7f7c-119">Element</span></span>|<span data-ttu-id="a7f7c-120">Description</span><span class="sxs-lookup"><span data-stu-id="a7f7c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7f7c-121">\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="a7f7c-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="a7f7c-122">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="a7f7c-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="a7f7c-123">Critères peuvent être regroupés en critères de recherche (spécifiant les services que vous recherchez) et recherchez les critères d’arrêt (la durée pendant laquelle la recherche).</span><span class="sxs-lookup"><span data-stu-id="a7f7c-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7f7c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7f7c-124">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
