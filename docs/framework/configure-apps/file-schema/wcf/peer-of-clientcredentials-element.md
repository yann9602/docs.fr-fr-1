---
title: "&lt;peer&gt;, élément de &lt;clientCredentials&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f26321afdbe53c4ab3750eae4a7a730bcb5ae4e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="27539-102">&lt;peer&gt;, élément de &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="27539-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="27539-103">Spécifie les informations d'identification utilisées lors de l'authentification de clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="27539-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="27539-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="27539-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="27539-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="27539-105">\<behaviors></span></span>  
<span data-ttu-id="27539-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="27539-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="27539-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="27539-107">\<behavior></span></span>  
<span data-ttu-id="27539-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="27539-108">\<clientCredentials></span></span>  
<span data-ttu-id="27539-109">\<homologue ></span><span class="sxs-lookup"><span data-stu-id="27539-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27539-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27539-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27539-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="27539-111">Attributes and Elements</span></span>  
 <span data-ttu-id="27539-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="27539-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27539-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="27539-113">Attributes</span></span>  
 <span data-ttu-id="27539-114">Aucun</span><span class="sxs-lookup"><span data-stu-id="27539-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="27539-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="27539-115">Child Elements</span></span>  
  
|<span data-ttu-id="27539-116">Élément</span><span class="sxs-lookup"><span data-stu-id="27539-116">Element</span></span>|<span data-ttu-id="27539-117">Description</span><span class="sxs-lookup"><span data-stu-id="27539-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27539-118">\<certificat ></span><span class="sxs-lookup"><span data-stu-id="27539-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="27539-119">Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="27539-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="27539-120">.</span><span class="sxs-lookup"><span data-stu-id="27539-120">.</span></span>|  
|[<span data-ttu-id="27539-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="27539-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="27539-122">Spécifie les options d'authentification pour les clients du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="27539-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="27539-123">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="27539-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="27539-124">Spécifie les options d'authentification pour les expéditeurs de messages.</span><span class="sxs-lookup"><span data-stu-id="27539-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27539-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="27539-125">Parent Elements</span></span>  
  
|<span data-ttu-id="27539-126">Élément</span><span class="sxs-lookup"><span data-stu-id="27539-126">Element</span></span>|<span data-ttu-id="27539-127">Description</span><span class="sxs-lookup"><span data-stu-id="27539-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27539-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="27539-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="27539-129">Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="27539-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27539-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="27539-130">Remarks</span></span>  
 <span data-ttu-id="27539-131">Cet élément de configuration spécifie les informations d'identification qu'un nœud homologue utilise pour s'authentifier sur les autres nœuds de la maille, ainsi que les paramètres d'authentification qu'un nœud homologue utilise pour authentifier les autres nœuds homologues.</span><span class="sxs-lookup"><span data-stu-id="27539-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="27539-132">Pour plus d’informations, consultez [l’authentification de Message du canal homologue](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95) et [sécurisation des Applications de canal homologue](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="27539-132">For more information, see [Peer Channel Message Authentication](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27539-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27539-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="27539-134">Mise en réseau pair à pair</span><span class="sxs-lookup"><span data-stu-id="27539-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="27539-135">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="27539-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="27539-136">Authentification de Message de canal homologue</span><span class="sxs-lookup"><span data-stu-id="27539-136">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="27539-137">Authentification personnalisée de canal homologue</span><span class="sxs-lookup"><span data-stu-id="27539-137">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="27539-138">Sécurisation des Applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="27539-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="27539-139">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="27539-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
