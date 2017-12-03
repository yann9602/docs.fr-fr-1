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
ms.openlocfilehash: 3754964d07dd80442fbffd7c632304ef9d83ab1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a><span data-ttu-id="01460-102">&lt;peer&gt; de &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="01460-102">&lt;peer&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="01460-103">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="01460-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="01460-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="01460-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="01460-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="01460-105">\<behaviors></span></span>  
<span data-ttu-id="01460-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="01460-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="01460-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="01460-107">\<behavior></span></span>  
<span data-ttu-id="01460-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="01460-108">\<serviceCredentials></span></span>  
<span data-ttu-id="01460-109">\<homologue ></span><span class="sxs-lookup"><span data-stu-id="01460-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01460-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01460-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01460-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="01460-111">Attributes and Elements</span></span>  
 <span data-ttu-id="01460-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="01460-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01460-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="01460-113">Attributes</span></span>  
 <span data-ttu-id="01460-114">Aucun</span><span class="sxs-lookup"><span data-stu-id="01460-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="01460-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="01460-115">Child Elements</span></span>  
  
|<span data-ttu-id="01460-116">Élément</span><span class="sxs-lookup"><span data-stu-id="01460-116">Element</span></span>|<span data-ttu-id="01460-117">Description</span><span class="sxs-lookup"><span data-stu-id="01460-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01460-118">\<certificat ></span><span class="sxs-lookup"><span data-stu-id="01460-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="01460-119">Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les services de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="01460-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="01460-120">.</span><span class="sxs-lookup"><span data-stu-id="01460-120">.</span></span>|  
|[<span data-ttu-id="01460-121">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="01460-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="01460-122">Spécifie les options d'authentification pour les expéditeurs de messages.</span><span class="sxs-lookup"><span data-stu-id="01460-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="01460-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="01460-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="01460-124">Spécifie les options d'authentification pour les services du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="01460-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="01460-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="01460-125">Parent Elements</span></span>  
  
|<span data-ttu-id="01460-126">Élément</span><span class="sxs-lookup"><span data-stu-id="01460-126">Element</span></span>|<span data-ttu-id="01460-127">Description</span><span class="sxs-lookup"><span data-stu-id="01460-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01460-128">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="01460-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="01460-129">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="01460-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01460-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01460-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="01460-131">Mise en réseau pair à pair</span><span class="sxs-lookup"><span data-stu-id="01460-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="01460-132">Authentification de Message de canal homologue</span><span class="sxs-lookup"><span data-stu-id="01460-132">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="01460-133">Authentification personnalisée de canal homologue</span><span class="sxs-lookup"><span data-stu-id="01460-133">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="01460-134">Sécurisation des Applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="01460-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="01460-135">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="01460-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
