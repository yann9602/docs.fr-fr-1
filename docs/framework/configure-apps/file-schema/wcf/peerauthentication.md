---
title: '&lt;peerAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a900a1f3fc2e07cffe04833cc3c7d3ccd063e24a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltpeerauthenticationgt"></a><span data-ttu-id="5438c-102">&lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="5438c-102">&lt;peerAuthentication&gt;</span></span>
<span data-ttu-id="5438c-103">Spécifie des paramètres d'authentification pour un certificat d'homologue utilisé par un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="5438c-103">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="5438c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5438c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5438c-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="5438c-105">\<behaviors></span></span>  
<span data-ttu-id="5438c-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5438c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5438c-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5438c-107">\<behavior></span></span>  
<span data-ttu-id="5438c-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="5438c-108">\<serviceCredentials></span></span>  
<span data-ttu-id="5438c-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="5438c-109">\<peer></span></span>  
<span data-ttu-id="5438c-110">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5438c-110">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5438c-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5438c-111">Syntax</span></span>  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5438c-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5438c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5438c-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5438c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5438c-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="5438c-114">Attributes</span></span>  
  
|<span data-ttu-id="5438c-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="5438c-115">Attribute</span></span>|<span data-ttu-id="5438c-116">Description</span><span class="sxs-lookup"><span data-stu-id="5438c-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="5438c-117">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="5438c-117">Optional enumeration.</span></span> <span data-ttu-id="5438c-118">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="5438c-118">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="5438c-119">Cet attribut est de type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="5438c-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="5438c-120">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="5438c-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="5438c-121">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="5438c-121">Optional string.</span></span> <span data-ttu-id="5438c-122">Spécifie un type et un assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5438c-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="5438c-123">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="5438c-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="5438c-124">Cet attribut est de type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="5438c-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="5438c-125"> fournit un validateur de certificat homologue par défaut qui vérifie le certificat homologue par rapport au magasin de personnes de confiance.</span><span class="sxs-lookup"><span data-stu-id="5438c-125"> provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="5438c-126">Il vérifie également que le certificat remonte jusqu'à une racine valide.</span><span class="sxs-lookup"><span data-stu-id="5438c-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="5438c-127">Vous pouvez implémenter un validateur personnalisé pour spécifier un comportement différent et utiliser cet attribut pour pointer vers ce validateur.</span><span class="sxs-lookup"><span data-stu-id="5438c-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="5438c-128">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="5438c-128">Optional enumeration.</span></span> <span data-ttu-id="5438c-129">Spécifie le mode de révocation de certificat.</span><span class="sxs-lookup"><span data-stu-id="5438c-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="5438c-130">Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="5438c-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="5438c-131">Le système vérifie que le certificat homologue n'a pas été révoqué en le recherchant dans la liste des certificats révoqués.</span><span class="sxs-lookup"><span data-stu-id="5438c-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="5438c-132">Cette vérification peut être effectuée en ligne ou par rapport à une liste de révocations mise en cache.</span><span class="sxs-lookup"><span data-stu-id="5438c-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="5438c-133">La vérification de la révocation peut être désactivée en affectant la valeur NoCheck à cet attribut.</span><span class="sxs-lookup"><span data-stu-id="5438c-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="5438c-134">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="5438c-134">Optional enumeration.</span></span> <span data-ttu-id="5438c-135">Spécifie l'emplacement de magasin approuvé où le certificat homologue est validé par le système de sécurité [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5438c-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="5438c-136">Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="5438c-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5438c-137">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5438c-137">Child Elements</span></span>  
 <span data-ttu-id="5438c-138">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5438c-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5438c-139">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5438c-139">Parent Elements</span></span>  
  
|<span data-ttu-id="5438c-140">Élément</span><span class="sxs-lookup"><span data-stu-id="5438c-140">Element</span></span>|<span data-ttu-id="5438c-141">Description</span><span class="sxs-lookup"><span data-stu-id="5438c-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5438c-142">\<peer></span><span class="sxs-lookup"><span data-stu-id="5438c-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="5438c-143">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="5438c-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5438c-144">Notes</span><span class="sxs-lookup"><span data-stu-id="5438c-144">Remarks</span></span>  
 <span data-ttu-id="5438c-145">L'élément `<authentication>` correspond à la classe <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>.</span><span class="sxs-lookup"><span data-stu-id="5438c-145">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="5438c-146">Cet élément spécifie un validateur, appelé pendant l'authentification de voisins dans la maille.</span><span class="sxs-lookup"><span data-stu-id="5438c-146">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="5438c-147">Lorsqu'un nouvel homologue essaie d'établir une connexion avec un voisin, il transmet ses propres informations d'identification à l'homologue répondant.</span><span class="sxs-lookup"><span data-stu-id="5438c-147">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="5438c-148">Le validateur du répondeur est appelé pour vérifier les informations d'identification du tiers distant.</span><span class="sxs-lookup"><span data-stu-id="5438c-148">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="5438c-149">Chaque fois qu'une connexion est établie avec un homologue de la maille, les deux homologues sont authentifiés mutuellement, ce qui signifie que des validateurs sont appelés à chaque extrémité.</span><span class="sxs-lookup"><span data-stu-id="5438c-149">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5438c-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5438c-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="5438c-151">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="5438c-151">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="5438c-152">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="5438c-152">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="5438c-153">Authentification de Message de canal homologue</span><span class="sxs-lookup"><span data-stu-id="5438c-153">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="5438c-154">Authentification personnalisée de canal homologue</span><span class="sxs-lookup"><span data-stu-id="5438c-154">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="5438c-155">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="5438c-155">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
