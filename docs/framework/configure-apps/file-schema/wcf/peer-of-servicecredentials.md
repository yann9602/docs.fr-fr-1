---
title: '&lt;peer&gt; de &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d04c6121c5d106f5877517e9f72d1b533480dfb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a><span data-ttu-id="44182-102">&lt;peer&gt; de &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="44182-102">&lt;peer&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="44182-103">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="44182-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="44182-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="44182-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="44182-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="44182-105">\<behaviors></span></span>  
<span data-ttu-id="44182-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="44182-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="44182-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="44182-107">\<behavior></span></span>  
<span data-ttu-id="44182-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="44182-108">\<serviceCredentials></span></span>  
<span data-ttu-id="44182-109">\<homologue ></span><span class="sxs-lookup"><span data-stu-id="44182-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44182-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44182-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44182-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="44182-111">Attributes and Elements</span></span>  
 <span data-ttu-id="44182-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="44182-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44182-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="44182-113">Attributes</span></span>  
 <span data-ttu-id="44182-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="44182-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="44182-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="44182-115">Child Elements</span></span>  
  
|<span data-ttu-id="44182-116">Élément</span><span class="sxs-lookup"><span data-stu-id="44182-116">Element</span></span>|<span data-ttu-id="44182-117">Description</span><span class="sxs-lookup"><span data-stu-id="44182-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44182-118">\<certificat ></span><span class="sxs-lookup"><span data-stu-id="44182-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="44182-119">Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les services de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="44182-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="44182-120">.</span><span class="sxs-lookup"><span data-stu-id="44182-120">.</span></span>|  
|[<span data-ttu-id="44182-121">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="44182-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="44182-122">Spécifie les options d'authentification pour les expéditeurs de messages.</span><span class="sxs-lookup"><span data-stu-id="44182-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="44182-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="44182-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="44182-124">Spécifie les options d'authentification pour les services du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="44182-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44182-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="44182-125">Parent Elements</span></span>  
  
|<span data-ttu-id="44182-126">Élément</span><span class="sxs-lookup"><span data-stu-id="44182-126">Element</span></span>|<span data-ttu-id="44182-127">Description</span><span class="sxs-lookup"><span data-stu-id="44182-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44182-128">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="44182-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="44182-129">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="44182-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44182-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44182-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="44182-131">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="44182-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="44182-132">Authentification de Message de canal homologue</span><span class="sxs-lookup"><span data-stu-id="44182-132">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="44182-133">Authentification personnalisée de canal homologue</span><span class="sxs-lookup"><span data-stu-id="44182-133">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="44182-134">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="44182-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="44182-135">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="44182-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
