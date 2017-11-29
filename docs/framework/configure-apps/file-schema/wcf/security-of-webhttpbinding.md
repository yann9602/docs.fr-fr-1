---
title: '&lt;security&gt; de &lt;webHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b3d5d00dcc79a746818975a6a8b125d3dc33933b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="d795b-102">&lt;security&gt; de &lt;webHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="d795b-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="d795b-103">Spécifie les exigences de sécurité pour un point de terminaison configuré avec un [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d795b-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="d795b-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d795b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d795b-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="d795b-105">\<bindings></span></span>  
<span data-ttu-id="d795b-106">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d795b-106">\<webHttpBinding></span></span>  
<span data-ttu-id="d795b-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="d795b-107">\<binding></span></span>  
<span data-ttu-id="d795b-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="d795b-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d795b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d795b-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
    <bindings>  
        <webHttpBinding>  
            <binding name = "string">  
              <security mode="None/Transport/TransportCredentialOnly">  
                                    <transport clientCredentialType =   
                                     "Basic/Certificate/Digest/None/Ntlm/Windows"  
                                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                                     realm="string" />  
              </security>  
        </webHttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d795b-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d795b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d795b-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d795b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d795b-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="d795b-112">Attributes</span></span>  
  
|<span data-ttu-id="d795b-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="d795b-113">Attribute</span></span>|<span data-ttu-id="d795b-114">Description</span><span class="sxs-lookup"><span data-stu-id="d795b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d795b-115">mode</span><span class="sxs-lookup"><span data-stu-id="d795b-115">mode</span></span>|<span data-ttu-id="d795b-116">Indique si un point de terminaison utilise la sécurité au niveau du transport ou s'il n'utilise aucune sécurité.</span><span class="sxs-lookup"><span data-stu-id="d795b-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="d795b-117">La valeur par défaut est `None`.</span><span class="sxs-lookup"><span data-stu-id="d795b-117">The default is `None`.</span></span> <span data-ttu-id="d795b-118">Cet attribut est de type <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d795b-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d795b-119">Mode, attribut</span><span class="sxs-lookup"><span data-stu-id="d795b-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="d795b-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="d795b-120">Value</span></span>|<span data-ttu-id="d795b-121">Description</span><span class="sxs-lookup"><span data-stu-id="d795b-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d795b-122">None</span><span class="sxs-lookup"><span data-stu-id="d795b-122">None</span></span>|<span data-ttu-id="d795b-123">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="d795b-123">Security is disabled.</span></span>|  
|<span data-ttu-id="d795b-124">Transport</span><span class="sxs-lookup"><span data-stu-id="d795b-124">Transport</span></span>|<span data-ttu-id="d795b-125">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d795b-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="d795b-126">Le service doit être configuré avec les certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="d795b-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="d795b-127">Le message est entièrement sécurisé à l’aide du protocole HTTPS et le service est authentifié par le client à l’aide du certificat SSL du service.</span><span class="sxs-lookup"><span data-stu-id="d795b-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="d795b-128">L’authentification du client est contrôlée par le `ClientCredentialType` attribut de la [ \<transport >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d795b-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="d795b-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="d795b-129">TransportCredentialOnly</span></span>|<span data-ttu-id="d795b-130">Ce mode n'assure pas l'intégrité et la confidentialité des messages.</span><span class="sxs-lookup"><span data-stu-id="d795b-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="d795b-131">Il fournit l'authentification du client basée sur le protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="d795b-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="d795b-132">Ce mode doit être utilisé avec précaution.</span><span class="sxs-lookup"><span data-stu-id="d795b-132">This mode should be used with caution.</span></span> <span data-ttu-id="d795b-133">Il doit être utilisé dans les environnements où la sécurité de transport est fournie par d'autres moyens (tels que IPSec) et où seule l'authentification du client est fournie par l'infrastructure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d795b-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d795b-134">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d795b-134">Child Elements</span></span>  
  
|<span data-ttu-id="d795b-135">Élément</span><span class="sxs-lookup"><span data-stu-id="d795b-135">Element</span></span>|<span data-ttu-id="d795b-136">Description</span><span class="sxs-lookup"><span data-stu-id="d795b-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d795b-137">\<transport ></span><span class="sxs-lookup"><span data-stu-id="d795b-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="d795b-138">Définit les paramètres de sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="d795b-138">Defines the transport security settings.</span></span> <span data-ttu-id="d795b-139">Cet élément correspond au type <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="d795b-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d795b-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d795b-140">Parent Elements</span></span>  
  
|<span data-ttu-id="d795b-141">Élément</span><span class="sxs-lookup"><span data-stu-id="d795b-141">Element</span></span>|<span data-ttu-id="d795b-142">Description</span><span class="sxs-lookup"><span data-stu-id="d795b-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d795b-143">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d795b-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="d795b-144">Élément de liaison utilisé pour configurer des points de terminaison pour les services Web [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] qui répondent aux requêtes HTTP au lieu des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="d795b-144">A binding element that is used to configure endpoints for [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d795b-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d795b-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="d795b-146">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="d795b-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d795b-147">Sélection d’un Type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="d795b-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="d795b-148">Liaisons</span><span class="sxs-lookup"><span data-stu-id="d795b-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d795b-149">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="d795b-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d795b-150">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d795b-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d795b-151">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="d795b-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="d795b-152">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="d795b-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
