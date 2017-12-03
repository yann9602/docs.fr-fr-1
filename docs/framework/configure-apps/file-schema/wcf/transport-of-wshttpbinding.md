---
title: '&lt;transport&gt; de &lt;wsHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e1ea5fc60f4dc64fd895469b580b81379da26191
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a><span data-ttu-id="ba9e5-102">&lt;transport&gt; de &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="ba9e5-102">&lt;transport&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="ba9e5-103">Définit les paramètres d'authentification correspondant au transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="ba9e5-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ba9e5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ba9e5-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="ba9e5-105">\<bindings></span></span>  
<span data-ttu-id="ba9e5-106">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ba9e5-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="ba9e5-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="ba9e5-107">\<binding></span></span>  
<span data-ttu-id="ba9e5-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="ba9e5-108">\<security></span></span>  
<span data-ttu-id="ba9e5-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="ba9e5-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba9e5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba9e5-110">Syntax</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding>  
        <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport  
            clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"  
            proxyCredentialType="Basic|Digest|None|Ntlm|Windows"  
            realm="string" />  
                <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always" protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                </extendedProtecutionPolicy>  
            </transport>  
        </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="ba9e5-111">Type</span><span class="sxs-lookup"><span data-stu-id="ba9e5-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba9e5-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ba9e5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ba9e5-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba9e5-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="ba9e5-114">Attributes</span></span>  
  
|<span data-ttu-id="ba9e5-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="ba9e5-115">Attribute</span></span>|<span data-ttu-id="ba9e5-116">Description</span><span class="sxs-lookup"><span data-stu-id="ba9e5-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="ba9e5-117">Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="ba9e5-118">Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="ba9e5-119">Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="ba9e5-120">Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="ba9e5-121">Chaîne indiquant le domaine de l'authentification de base ou Digest.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="ba9e5-122">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ba9e5-123">Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="ba9e5-124">Il peut également spécifier une collection d'utilisateurs disposant d'un accès.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="ba9e5-125">Un utilisateur peut interroger le domaine d'authentification pour vérifier quels noms d'utilisateurs et mots de passe peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="ba9e5-126">Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="ba9e5-127">1.  Never : la stratégie n'est jamais appliquée (la protection étendue est désactivée).</span><span class="sxs-lookup"><span data-stu-id="ba9e5-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="ba9e5-128">2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="ba9e5-129">3.  Always : la stratégie est toujours appliquée.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="ba9e5-130">Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="ba9e5-131">Attribut clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="ba9e5-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ba9e5-132">Valeur</span><span class="sxs-lookup"><span data-stu-id="ba9e5-132">Value</span></span>|<span data-ttu-id="ba9e5-133">Description</span><span class="sxs-lookup"><span data-stu-id="ba9e5-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="ba9e5-134">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="ba9e5-135">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-135">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="ba9e5-136">Utilise l'authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-136">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="ba9e5-137">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="ba9e5-138">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-138">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="ba9e5-139">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-139">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="ba9e5-140">Attribut proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="ba9e5-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ba9e5-141">Valeur</span><span class="sxs-lookup"><span data-stu-id="ba9e5-141">Value</span></span>|<span data-ttu-id="ba9e5-142">Description</span><span class="sxs-lookup"><span data-stu-id="ba9e5-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="ba9e5-143">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="ba9e5-144">Utilise l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="ba9e5-145">Utilise l'authentification Digest.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="ba9e5-146">Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="ba9e5-147">Utilise l'authentification intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-147">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="ba9e5-148">Utilise des certificats X.509 pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-148">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba9e5-149">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ba9e5-149">Child Elements</span></span>  
 <span data-ttu-id="ba9e5-150">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ba9e5-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba9e5-151">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ba9e5-151">Parent Elements</span></span>  
  
|<span data-ttu-id="ba9e5-152">Élément</span><span class="sxs-lookup"><span data-stu-id="ba9e5-152">Element</span></span>|<span data-ttu-id="ba9e5-153">Description</span><span class="sxs-lookup"><span data-stu-id="ba9e5-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba9e5-154">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="ba9e5-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="ba9e5-155">Représente les fonctionnalités de sécurité de le [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ba9e5-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba9e5-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba9e5-156">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="ba9e5-157">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="ba9e5-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="ba9e5-158">Liaisons</span><span class="sxs-lookup"><span data-stu-id="ba9e5-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ba9e5-159">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="ba9e5-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ba9e5-160">Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ba9e5-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="ba9e5-161">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="ba9e5-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
