---
title: '&lt;announcementEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5458149a68273a62b1636dec0da4d9494fb63a99
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltannouncementendpointgt"></a><span data-ttu-id="f6126-102">&lt;announcementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="f6126-102">&lt;announcementEndpoint&gt;</span></span>
<span data-ttu-id="f6126-103">Cet élément de configuration définit un point de terminaison standard avec un contrat d'annonce fixe.</span><span class="sxs-lookup"><span data-stu-id="f6126-103">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="f6126-104">Un service peut éventuellement annoncer sa disponibilité en envoyant un message d'annonce en ligne ou hors connexion selon qu'il est respectivement ouvert ou fermé.</span><span class="sxs-lookup"><span data-stu-id="f6126-104">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="f6126-105">A [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service spécifie les points de terminaison d’annonce dans le [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) élément et utilise le AnnouncementClient pour effectuer les annonces.</span><span class="sxs-lookup"><span data-stu-id="f6126-105">A [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="f6126-106">Un client souhaite écouter l’annonce à partir de l’autre service est en réalité agissant comme un [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service ; par conséquent, vous devez configurer les points de terminaison d’annonce pour le client dans le [ \<services >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span><span class="sxs-lookup"><span data-stu-id="f6126-106">A client wishing to listen for the announcement from other service is actually acting as a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="f6126-107">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f6126-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="f6126-108">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f6126-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6126-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6126-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005" 
                        maxAnnouncementDelay="Timespan" 
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6126-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f6126-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f6126-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f6126-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6126-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="f6126-112">Attributes</span></span>  
  
|<span data-ttu-id="f6126-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="f6126-113">Attribute</span></span>|<span data-ttu-id="f6126-114">Description</span><span class="sxs-lookup"><span data-stu-id="f6126-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6126-115">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="f6126-115">discoveryVersion</span></span>|<span data-ttu-id="f6126-116">Chaîne qui spécifie l'une des deux versions du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="f6126-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="f6126-117">Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="f6126-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="f6126-118">Cette valeur est de type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="f6126-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="f6126-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="f6126-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="f6126-120">Valeur Timespan qui spécifie le délai d'attente maximal du protocole de découverte avant l'envoi d'un message de type Hello.</span><span class="sxs-lookup"><span data-stu-id="f6126-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="f6126-121">Les messages attendent pendant un délai aléatoire compris entre 0 et la valeur de cet attribut avant d'être envoyés.</span><span class="sxs-lookup"><span data-stu-id="f6126-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="f6126-122">Cet attribut permet de définir un délai court et aléatoire pour empêcher toute tempête de réseau lorsqu'un réseau est en panne et que tous les services reviennent en ligne en même temps.</span><span class="sxs-lookup"><span data-stu-id="f6126-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="f6126-123">name</span><span class="sxs-lookup"><span data-stu-id="f6126-123">name</span></span>|<span data-ttu-id="f6126-124">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="f6126-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="f6126-125">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="f6126-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6126-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f6126-126">Child Elements</span></span>  
 <span data-ttu-id="f6126-127">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f6126-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6126-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f6126-128">Parent Elements</span></span>  
  
|<span data-ttu-id="f6126-129">Élément</span><span class="sxs-lookup"><span data-stu-id="f6126-129">Element</span></span>|<span data-ttu-id="f6126-130">Description</span><span class="sxs-lookup"><span data-stu-id="f6126-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6126-131">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f6126-131">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f6126-132">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="f6126-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f6126-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="f6126-133">Example</span></span>  
 <span data-ttu-id="f6126-134">L'exemple suivant montre un client qui écoute des messages d'annonce sur HTTP et Peernet.</span><span class="sxs-lookup"><span data-stu-id="f6126-134">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
```xml  
<services>  
  <service name="ServiceAnnouncementListener">  
    <endpoint name="httpAnnouncementEndpoint"  
              kind="announcementEndpoint"  
              binding="basicHttpBinding"  
              address="announcements" />  
    <endpoint name="peerNetAnnouncementEndpoint"  
              kind="announcementEndpoint"  
              binding="peerTcpBinding"  
              address="net.p2p://discoveryMesh/multicast"  
              bindingConfiguration="discoveryPeerTcpBindingConfig" />  
  ...  
  </service>  
</services>  
  
<standardEndpoints>  
  <announcementEndpoint>  
    <standardEndpoint name="httpAnnouncementEndpoint"                         
                      version="WSDiscoveryApril2005" />  
    <standardEndpoint name="peerNetAnnouncementEndpoint"                         
                      version="WSDiscoveryApril2005" />  
   </announcementEndpoint>  
</standardEndpoints>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6126-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6126-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
