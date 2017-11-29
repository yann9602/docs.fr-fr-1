---
title: '&lt;transport&gt; de &lt;webHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 44397edf2d2c5e2f99a255789452b08d91484b81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a><span data-ttu-id="2a891-102">&lt;transport&gt; de &lt;webHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="2a891-102">&lt;transport&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="2a891-103">Définit les paramètres de sécurité au niveau du transport pour un point de terminaison de service configuré pour recevoir des demandes HTTP.</span><span class="sxs-lookup"><span data-stu-id="2a891-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="2a891-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2a891-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a891-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="2a891-105">\<bindings></span></span>  
<span data-ttu-id="2a891-106">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="2a891-106">\<webHttpBinding></span></span>  
<span data-ttu-id="2a891-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="2a891-107">\<binding></span></span>  
<span data-ttu-id="2a891-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="2a891-108">\<security></span></span>  
<span data-ttu-id="2a891-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="2a891-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a891-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a891-110">Syntax</span></span>  
  
```xml  
<webHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</WebHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="2a891-111">Type</span><span class="sxs-lookup"><span data-stu-id="2a891-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a891-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2a891-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2a891-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2a891-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a891-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="2a891-114">Attributes</span></span>  
  
|<span data-ttu-id="2a891-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="2a891-115">Attribute</span></span>|<span data-ttu-id="2a891-116">Description</span><span class="sxs-lookup"><span data-stu-id="2a891-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="2a891-117">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="2a891-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="2a891-118">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2a891-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="2a891-119">Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.</span><span class="sxs-lookup"><span data-stu-id="2a891-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="2a891-120">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2a891-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="2a891-121">Chaîne indiquant le domaine de l'authentification de base ou Digest.</span><span class="sxs-lookup"><span data-stu-id="2a891-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="2a891-122">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="2a891-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="2a891-123">Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.</span><span class="sxs-lookup"><span data-stu-id="2a891-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="2a891-124">Il peut également spécifier une collection d'utilisateurs disposant d'un accès.</span><span class="sxs-lookup"><span data-stu-id="2a891-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="2a891-125">Un utilisateur peut interroger le domaine d'authentification pour vérifier quels noms d'utilisateurs et mots de passe peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="2a891-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="2a891-126">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="2a891-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="2a891-127">1.  Never : la stratégie n'est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="2a891-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="2a891-128">2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="2a891-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="2a891-129">3.  Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="2a891-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="2a891-130">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="2a891-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="2a891-131">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="2a891-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2a891-132">Valeur</span><span class="sxs-lookup"><span data-stu-id="2a891-132">Value</span></span>|<span data-ttu-id="2a891-133">Description</span><span class="sxs-lookup"><span data-stu-id="2a891-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="2a891-134">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="2a891-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="2a891-135">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="2a891-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="2a891-136">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="2a891-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="2a891-137">Utilise l'authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="2a891-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="2a891-138">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="2a891-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="2a891-139">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="2a891-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="2a891-140">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="2a891-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2a891-141">Valeur</span><span class="sxs-lookup"><span data-stu-id="2a891-141">Value</span></span>|<span data-ttu-id="2a891-142">Description</span><span class="sxs-lookup"><span data-stu-id="2a891-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="2a891-143">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="2a891-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="2a891-144">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="2a891-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="2a891-145">Utilise l'authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="2a891-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="2a891-146">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="2a891-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="2a891-147">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="2a891-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a891-148">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2a891-148">Child Elements</span></span>  
 <span data-ttu-id="2a891-149">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2a891-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a891-150">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2a891-150">Parent Elements</span></span>  
  
|<span data-ttu-id="2a891-151">Élément</span><span class="sxs-lookup"><span data-stu-id="2a891-151">Element</span></span>|<span data-ttu-id="2a891-152">Description</span><span class="sxs-lookup"><span data-stu-id="2a891-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a891-153">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="2a891-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="2a891-154">Représente les fonctionnalités de sécurité de le [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="2a891-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a891-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a891-155">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="2a891-156">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="2a891-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="2a891-157">Liaisons</span><span class="sxs-lookup"><span data-stu-id="2a891-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2a891-158">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="2a891-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2a891-159">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="2a891-159">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="2a891-160">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="2a891-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="2a891-161">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="2a891-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
