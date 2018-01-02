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
ms.workload: dotnet
ms.openlocfilehash: ed3e933e1c3468a09b1d6b089b4abf52dad85017
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="30759-102">&lt;transport&gt; de &lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="30759-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="30759-103">Spécifie les paramètres de sécurité de niveau transport lors de l’utilisation du [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="30759-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="30759-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="30759-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="30759-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="30759-105">\<bindings></span></span>  
<span data-ttu-id="30759-106">\<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="30759-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="30759-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="30759-107">\<binding></span></span>  
<span data-ttu-id="30759-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="30759-108">\<security></span></span>  
<span data-ttu-id="30759-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="30759-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30759-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30759-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30759-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="30759-111">Attributes and Elements</span></span>  
 <span data-ttu-id="30759-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="30759-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30759-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="30759-113">Attributes</span></span>  
  
|<span data-ttu-id="30759-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="30759-114">Attribute</span></span>|<span data-ttu-id="30759-115">Description</span><span class="sxs-lookup"><span data-stu-id="30759-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30759-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="30759-116">credentialType</span></span>|<span data-ttu-id="30759-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="30759-117">Optional.</span></span> <span data-ttu-id="30759-118">Spécifie le type d'informations d'identification utilisé pour vérifier les messages envoyés avec le transport d'homologues.</span><span class="sxs-lookup"><span data-stu-id="30759-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="30759-119">Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="30759-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="30759-120">Attribut credentialType</span><span class="sxs-lookup"><span data-stu-id="30759-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="30759-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="30759-121">Value</span></span>|<span data-ttu-id="30759-122">Description</span><span class="sxs-lookup"><span data-stu-id="30759-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="30759-123">Certificat</span><span class="sxs-lookup"><span data-stu-id="30759-123">Certificate</span></span>|<span data-ttu-id="30759-124">L'authentification du transport de canal homologue requiert un certificat X509.</span><span class="sxs-lookup"><span data-stu-id="30759-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="30759-125">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="30759-125">Password</span></span>|<span data-ttu-id="30759-126">L'authentification du transport de canal homologue requiert un mot de passe correct.</span><span class="sxs-lookup"><span data-stu-id="30759-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30759-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="30759-127">Child Elements</span></span>  
 <span data-ttu-id="30759-128">Aucun.</span><span class="sxs-lookup"><span data-stu-id="30759-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30759-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="30759-129">Parent Elements</span></span>  
  
|<span data-ttu-id="30759-130">Élément</span><span class="sxs-lookup"><span data-stu-id="30759-130">Element</span></span>|<span data-ttu-id="30759-131">Description</span><span class="sxs-lookup"><span data-stu-id="30759-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30759-132">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="30759-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="30759-133">Définit les paramètres de sécurité pour le [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="30759-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30759-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30759-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="30759-135">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="30759-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="30759-136">Liaisons</span><span class="sxs-lookup"><span data-stu-id="30759-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="30759-137">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="30759-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="30759-138">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="30759-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="30759-139">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="30759-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
