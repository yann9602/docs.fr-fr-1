---
title: '&lt;transport&gt; de &lt;peerTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8bb0fbce0d7b45fd051db187cd6d7e920b08cab3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="861eb-102">&lt;transport&gt; de &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="861eb-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="861eb-103">Indique le type de transport correspondant aux messages sécurisés envoyés par des homologues configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="861eb-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="861eb-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="861eb-104">\<system.serviceModel></span></span>  
<span data-ttu-id="861eb-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="861eb-105">\<bindings></span></span>  
<span data-ttu-id="861eb-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="861eb-106">\<customBinding></span></span>  
<span data-ttu-id="861eb-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="861eb-107">\<binding></span></span>  
<span data-ttu-id="861eb-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="861eb-108">\<peerTransport></span></span>  
<span data-ttu-id="861eb-109">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="861eb-109">\<security></span></span>  
<span data-ttu-id="861eb-110">\<transport ></span><span class="sxs-lookup"><span data-stu-id="861eb-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="861eb-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="861eb-111">Syntax</span></span>  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="861eb-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="861eb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="861eb-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="861eb-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="861eb-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="861eb-114">Attributes</span></span>  
  
|<span data-ttu-id="861eb-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="861eb-115">Attribute</span></span>|<span data-ttu-id="861eb-116">Description</span><span class="sxs-lookup"><span data-stu-id="861eb-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="861eb-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="861eb-117">credentialType</span></span>|<span data-ttu-id="861eb-118">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="861eb-118">Optional.</span></span> <span data-ttu-id="861eb-119">Spécifie le type d'informations d'identification utilisé pour vérifier les messages envoyés avec le transport d'homologues.</span><span class="sxs-lookup"><span data-stu-id="861eb-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="861eb-120">Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="861eb-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="861eb-121">Attribut credentialType</span><span class="sxs-lookup"><span data-stu-id="861eb-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="861eb-122">Valeur</span><span class="sxs-lookup"><span data-stu-id="861eb-122">Value</span></span>|<span data-ttu-id="861eb-123">Description</span><span class="sxs-lookup"><span data-stu-id="861eb-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="861eb-124">Certificat</span><span class="sxs-lookup"><span data-stu-id="861eb-124">Certificate</span></span>|<span data-ttu-id="861eb-125">L'authentification du transport de canal homologue requiert un certificat X509.</span><span class="sxs-lookup"><span data-stu-id="861eb-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="861eb-126">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="861eb-126">Password</span></span>|<span data-ttu-id="861eb-127">L'authentification du transport de canal homologue requiert un mot de passe correct.</span><span class="sxs-lookup"><span data-stu-id="861eb-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="861eb-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="861eb-128">Child Elements</span></span>  
 <span data-ttu-id="861eb-129">Aucun.</span><span class="sxs-lookup"><span data-stu-id="861eb-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="861eb-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="861eb-130">Parent Elements</span></span>  
  
|<span data-ttu-id="861eb-131">Élément</span><span class="sxs-lookup"><span data-stu-id="861eb-131">Element</span></span>|<span data-ttu-id="861eb-132">Description</span><span class="sxs-lookup"><span data-stu-id="861eb-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="861eb-133">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="861eb-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="861eb-134">Définit les paramètres de sécurité pour un transport d'homologue.</span><span class="sxs-lookup"><span data-stu-id="861eb-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="861eb-135">Notes</span><span class="sxs-lookup"><span data-stu-id="861eb-135">Remarks</span></span>  
 <span data-ttu-id="861eb-136">Cet élément est défini uniquement si l’attribut mode de [ \<sécurité >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) a la valeur `Transport` ou `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="861eb-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="861eb-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="861eb-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="861eb-138">Sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="861eb-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="861eb-139">Transports</span><span class="sxs-lookup"><span data-stu-id="861eb-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="861eb-140">Choix d’un transport</span><span class="sxs-lookup"><span data-stu-id="861eb-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="861eb-141">Liaisons</span><span class="sxs-lookup"><span data-stu-id="861eb-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="861eb-142">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="861eb-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="861eb-143">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="861eb-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="861eb-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="861eb-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
