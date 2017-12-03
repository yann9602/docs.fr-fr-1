---
title: '&lt;transport&gt; de &lt;netPeerTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 181e6a9458754934d6b3b27a31c2cf2dd3455f52
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="a930d-102">&lt;transport&gt; de &lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a930d-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="a930d-103">Spécifie les paramètres de sécurité de niveau transport lors de l’utilisation du [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a930d-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="a930d-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a930d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a930d-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="a930d-105">\<bindings></span></span>  
<span data-ttu-id="a930d-106">\<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="a930d-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="a930d-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="a930d-107">\<binding></span></span>  
<span data-ttu-id="a930d-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="a930d-108">\<security></span></span>  
<span data-ttu-id="a930d-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="a930d-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a930d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a930d-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a930d-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a930d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a930d-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a930d-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a930d-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="a930d-113">Attributes</span></span>  
  
|<span data-ttu-id="a930d-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="a930d-114">Attribute</span></span>|<span data-ttu-id="a930d-115">Description</span><span class="sxs-lookup"><span data-stu-id="a930d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a930d-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="a930d-116">credentialType</span></span>|<span data-ttu-id="a930d-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a930d-117">Optional.</span></span> <span data-ttu-id="a930d-118">Spécifie le type d'informations d'identification utilisé pour vérifier les messages envoyés avec le transport d'homologues.</span><span class="sxs-lookup"><span data-stu-id="a930d-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="a930d-119">Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="a930d-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="a930d-120">Attribut credentialType</span><span class="sxs-lookup"><span data-stu-id="a930d-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="a930d-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="a930d-121">Value</span></span>|<span data-ttu-id="a930d-122">Description</span><span class="sxs-lookup"><span data-stu-id="a930d-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a930d-123">Certificat</span><span class="sxs-lookup"><span data-stu-id="a930d-123">Certificate</span></span>|<span data-ttu-id="a930d-124">L'authentification du transport de canal homologue requiert un certificat X509.</span><span class="sxs-lookup"><span data-stu-id="a930d-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="a930d-125">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="a930d-125">Password</span></span>|<span data-ttu-id="a930d-126">L'authentification du transport de canal homologue requiert un mot de passe correct.</span><span class="sxs-lookup"><span data-stu-id="a930d-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a930d-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a930d-127">Child Elements</span></span>  
 <span data-ttu-id="a930d-128">None</span><span class="sxs-lookup"><span data-stu-id="a930d-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a930d-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a930d-129">Parent Elements</span></span>  
  
|<span data-ttu-id="a930d-130">Élément</span><span class="sxs-lookup"><span data-stu-id="a930d-130">Element</span></span>|<span data-ttu-id="a930d-131">Description</span><span class="sxs-lookup"><span data-stu-id="a930d-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a930d-132">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="a930d-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="a930d-133">Définit les paramètres de sécurité pour le [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a930d-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a930d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a930d-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="a930d-135">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="a930d-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a930d-136">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a930d-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a930d-137">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="a930d-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a930d-138">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a930d-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a930d-139">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="a930d-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
