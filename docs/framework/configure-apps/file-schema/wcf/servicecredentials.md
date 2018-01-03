---
title: '&lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00567c32b800bb98386e15b2ba822ccc9623d72b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="71673-102">&lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="71673-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="71673-103">Spécifie l’information d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="71673-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="71673-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="71673-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="71673-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="71673-105">\<behaviors></span></span>  
<span data-ttu-id="71673-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="71673-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="71673-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="71673-107">\<behavior></span></span>  
<span data-ttu-id="71673-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="71673-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71673-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71673-109">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">  
   <clientCertificate>  
   </clientCertificate>  
   <issuedTokenAuthentication>  
   </issuedTokenAuthentication>  
   <peer>  
   </peer>  
   <secureConversationAuthentication>  
   </secureConversationAuthentication>  
   <serviceCertificate>  
   </serviceCertificate>  
   <userNameAuthentication>  
   </userNameAuthentication>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</serviceCredentials>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71673-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="71673-110">Attributes and Elements</span></span>  
 <span data-ttu-id="71673-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="71673-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71673-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="71673-112">Attributes</span></span>  
  
|<span data-ttu-id="71673-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="71673-113">Attribute</span></span>|<span data-ttu-id="71673-114">Description</span><span class="sxs-lookup"><span data-stu-id="71673-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="71673-115">Chaîne qui spécifie le type de cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="71673-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71673-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="71673-116">Child Elements</span></span>  
  
|<span data-ttu-id="71673-117">Élément</span><span class="sxs-lookup"><span data-stu-id="71673-117">Element</span></span>|<span data-ttu-id="71673-118">Description</span><span class="sxs-lookup"><span data-stu-id="71673-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71673-119">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="71673-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="71673-120">Spécifie le certificat à utiliser lorsque le certificat client est disponible hors bande.</span><span class="sxs-lookup"><span data-stu-id="71673-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="71673-121">Cet élément spécifie également les paramètres de validation du certificat client.</span><span class="sxs-lookup"><span data-stu-id="71673-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="71673-122">Cet élément est de type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="71673-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="71673-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="71673-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="71673-124">Spécifie le jeton émis actuellement pour ce service.</span><span class="sxs-lookup"><span data-stu-id="71673-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="71673-125">Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="71673-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="71673-126">\<homologue ></span><span class="sxs-lookup"><span data-stu-id="71673-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="71673-127">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="71673-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="71673-128">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="71673-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="71673-129">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="71673-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="71673-130">Spécifie les informations d'identification actuelles pour une conversation sécurisée.</span><span class="sxs-lookup"><span data-stu-id="71673-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="71673-131">Cet élément est de type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="71673-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="71673-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="71673-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="71673-133">Spécifie un certificat utilisé par un service pour s'identifier.</span><span class="sxs-lookup"><span data-stu-id="71673-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="71673-134">Cet élément est de type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="71673-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="71673-135">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="71673-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="71673-136">Spécifie les paramètres pour la validation du mot de passe du nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="71673-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="71673-137">Cet élément est de type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="71673-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="71673-138">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="71673-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="71673-139">Spécifie les paramètres de validation des informations d’identification Windows.</span><span class="sxs-lookup"><span data-stu-id="71673-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="71673-140">Cet élément est de type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="71673-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="71673-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="71673-141">Parent Elements</span></span>  
  
|<span data-ttu-id="71673-142">Élément</span><span class="sxs-lookup"><span data-stu-id="71673-142">Element</span></span>|<span data-ttu-id="71673-143">Description</span><span class="sxs-lookup"><span data-stu-id="71673-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71673-144">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="71673-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="71673-145">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="71673-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71673-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71673-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [<span data-ttu-id="71673-147">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="71673-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
