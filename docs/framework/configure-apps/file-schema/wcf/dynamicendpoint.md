---
title: '&lt;dynamicEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46fb4f1f4688aede484b177e30b8bc8dfff1ece2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="750ee-102">&lt;dynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="750ee-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="750ee-103">Cet élément de configuration définit un point de terminaison standard qui contient des informations pour permettre à une application de fonctionner en tant que programme client qui peut rechercher l'adresse du point de terminaison de manière dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="750ee-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="750ee-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="750ee-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="750ee-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="750ee-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="750ee-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="750ee-106">Syntax</span></span>  
  
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
            <add scope="URI" />
          </scopes>
        </findCriteria>
      </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="750ee-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="750ee-107">Attributes and Elements</span></span>  
 <span data-ttu-id="750ee-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="750ee-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="750ee-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="750ee-109">Attributes</span></span>  
 <span data-ttu-id="750ee-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="750ee-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="750ee-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="750ee-111">Child Elements</span></span>  
  
|<span data-ttu-id="750ee-112">Élément</span><span class="sxs-lookup"><span data-stu-id="750ee-112">Element</span></span>|<span data-ttu-id="750ee-113">Description</span><span class="sxs-lookup"><span data-stu-id="750ee-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="750ee-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="750ee-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="750ee-115">Contient les paramètres requis par une application pour participer au processus de découverte de service en tant que client.</span><span class="sxs-lookup"><span data-stu-id="750ee-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="750ee-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="750ee-116">Parent Elements</span></span>  
  
|<span data-ttu-id="750ee-117">Élément</span><span class="sxs-lookup"><span data-stu-id="750ee-117">Element</span></span>|<span data-ttu-id="750ee-118">Description</span><span class="sxs-lookup"><span data-stu-id="750ee-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="750ee-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="750ee-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="750ee-120">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="750ee-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="750ee-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="750ee-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
