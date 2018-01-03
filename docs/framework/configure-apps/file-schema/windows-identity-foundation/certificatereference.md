---
title: '&lt;certificateReference&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: fd0d4742a162000d438851cef9c00e21368b7ba1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="88adb-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="88adb-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="88adb-103">Spécifie les paramètres qui sont utilisés pour rechercher et valider un certificat X.509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="88adb-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="88adb-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="88adb-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="88adb-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="88adb-105">\<federationConfiguration></span></span>  
<span data-ttu-id="88adb-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="88adb-106">\<serviceCertificate></span></span>  
<span data-ttu-id="88adb-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="88adb-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88adb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88adb-108">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88adb-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="88adb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="88adb-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="88adb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88adb-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="88adb-111">Attributes</span></span>  
  
|<span data-ttu-id="88adb-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="88adb-112">Attribute</span></span>|<span data-ttu-id="88adb-113">Description</span><span class="sxs-lookup"><span data-stu-id="88adb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88adb-114">storeName</span><span class="sxs-lookup"><span data-stu-id="88adb-114">storeName</span></span>|<span data-ttu-id="88adb-115">Le nom du magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="88adb-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="88adb-116">La valeur par défaut est « My ».</span><span class="sxs-lookup"><span data-stu-id="88adb-116">The default is "My".</span></span> <span data-ttu-id="88adb-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="88adb-117">Optional.</span></span>|  
|<span data-ttu-id="88adb-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="88adb-118">storeLocation</span></span>|<span data-ttu-id="88adb-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui spécifie l’emplacement du magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="88adb-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="88adb-120">La valeur par défaut est « Ordinateur_local ».</span><span class="sxs-lookup"><span data-stu-id="88adb-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="88adb-121">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="88adb-121">Optional.</span></span>|  
|<span data-ttu-id="88adb-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="88adb-122">x509FindType</span></span>|<span data-ttu-id="88adb-123">Un <xref:System.Security.Cryptography.X509Certificates.X509FindType> valeur qui spécifie le type de recherche doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="88adb-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="88adb-124">La valeur par défaut est « FindBySubjectDistinguishedName ».</span><span class="sxs-lookup"><span data-stu-id="88adb-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="88adb-125">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="88adb-125">Optional.</span></span>|  
|<span data-ttu-id="88adb-126">findValue</span><span class="sxs-lookup"><span data-stu-id="88adb-126">findValue</span></span>|<span data-ttu-id="88adb-127">Valeur à rechercher dans le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="88adb-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="88adb-128">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="88adb-128">Optional.</span></span>|  
|<span data-ttu-id="88adb-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="88adb-129">isChainIncluded</span></span>|<span data-ttu-id="88adb-130">Spécifie si la validation doit être effectuée à l’aide de la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="88adb-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="88adb-131">La valeur par défaut est « true » ; la validation est effectuée à l’aide de la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="88adb-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="88adb-132">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="88adb-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88adb-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="88adb-133">Child Elements</span></span>  
 <span data-ttu-id="88adb-134">Aucun.</span><span class="sxs-lookup"><span data-stu-id="88adb-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88adb-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="88adb-135">Parent Elements</span></span>  
  
|<span data-ttu-id="88adb-136">Élément</span><span class="sxs-lookup"><span data-stu-id="88adb-136">Element</span></span>|<span data-ttu-id="88adb-137">Description</span><span class="sxs-lookup"><span data-stu-id="88adb-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88adb-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="88adb-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="88adb-139">Configure le certificat qui est utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="88adb-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88adb-140">Notes</span><span class="sxs-lookup"><span data-stu-id="88adb-140">Remarks</span></span>  
 <span data-ttu-id="88adb-141">Le `<certificateReference>` élément spécifie les paramètres qui permettent de rechercher et de valider le certificat dans un magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="88adb-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="88adb-142">Lorsqu’il est spécifié en tant qu’élément enfant de le `<serviceCertficate>` élément, il spécifie les paramètres d’emplacement et la vérification du certificat X.509 qui est utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="88adb-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="88adb-143">Le `<certificateReference>` élément est représenté par la <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.</span><span class="sxs-lookup"><span data-stu-id="88adb-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
