---
title: '&lt;add&gt; de &lt;contractTypeNames&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 191e3e221ae42e5c046f8df324989aae7ab0dc1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="f276c-102">&lt;add&gt; de &lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="f276c-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="f276c-103">Élément de configuration qui spécifie le nom de contrat des services recherchés et les critères généralement utilisés lors de la recherche d'un service.</span><span class="sxs-lookup"><span data-stu-id="f276c-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="f276c-104">Si plusieurs noms de contrat sont spécifiés, seuls les points de terminaison de service correspondant à TOUS les contrats répondent.</span><span class="sxs-lookup"><span data-stu-id="f276c-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="f276c-105">Notez que dans [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], un point de terminaison ne peut prendre en charge qu'un seul contrat.</span><span class="sxs-lookup"><span data-stu-id="f276c-105">Note that in [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="f276c-106">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f276c-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="f276c-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f276c-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f276c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f276c-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <dynamicEndpoint>           <standardEndpoint>             <discoveryClientSettings discoveryEndpoint="String" >               <findCriteria duration="TimeSpan"                  maxResults="Integer"                   scopeMatchBy="Uri" >                  <contractTypeNames>                     <add name="String" namespace="String" />                  <contractTypeNames>                  <extensions />                  <scopes>                    <add scope="URI"/>                  </scopes>               </findCriteria>             </discoveryClientSettings>          <standardEndpoint>       </dynamicEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f276c-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f276c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f276c-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f276c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f276c-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="f276c-111">Attributes</span></span>  
  
|<span data-ttu-id="f276c-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="f276c-112">Attribute</span></span>|<span data-ttu-id="f276c-113">Description</span><span class="sxs-lookup"><span data-stu-id="f276c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f276c-114">name</span><span class="sxs-lookup"><span data-stu-id="f276c-114">name</span></span>|<span data-ttu-id="f276c-115">Chaîne qui spécifie le nom du type de contrat.</span><span class="sxs-lookup"><span data-stu-id="f276c-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="f276c-116">namespace</span><span class="sxs-lookup"><span data-stu-id="f276c-116">namespace</span></span>|<span data-ttu-id="f276c-117">Chaîne qui spécifie l'espace de noms du type de contrat.</span><span class="sxs-lookup"><span data-stu-id="f276c-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f276c-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f276c-118">Child Elements</span></span>  
 <span data-ttu-id="f276c-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f276c-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f276c-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f276c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f276c-121">Élément</span><span class="sxs-lookup"><span data-stu-id="f276c-121">Element</span></span>|<span data-ttu-id="f276c-122">Description</span><span class="sxs-lookup"><span data-stu-id="f276c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f276c-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="f276c-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="f276c-124">Collection de noms de type de contrat.</span><span class="sxs-lookup"><span data-stu-id="f276c-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f276c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f276c-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
