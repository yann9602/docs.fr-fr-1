---
title: '&lt;security&gt; de &lt;peerTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d08d839d0eb80c23b96f87cf26d3d68db7d358f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a><span data-ttu-id="7ef32-102">&lt;security&gt; de &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="7ef32-102">&lt;security&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="7ef32-103">Contient les paramètres de sécurité associés à un canal homologue, y compris le type d'authentification utilisé et la sécurité utilisée pour le transport de messages.</span><span class="sxs-lookup"><span data-stu-id="7ef32-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="7ef32-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7ef32-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7ef32-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="7ef32-105">\<bindings></span></span>  
<span data-ttu-id="7ef32-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7ef32-106">\<customBinding></span></span>  
<span data-ttu-id="7ef32-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="7ef32-107">\<binding></span></span>  
<span data-ttu-id="7ef32-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="7ef32-108">\<peerTransport></span></span>  
<span data-ttu-id="7ef32-109">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="7ef32-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ef32-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ef32-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">  
    <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
</security  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ef32-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7ef32-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7ef32-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7ef32-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ef32-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="7ef32-113">Attributes</span></span>  
  
|<span data-ttu-id="7ef32-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="7ef32-114">Attribute</span></span>|<span data-ttu-id="7ef32-115">Description</span><span class="sxs-lookup"><span data-stu-id="7ef32-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="7ef32-116">Spécifie le type de sécurité à appliquer.</span><span class="sxs-lookup"><span data-stu-id="7ef32-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="7ef32-117">La valeur par défaut est Message.</span><span class="sxs-lookup"><span data-stu-id="7ef32-117">The default value is Message.</span></span> <span data-ttu-id="7ef32-118">Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="7ef32-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="7ef32-119">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="7ef32-119">mode Attribute</span></span>  
  
|<span data-ttu-id="7ef32-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="7ef32-120">Value</span></span>|<span data-ttu-id="7ef32-121">Description</span><span class="sxs-lookup"><span data-stu-id="7ef32-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="7ef32-122">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="7ef32-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="7ef32-123">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7ef32-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="7ef32-124">La sécurité SOAP assure l'authentification, l'intégrité et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="7ef32-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="7ef32-125">Le protocole HTTPS assure l'authentification et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="7ef32-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="7ef32-126">Les messages SOAP fournissent des types d'informations d'identification enrichies.</span><span class="sxs-lookup"><span data-stu-id="7ef32-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ef32-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7ef32-127">Child Elements</span></span>  
  
|<span data-ttu-id="7ef32-128">Élément</span><span class="sxs-lookup"><span data-stu-id="7ef32-128">Element</span></span>|<span data-ttu-id="7ef32-129">Description</span><span class="sxs-lookup"><span data-stu-id="7ef32-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ef32-130">\<transport ></span><span class="sxs-lookup"><span data-stu-id="7ef32-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="7ef32-131">Définit un transport d’homologue pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="7ef32-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="7ef32-132">Cet élément dispose d'un attribut `clientCredentialType` qui spécifie les informations d'identification à utiliser lors de l'interaction avec un service.</span><span class="sxs-lookup"><span data-stu-id="7ef32-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="7ef32-133">Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="7ef32-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="7ef32-134">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7ef32-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7ef32-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7ef32-135">Parent Elements</span></span>  
  
|<span data-ttu-id="7ef32-136">Élément</span><span class="sxs-lookup"><span data-stu-id="7ef32-136">Element</span></span>|<span data-ttu-id="7ef32-137">Description</span><span class="sxs-lookup"><span data-stu-id="7ef32-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ef32-138">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="7ef32-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="7ef32-139">Définit un transport d’homologue pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="7ef32-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ef32-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ef32-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="7ef32-141">Sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="7ef32-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="7ef32-142">Transports</span><span class="sxs-lookup"><span data-stu-id="7ef32-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="7ef32-143">Choix d’un transport</span><span class="sxs-lookup"><span data-stu-id="7ef32-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="7ef32-144">Liaisons</span><span class="sxs-lookup"><span data-stu-id="7ef32-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7ef32-145">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="7ef32-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="7ef32-146">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="7ef32-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="7ef32-147">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7ef32-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
