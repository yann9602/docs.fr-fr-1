---
title: "&lt;en-têtes&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7fdd869553a672045c94a256b00638c9d0c4c24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltheadersgt"></a><span data-ttu-id="eb9f5-102">&lt;en-têtes&gt;</span><span class="sxs-lookup"><span data-stu-id="eb9f5-102">&lt;headers&gt;</span></span>
<span data-ttu-id="eb9f5-103">Un point de terminaison peut être adressé par un ou plusieurs en-têtes SOAP en plus de son URI de base.</span><span class="sxs-lookup"><span data-stu-id="eb9f5-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="eb9f5-104">Le jeu de scénarios où cette opération est utile est un jeu de scénarios intermédiaires SOAP où un point de terminaison requiert que les clients de ce point de terminaison incluent des en-têtes SOAP destinés à des intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="eb9f5-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="eb9f5-105">Cet élément de configuration peut être utilisé pour définir ces en-têtes d'adresse personnalisés.</span><span class="sxs-lookup"><span data-stu-id="eb9f5-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="eb9f5-106">Les entrées de la collection d'en-têtes de points de terminaison sont des éléments XML définis par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="eb9f5-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="eb9f5-107">Chaque élément doit être au format XML adéquat.</span><span class="sxs-lookup"><span data-stu-id="eb9f5-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="eb9f5-108">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="eb9f5-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="eb9f5-109">\<client ></span><span class="sxs-lookup"><span data-stu-id="eb9f5-109">\<client></span></span>  
<span data-ttu-id="eb9f5-110">\<point de terminaison ></span><span class="sxs-lookup"><span data-stu-id="eb9f5-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb9f5-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb9f5-111">Syntax</span></span>  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb9f5-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="eb9f5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="eb9f5-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="eb9f5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb9f5-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="eb9f5-114">Attributes</span></span>  
 <span data-ttu-id="eb9f5-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="eb9f5-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eb9f5-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="eb9f5-116">Child Elements</span></span>  
  
|<span data-ttu-id="eb9f5-117">Élément</span><span class="sxs-lookup"><span data-stu-id="eb9f5-117">Element</span></span>|<span data-ttu-id="eb9f5-118">Description</span><span class="sxs-lookup"><span data-stu-id="eb9f5-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb9f5-119">Region</span><span class="sxs-lookup"><span data-stu-id="eb9f5-119">Region</span></span>||  
|<span data-ttu-id="eb9f5-120">Membre</span><span class="sxs-lookup"><span data-stu-id="eb9f5-120">Member</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="eb9f5-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="eb9f5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="eb9f5-122">Élément</span><span class="sxs-lookup"><span data-stu-id="eb9f5-122">Element</span></span>|<span data-ttu-id="eb9f5-123">Description</span><span class="sxs-lookup"><span data-stu-id="eb9f5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb9f5-124">\<point de terminaison ></span><span class="sxs-lookup"><span data-stu-id="eb9f5-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="eb9f5-125">Configure différents types de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="eb9f5-125">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb9f5-126">Notes</span><span class="sxs-lookup"><span data-stu-id="eb9f5-126">Remarks</span></span>  
 <span data-ttu-id="eb9f5-127">Les en-têtes facultatifs fournissent des informations d'adressage plus détaillées pour identifier ou interagir avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="eb9f5-127">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="eb9f5-128">Par exemple, les en-tête peuvent indiquer comment traiter un message entrant, où le point de terminaison doit envoyer un message de réponse ou quelle instance d'un service utiliser pour traiter un message entrant d'un utilisateur particulier lorsque plusieurs instances sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="eb9f5-128">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb9f5-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb9f5-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [<span data-ttu-id="eb9f5-130">Points de terminaison : adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="eb9f5-130">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
