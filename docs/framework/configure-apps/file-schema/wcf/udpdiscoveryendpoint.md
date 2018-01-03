---
title: '&lt;udpDiscoveryEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d8758e5126be13d61f2b3dd85f0b3b472c42ae1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltudpdiscoveryendpointgt"></a><span data-ttu-id="749da-102">&lt;udpDiscoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="749da-102">&lt;udpDiscoveryEndpoint&gt;</span></span>
<span data-ttu-id="749da-103">Cet élément de configuration définit un point de terminaison standard préconfiguré pour les opérations de découverte sur une liaison de multidiffusion UDP.</span><span class="sxs-lookup"><span data-stu-id="749da-103">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="749da-104">Ce point de terminaison a un contrat fixe et prend en charge deux versions de protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="749da-104">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="749da-105">De plus, il a une liaison UDP fixe et une adresse par défaut indiquée dans les spécifications WS-Discovery (WS-Discovery Avril 2005 ou WS-Discovery V1.1).</span><span class="sxs-lookup"><span data-stu-id="749da-105">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1)..</span></span>  
  
 <span data-ttu-id="749da-106">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="749da-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="749da-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="749da-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="749da-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="749da-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <discoveryEndpoint>           <standardEndpoint                  discoveryMode="Adhoc/Managed"                  discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"                  maxResponseDelay="Timespan"                  multicastAddress="Uri"                   name="String" />       </discoveryEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="749da-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="749da-109">Attributes and Elements</span></span>  
 <span data-ttu-id="749da-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="749da-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="749da-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="749da-111">Attributes</span></span>  
  
|<span data-ttu-id="749da-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="749da-112">Attribute</span></span>|<span data-ttu-id="749da-113">Description</span><span class="sxs-lookup"><span data-stu-id="749da-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="749da-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="749da-114">discoveryMode</span></span>|<span data-ttu-id="749da-115">Chaîne qui spécifie le mode de protocole de découverte.</span><span class="sxs-lookup"><span data-stu-id="749da-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="749da-116">Les valeurs valides sont « Ad hoc » et « Géré ».</span><span class="sxs-lookup"><span data-stu-id="749da-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="749da-117">En mode managé, le protocole repose sur un proxy de découverte, qui fait office de référentiel des services détectables.</span><span class="sxs-lookup"><span data-stu-id="749da-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="749da-118">Le mode ad hoc nécessite que le protocole utilise le mécanisme de multidiffusion UDP pour rechercher les services disponibles.</span><span class="sxs-lookup"><span data-stu-id="749da-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="749da-119">Cette valeur est de type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="749da-119">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="749da-120">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="749da-120">discoveryVersion</span></span>|<span data-ttu-id="749da-121">Chaîne qui spécifie l'une des deux versions du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="749da-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="749da-122">Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="749da-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="749da-123">Cette valeur est de type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="749da-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="749da-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="749da-124">maxResponseDelay</span></span>|<span data-ttu-id="749da-125">Valeur Timespan qui indique la valeur maximale du délai d'attente du protocole de découverte avant l'envoi de certains messages, tels que ceux de type Probe Match ou Resolve Match.</span><span class="sxs-lookup"><span data-stu-id="749da-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="749da-126">Si tous les messages ProbeMatches sont envoyés en même temps, une tempête de réseau peut en résulter.</span><span class="sxs-lookup"><span data-stu-id="749da-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="749da-127">Pour empêcher cet effet, les messages ProbeMatches sont envoyés avec un délai aléatoire entre chaque message ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="749da-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="749da-128">Le délai aléatoire est compris entre 0 et la valeur définie par cet attribut.</span><span class="sxs-lookup"><span data-stu-id="749da-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="749da-129">Si l'attribut a la valeur 0, les messages ProbeMatches sont envoyés dans une boucle serrée sans délai.</span><span class="sxs-lookup"><span data-stu-id="749da-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="749da-130">Sinon, les messages ProbeMatches sont envoyés avec un délai aléatoire de sorte que la durée totale nécessaire à l'envoi de tous les messages ProbeMatches ne dépasse pas le maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="749da-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="749da-131">Cette valeur est uniquement pertinente pour les services, elle n'est pas utilisée par les clients.</span><span class="sxs-lookup"><span data-stu-id="749da-131">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="749da-132">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="749da-132">multicastAddress</span></span>|<span data-ttu-id="749da-133">URI qui spécifie une adresse de multidiffusion à utiliser pour l'envoi et la réception des messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="749da-133">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="749da-134">La valeur par défaut est représentée par l'adresse de multidiffusion conforme à la spécification du protocole.</span><span class="sxs-lookup"><span data-stu-id="749da-134">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="749da-135">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="749da-135">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="749da-136">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="749da-136">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="749da-137">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="749da-137">Child Elements</span></span>  
  
|<span data-ttu-id="749da-138">Élément</span><span class="sxs-lookup"><span data-stu-id="749da-138">Element</span></span>|<span data-ttu-id="749da-139">Description</span><span class="sxs-lookup"><span data-stu-id="749da-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="749da-140">\<udpTransportSettings ></span><span class="sxs-lookup"><span data-stu-id="749da-140">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="749da-141">Collection de paramètres qui vous permettent de configurer le transport UDP pour le point de terminaison UDP.</span><span class="sxs-lookup"><span data-stu-id="749da-141">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="749da-142">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="749da-142">Parent Elements</span></span>  
  
|<span data-ttu-id="749da-143">Élément</span><span class="sxs-lookup"><span data-stu-id="749da-143">Element</span></span>|<span data-ttu-id="749da-144">Description</span><span class="sxs-lookup"><span data-stu-id="749da-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="749da-145">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="749da-145">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="749da-146">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="749da-146">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="749da-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="749da-147">Example</span></span>  
 <span data-ttu-id="749da-148">L'exemple suivant montre un service qui écoute des messages de découverte sur un transport de multidiffusion UDP.</span><span class="sxs-lookup"><span data-stu-id="749da-148">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
```xml
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <endpoint binding="basicHttpBinding"   
              address="calculator" 
              contract="ICalculatorService" />  
    <endpoint name="DiscoveryEndpoint"  
              kind="udpDiscoveryEndpoint" />  
  </service>  
  <standardEndpoints>  
    <udpDiscoveryEndpoint>  
      <standardEndpoint name="DiscoveryEndpoint"                         
                        version="WSDiscoveryApril2005" />  
    </udpDiscoveryEndpoint>  
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="749da-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="749da-149">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
