---
title: '&lt;certificate&gt; de &lt;peer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1449bab5d585183d73da5ca0d2234857d9d92151
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltcertificategt-of-ltpeergt"></a><span data-ttu-id="365dd-102">&lt;certificate&gt; de &lt;peer&gt;</span><span class="sxs-lookup"><span data-stu-id="365dd-102">&lt;certificate&gt; of &lt;peer&gt;</span></span>
<span data-ttu-id="365dd-103">Spécifie un certificat utilisé par un homologue.</span><span class="sxs-lookup"><span data-stu-id="365dd-103">Specifies a certificate used by a peer.</span></span>  
  
 <span data-ttu-id="365dd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="365dd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="365dd-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="365dd-105">\<behaviors></span></span>  
<span data-ttu-id="365dd-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="365dd-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="365dd-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="365dd-107">\<behavior></span></span>  
<span data-ttu-id="365dd-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="365dd-108">\<serviceCredentials></span></span>  
<span data-ttu-id="365dd-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="365dd-109">\<peer></span></span>  
<span data-ttu-id="365dd-110">\<certificate></span><span class="sxs-lookup"><span data-stu-id="365dd-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="365dd-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="365dd-111">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="365dd-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="365dd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="365dd-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="365dd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="365dd-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="365dd-114">Attributes</span></span>  
  
|<span data-ttu-id="365dd-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="365dd-115">Attribute</span></span>|<span data-ttu-id="365dd-116">Description</span><span class="sxs-lookup"><span data-stu-id="365dd-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="365dd-117">Chaîne qui contient la valeur à rechercher dans le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="365dd-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="365dd-118">Le type contenu dans l'attribut doit répondre aux spécifications du `x509FindType` spécifié.</span><span class="sxs-lookup"><span data-stu-id="365dd-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="365dd-119">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="365dd-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="365dd-120">Indique l'emplacement du magasin de certificats X.509 utilisé par le client pour valider le certificat de l'homologue.</span><span class="sxs-lookup"><span data-stu-id="365dd-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="365dd-121">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="365dd-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="365dd-122">-LocalMachine : magasin de certificats assigné à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="365dd-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="365dd-123">-CurrentUser : magasin de certificats assigné à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="365dd-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="365dd-124">La valeur par défaut est LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="365dd-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="365dd-125">Spécifie le nom du magasin de certificats X.509 à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="365dd-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="365dd-126">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="365dd-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="365dd-127">-AddressBook : Magasin de certificats pour d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="365dd-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="365dd-128">-AuthRoot : Magasin de certificats pour les autorités de certification (CA) tierces.</span><span class="sxs-lookup"><span data-stu-id="365dd-128">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="365dd-129">-CertificateAuthority : Magasin des autorités de certification intermédiaires (CA).</span><span class="sxs-lookup"><span data-stu-id="365dd-129">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="365dd-130">-Disallowed : Magasin de certificats pour les certificats révoqués.</span><span class="sxs-lookup"><span data-stu-id="365dd-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="365dd-131">-My : Magasin de certificats pour les certificats personnels.</span><span class="sxs-lookup"><span data-stu-id="365dd-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="365dd-132">-Root : Magasin de certificats pour autorités de certification racine de confiance (CA).</span><span class="sxs-lookup"><span data-stu-id="365dd-132">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="365dd-133">-TrustedPeople : Magasin de certificats pour directement approuvées de personnes et les ressources.</span><span class="sxs-lookup"><span data-stu-id="365dd-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="365dd-134">-TrustedPublisher : Magasin de certificats pour les éditeurs directement approuvés.</span><span class="sxs-lookup"><span data-stu-id="365dd-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="365dd-135">La valeur par défaut est My.</span><span class="sxs-lookup"><span data-stu-id="365dd-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="365dd-136">Définit le type de recherche X.509 à exécuter.</span><span class="sxs-lookup"><span data-stu-id="365dd-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="365dd-137">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="365dd-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="365dd-138">-   FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="365dd-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="365dd-139">-   FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="365dd-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="365dd-140">-   FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="365dd-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="365dd-141">-   FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="365dd-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="365dd-142">-   FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="365dd-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="365dd-143">-   FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="365dd-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="365dd-144">-   FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="365dd-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="365dd-145">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="365dd-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="365dd-146">-   FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="365dd-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="365dd-147">-   FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="365dd-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="365dd-148">-   FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="365dd-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="365dd-149">-   FindByExtension</span><span class="sxs-lookup"><span data-stu-id="365dd-149">-   FindByExtension</span></span><br /><span data-ttu-id="365dd-150">-   FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="365dd-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="365dd-151">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="365dd-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="365dd-152">Le type contenu dans l'attribut `findValue` doit répondre aux spécifications du `X509FindType` spécifié.</span><span class="sxs-lookup"><span data-stu-id="365dd-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="365dd-153">La valeur par défaut est FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="365dd-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="365dd-154">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="365dd-154">Child Elements</span></span>  
 <span data-ttu-id="365dd-155">Aucun.</span><span class="sxs-lookup"><span data-stu-id="365dd-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="365dd-156">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="365dd-156">Parent Elements</span></span>  
  
|<span data-ttu-id="365dd-157">Élément</span><span class="sxs-lookup"><span data-stu-id="365dd-157">Element</span></span>|<span data-ttu-id="365dd-158">Description</span><span class="sxs-lookup"><span data-stu-id="365dd-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="365dd-159">\<peer></span><span class="sxs-lookup"><span data-stu-id="365dd-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="365dd-160">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="365dd-160">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="365dd-161">Notes</span><span class="sxs-lookup"><span data-stu-id="365dd-161">Remarks</span></span>  
 <span data-ttu-id="365dd-162">Cet élément de configuration contient une instance de `X509Certificate2` utilisée lors de l'authentification de voisins dans la maille d'homologues.</span><span class="sxs-lookup"><span data-stu-id="365dd-162">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="365dd-163">Pour plus d’informations sur la programmation d’égal à égal, consultez [mise en réseau pair à pair](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="365dd-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="365dd-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="365dd-164">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="365dd-165">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="365dd-165">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="365dd-166">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="365dd-166">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="365dd-167">Authentification de Message de canal homologue</span><span class="sxs-lookup"><span data-stu-id="365dd-167">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="365dd-168">Authentification personnalisée de canal homologue</span><span class="sxs-lookup"><span data-stu-id="365dd-168">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="365dd-169">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="365dd-169">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="365dd-170">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="365dd-170">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
