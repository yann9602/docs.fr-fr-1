---
title: '&lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 834853d8a922148d2810cd391a64a281f2f9ae3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcredentialsgt"></a><span data-ttu-id="c6953-102">&lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="c6953-102">&lt;clientCredentials&gt;</span></span>
<span data-ttu-id="c6953-103">Indique les informations d'identification utilisées pour authentifier le client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="c6953-103">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="c6953-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c6953-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c6953-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="c6953-105">\<behaviors></span></span>  
<span data-ttu-id="c6953-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c6953-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="c6953-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="c6953-107">\<behavior></span></span>  
<span data-ttu-id="c6953-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="c6953-108">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6953-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6953-109">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"  
      supportInteractive="Boolean" >  
   <clientCertificate>  
   </clientCertificate>  
   <digest>  
   </digest>  
   <isuedToken>  
   </isuedToken>  
   <peer>  
   </peer>  
   <serviceCertificate>  
   </serviceCertificate>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</clientCredentials>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6953-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c6953-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c6953-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c6953-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6953-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="c6953-112">Attributes</span></span>  
  
|<span data-ttu-id="c6953-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="c6953-113">Attribute</span></span>|<span data-ttu-id="c6953-114">Description</span><span class="sxs-lookup"><span data-stu-id="c6953-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="c6953-115">Valeur booléenne indiquant si un utilisateur interactif peut sélectionner les informations d'identification d'un client pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="c6953-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="c6953-116">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="c6953-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="c6953-117">Chaîne qui spécifie le type de cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="c6953-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6953-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c6953-118">Child Elements</span></span>  
  
|<span data-ttu-id="c6953-119">Élément</span><span class="sxs-lookup"><span data-stu-id="c6953-119">Element</span></span>|<span data-ttu-id="c6953-120">Description</span><span class="sxs-lookup"><span data-stu-id="c6953-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6953-121">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="c6953-121">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="c6953-122">Indique le certificat utilisé pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="c6953-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="c6953-123">Cet élément est de type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="c6953-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="c6953-124">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="c6953-124">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="c6953-125">Indique un condensat utilisé pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="c6953-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="c6953-126">Cet élément est de type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="c6953-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="c6953-127">\<jeton issuedToken ></span><span class="sxs-lookup"><span data-stu-id="c6953-127">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="c6953-128">Spécifie un type de jeton personnalisé utilisé pour authentifier le client à un service STS.</span><span class="sxs-lookup"><span data-stu-id="c6953-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="c6953-129">Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="c6953-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="c6953-130">\<homologue ></span><span class="sxs-lookup"><span data-stu-id="c6953-130">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="c6953-131">Spécifie des informations d'identification d'homologue actuelles.</span><span class="sxs-lookup"><span data-stu-id="c6953-131">Specifies a current peer credential.</span></span> <span data-ttu-id="c6953-132">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="c6953-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="c6953-133">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="c6953-133">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="c6953-134">Spécifie le certificat utilisé pour authentifier le service auprès du client et fournit une structure permettant de définir des options de certificat.</span><span class="sxs-lookup"><span data-stu-id="c6953-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="c6953-135">Ce certificat doit être fourni au client hors bande, à partir du service.</span><span class="sxs-lookup"><span data-stu-id="c6953-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="c6953-136">Cet élément est de type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="c6953-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="c6953-137">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="c6953-137">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="c6953-138">Indique des informations d'identification Windows.</span><span class="sxs-lookup"><span data-stu-id="c6953-138">Specifies a Windows credential.</span></span> <span data-ttu-id="c6953-139">La valeur par défaut correspond aux informations d'identification du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="c6953-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="c6953-140">Cet élément est de type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="c6953-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6953-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c6953-141">Parent Elements</span></span>  
  
|<span data-ttu-id="c6953-142">Élément</span><span class="sxs-lookup"><span data-stu-id="c6953-142">Element</span></span>|<span data-ttu-id="c6953-143">Description</span><span class="sxs-lookup"><span data-stu-id="c6953-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6953-144">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="c6953-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c6953-145">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c6953-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6953-146">Remarques</span><span class="sxs-lookup"><span data-stu-id="c6953-146">Remarks</span></span>  
 <span data-ttu-id="c6953-147">Les informations d'identification du client permettent d'authentifier le client auprès des services dans les cas où l'authentification mutuelle est requise.</span><span class="sxs-lookup"><span data-stu-id="c6953-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="c6953-148">Cette section de configuration peut également servir à spécifier des certificats de service pour les scénarios dans lesquels le client doit sécuriser des messages auprès d'un service à l'aide du certificat de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="c6953-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6953-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6953-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [<span data-ttu-id="c6953-150">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="c6953-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="c6953-151">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="c6953-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
