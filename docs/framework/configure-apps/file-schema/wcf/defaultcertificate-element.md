---
title: "&lt;defaultCertificate&gt;, élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4424b8b5e0389c0a0395550fddb71ac34e0fb987
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdefaultcertificategt-element"></a><span data-ttu-id="84496-102">&lt;defaultCertificate&gt;, élément</span><span class="sxs-lookup"><span data-stu-id="84496-102">&lt;defaultCertificate&gt; Element</span></span>
<span data-ttu-id="84496-103">Spécifie un certificat X.509 à utiliser lorsqu'un service ou un service d'émission de jeton de sécurité n'en fournit pas un via un protocole de négociation.</span><span class="sxs-lookup"><span data-stu-id="84496-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="84496-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="84496-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="84496-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="84496-105">\<behaviors></span></span>  
<span data-ttu-id="84496-106">section d’endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="84496-106">endpointBehaviors section</span></span>  
<span data-ttu-id="84496-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="84496-107">\<behavior></span></span>  
<span data-ttu-id="84496-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="84496-108">\<clientCredentials></span></span>  
<span data-ttu-id="84496-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="84496-109">\<serviceCertificate></span></span>  
<span data-ttu-id="84496-110">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="84496-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84496-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84496-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84496-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="84496-112">Attributes and Elements</span></span>  
 <span data-ttu-id="84496-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="84496-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84496-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="84496-114">Attributes</span></span>  
  
|<span data-ttu-id="84496-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="84496-115">Attribute</span></span>|<span data-ttu-id="84496-116">Description</span><span class="sxs-lookup"><span data-stu-id="84496-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84496-117">findValue</span><span class="sxs-lookup"><span data-stu-id="84496-117">findValue</span></span>|<span data-ttu-id="84496-118">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="84496-118">String.</span></span> <span data-ttu-id="84496-119">La valeur à rechercher.</span><span class="sxs-lookup"><span data-stu-id="84496-119">The value to search for.</span></span>|  
|<span data-ttu-id="84496-120">x509FindType</span><span class="sxs-lookup"><span data-stu-id="84496-120">x509FindType</span></span>|<span data-ttu-id="84496-121">Énumération.</span><span class="sxs-lookup"><span data-stu-id="84496-121">Enumeration.</span></span> <span data-ttu-id="84496-122">L'un des champs de certificat à rechercher.</span><span class="sxs-lookup"><span data-stu-id="84496-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="84496-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="84496-123">storeLocation</span></span>|<span data-ttu-id="84496-124">Énumération.</span><span class="sxs-lookup"><span data-stu-id="84496-124">Enumeration.</span></span> <span data-ttu-id="84496-125">L'un des deux emplacements du magasin du système à rechercher.</span><span class="sxs-lookup"><span data-stu-id="84496-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="84496-126">storeName</span><span class="sxs-lookup"><span data-stu-id="84496-126">storeName</span></span>|<span data-ttu-id="84496-127">Énumération.</span><span class="sxs-lookup"><span data-stu-id="84496-127">Enumeration.</span></span> <span data-ttu-id="84496-128">L'un des magasins de systèmes à rechercher.</span><span class="sxs-lookup"><span data-stu-id="84496-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="84496-129">findValue, attribute</span><span class="sxs-lookup"><span data-stu-id="84496-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="84496-130">Valeur</span><span class="sxs-lookup"><span data-stu-id="84496-130">Value</span></span>|<span data-ttu-id="84496-131">Description</span><span class="sxs-lookup"><span data-stu-id="84496-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84496-132">Chaîne</span><span class="sxs-lookup"><span data-stu-id="84496-132">String</span></span>|<span data-ttu-id="84496-133">La valeur dépend du champ (spécifié par l'attribut X509FindType) qui est recherché.</span><span class="sxs-lookup"><span data-stu-id="84496-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="84496-134">Par exemple, lors de la recherche d'une empreinte numérique, la valeur doit être une chaîne de nombres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="84496-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="84496-135">x509FindType, attribut</span><span class="sxs-lookup"><span data-stu-id="84496-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="84496-136">Valeur</span><span class="sxs-lookup"><span data-stu-id="84496-136">Value</span></span>|<span data-ttu-id="84496-137">Description</span><span class="sxs-lookup"><span data-stu-id="84496-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84496-138">Énumération</span><span class="sxs-lookup"><span data-stu-id="84496-138">Enumeration</span></span>|<span data-ttu-id="84496-139">Les valeurs comprennent : FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="84496-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="84496-140">storeLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="84496-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="84496-141">Valeur</span><span class="sxs-lookup"><span data-stu-id="84496-141">Value</span></span>|<span data-ttu-id="84496-142">Description</span><span class="sxs-lookup"><span data-stu-id="84496-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84496-143">Énumération</span><span class="sxs-lookup"><span data-stu-id="84496-143">Enumeration</span></span>|<span data-ttu-id="84496-144">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="84496-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="84496-145">storeName, attribut</span><span class="sxs-lookup"><span data-stu-id="84496-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="84496-146">Valeur</span><span class="sxs-lookup"><span data-stu-id="84496-146">Value</span></span>|<span data-ttu-id="84496-147">Description</span><span class="sxs-lookup"><span data-stu-id="84496-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84496-148">Énumération</span><span class="sxs-lookup"><span data-stu-id="84496-148">Enumeration</span></span>|<span data-ttu-id="84496-149">Les valeurs comprennent : AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople et TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="84496-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84496-150">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="84496-150">Child Elements</span></span>  
 <span data-ttu-id="84496-151">Aucun.</span><span class="sxs-lookup"><span data-stu-id="84496-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84496-152">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="84496-152">Parent Elements</span></span>  
  
|<span data-ttu-id="84496-153">Élément</span><span class="sxs-lookup"><span data-stu-id="84496-153">Element</span></span>|<span data-ttu-id="84496-154">Description</span><span class="sxs-lookup"><span data-stu-id="84496-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84496-155">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="84496-155">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="84496-156">Spécifie un certificat à utiliser lors de l'authentification d'un service au client.</span><span class="sxs-lookup"><span data-stu-id="84496-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84496-157">Remarques</span><span class="sxs-lookup"><span data-stu-id="84496-157">Remarks</span></span>  
 <span data-ttu-id="84496-158">Pour les liaisons qui utilisent la sécurité de message basée sur des certificats, le certificat spécifié par cet élément de configuration est utilisé pour chiffrer les messages au service et doit être utilisé par le service pour signer les réponses au client.</span><span class="sxs-lookup"><span data-stu-id="84496-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="84496-159">Il stocke un certificat unique à utiliser lorsqu'aucun certificat n'est spécifié par un service.</span><span class="sxs-lookup"><span data-stu-id="84496-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84496-160">Exemple</span><span class="sxs-lookup"><span data-stu-id="84496-160">Example</span></span>  
 <span data-ttu-id="84496-161">L'exemple suivant spécifie un certificat à utiliser pour les points de terminaison dont l'URI commence par http://www.contoso.com et un certificat à utiliser pour tous les autres points de terminaison qui n'exécutent pas la négociation de certificat.</span><span class="sxs-lookup"><span data-stu-id="84496-161">The following example specifies a certificate to use for endpoints whose URI begins with http://www.contoso.com and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="84496-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84496-162">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [<span data-ttu-id="84496-163">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="84496-163">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="84496-164">\<authentification ></span><span class="sxs-lookup"><span data-stu-id="84496-164">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="84496-165">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="84496-165">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="84496-166">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="84496-166">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
