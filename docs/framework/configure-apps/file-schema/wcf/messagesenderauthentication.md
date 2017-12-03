---
title: '&lt;messageSenderAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a008919cc068ca5cdd841ec67f1a7194bbffcd8c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagesenderauthenticationgt"></a><span data-ttu-id="c60fd-102">&lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="c60fd-102">&lt;messageSenderAuthentication&gt;</span></span>
<span data-ttu-id="c60fd-103">Spécifie les paramètres d'authentification pour le certificat homologue utilisé par l'expéditeur d'un message.</span><span class="sxs-lookup"><span data-stu-id="c60fd-103">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="c60fd-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c60fd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c60fd-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="c60fd-105">\<behaviors></span></span>  
<span data-ttu-id="c60fd-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c60fd-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c60fd-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="c60fd-107">\<behavior></span></span>  
<span data-ttu-id="c60fd-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="c60fd-108">\<serviceCredentials></span></span>  
<span data-ttu-id="c60fd-109">\<homologue ></span><span class="sxs-lookup"><span data-stu-id="c60fd-109">\<peer></span></span>  
<span data-ttu-id="c60fd-110">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="c60fd-110">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c60fd-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c60fd-111">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c60fd-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c60fd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c60fd-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c60fd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c60fd-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="c60fd-114">Attributes</span></span>  
  
|<span data-ttu-id="c60fd-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="c60fd-115">Attribute</span></span>|<span data-ttu-id="c60fd-116">Description</span><span class="sxs-lookup"><span data-stu-id="c60fd-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="c60fd-117">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="c60fd-117">Optional enumeration.</span></span> <span data-ttu-id="c60fd-118">Spécifie l'un des cinq modes utilisés pour valider les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="c60fd-118">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="c60fd-119">Cet attribut est de type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="c60fd-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="c60fd-120">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="c60fd-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="c60fd-121">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="c60fd-121">Optional string.</span></span> <span data-ttu-id="c60fd-122">Spécifie un type et un assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c60fd-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="c60fd-123">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="c60fd-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="c60fd-124">Cet attribut est de type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="c60fd-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="c60fd-125"> fournit un validateur de certificat homologue par défaut qui vérifie le certificat homologue par rapport au magasin de personnes de confiance.</span><span class="sxs-lookup"><span data-stu-id="c60fd-125"> provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="c60fd-126">Il vérifie également que le certificat remonte jusqu'à une racine valide.</span><span class="sxs-lookup"><span data-stu-id="c60fd-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="c60fd-127">Vous pouvez implémenter un validateur personnalisé pour spécifier un comportement différent et utiliser cet attribut pour pointer vers ce validateur.</span><span class="sxs-lookup"><span data-stu-id="c60fd-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="c60fd-128">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="c60fd-128">Optional enumeration.</span></span> <span data-ttu-id="c60fd-129">Spécifie le mode de révocation de certificat.</span><span class="sxs-lookup"><span data-stu-id="c60fd-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="c60fd-130">Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="c60fd-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="c60fd-131">Le système vérifie que le certificat homologue n'a pas été révoqué en le recherchant dans la liste des certificats révoqués.</span><span class="sxs-lookup"><span data-stu-id="c60fd-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="c60fd-132">Cette vérification peut être effectuée en ligne ou par rapport à une liste de révocations mise en cache.</span><span class="sxs-lookup"><span data-stu-id="c60fd-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="c60fd-133">La vérification de la révocation peut être désactivée en affectant la valeur NoCheck à cet attribut.</span><span class="sxs-lookup"><span data-stu-id="c60fd-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="c60fd-134">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="c60fd-134">Optional enumeration.</span></span> <span data-ttu-id="c60fd-135">Spécifie l'emplacement de magasin approuvé où le certificat homologue est validé par le système de sécurité [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c60fd-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="c60fd-136">Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="c60fd-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c60fd-137">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c60fd-137">Child Elements</span></span>  
 <span data-ttu-id="c60fd-138">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c60fd-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c60fd-139">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c60fd-139">Parent Elements</span></span>  
  
|<span data-ttu-id="c60fd-140">Élément</span><span class="sxs-lookup"><span data-stu-id="c60fd-140">Element</span></span>|<span data-ttu-id="c60fd-141">Description</span><span class="sxs-lookup"><span data-stu-id="c60fd-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c60fd-142">\<homologue ></span><span class="sxs-lookup"><span data-stu-id="c60fd-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="c60fd-143">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="c60fd-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c60fd-144">Remarques</span><span class="sxs-lookup"><span data-stu-id="c60fd-144">Remarks</span></span>  
 <span data-ttu-id="c60fd-145">Cet élément doit être configuré si l'authentification des messages est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="c60fd-145">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="c60fd-146">Pour les canaux de sortie, chaque message est signé à l’aide du certificat fourni par [ \<certificat >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="c60fd-146">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="c60fd-147">Avant d'être remis à l'application, tous les messages sont vérifiés par rapport aux informations d'identification de message à l'aide du validateur spécifié par l'attribut `customCertificateValidatorType` de cet élément.</span><span class="sxs-lookup"><span data-stu-id="c60fd-147">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="c60fd-148">Le validateur peut accepter ou rejeter les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="c60fd-148">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c60fd-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c60fd-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [<span data-ttu-id="c60fd-150">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="c60fd-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="c60fd-151">Mise en réseau pair à pair</span><span class="sxs-lookup"><span data-stu-id="c60fd-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="c60fd-152">Authentification de Message de canal homologue</span><span class="sxs-lookup"><span data-stu-id="c60fd-152">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="c60fd-153">Authentification personnalisée de canal homologue</span><span class="sxs-lookup"><span data-stu-id="c60fd-153">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="c60fd-154">Sécurisation des Applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="c60fd-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
