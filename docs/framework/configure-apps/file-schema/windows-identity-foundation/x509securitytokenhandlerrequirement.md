---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7cb9eb1e7e80837e8036a8241a3a6bd679ed5e11
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="3c685-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="3c685-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="3c685-103">Fournit une configuration facultative pour le <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="3c685-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="3c685-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="3c685-104">\<system.identityModel></span></span>  
<span data-ttu-id="3c685-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3c685-105">\<identityConfiguration></span></span>  
<span data-ttu-id="3c685-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="3c685-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3c685-107">\<add></span><span class="sxs-lookup"><span data-stu-id="3c685-107">\<add></span></span>  
<span data-ttu-id="3c685-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="3c685-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c685-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c685-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c685-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3c685-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3c685-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3c685-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c685-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="3c685-112">Attributes</span></span>  
  
|<span data-ttu-id="3c685-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="3c685-113">Attribute</span></span>|<span data-ttu-id="3c685-114">Description</span><span class="sxs-lookup"><span data-stu-id="3c685-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c685-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="3c685-115">certificateValidationMode</span></span>|<span data-ttu-id="3c685-116">Un <xref:System.ServiceModel.Security.X509CertificateValidationMode> valeur qui spécifie le mode de validation à utiliser pour le certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="3c685-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="3c685-117">La valeur par défaut est « PeerOrChainTrust ».</span><span class="sxs-lookup"><span data-stu-id="3c685-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="3c685-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="3c685-118">mapToWindows</span></span>|<span data-ttu-id="3c685-119">Spécifie si le Gestionnaire de jetons doit mapper le jeton de validation à un compte Windows à l’aide de la revendication UPN entrante.</span><span class="sxs-lookup"><span data-stu-id="3c685-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="3c685-120">La valeur par défaut est « false ».</span><span class="sxs-lookup"><span data-stu-id="3c685-120">The default is "false".</span></span>|  
|<span data-ttu-id="3c685-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="3c685-121">revocationMode</span></span>|<span data-ttu-id="3c685-122">Un <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valeur qui spécifie le mode de révocation à utiliser pour le certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="3c685-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="3c685-123">La valeur par défaut est « Online ».</span><span class="sxs-lookup"><span data-stu-id="3c685-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="3c685-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="3c685-124">trustedStoreLocation</span></span>|<span data-ttu-id="3c685-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui spécifie le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="3c685-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="3c685-126">La valeur par défaut est « Ordinateur_local ».</span><span class="sxs-lookup"><span data-stu-id="3c685-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="3c685-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="3c685-127">certificateValidator</span></span>|<span data-ttu-id="3c685-128">Un type personnalisé qui dérive de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="3c685-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="3c685-129">Si le `certificateValidationMode` attribut est « Custom », une instance de ce type est utilisée pour la validation de certificat de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="3c685-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c685-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3c685-130">Child Elements</span></span>  
 <span data-ttu-id="3c685-131">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3c685-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c685-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3c685-132">Parent Elements</span></span>  
  
|<span data-ttu-id="3c685-133">Élément</span><span class="sxs-lookup"><span data-stu-id="3c685-133">Element</span></span>|<span data-ttu-id="3c685-134">Description</span><span class="sxs-lookup"><span data-stu-id="3c685-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c685-135">\<add></span><span class="sxs-lookup"><span data-stu-id="3c685-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="3c685-136">Ajoute le Gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="3c685-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3c685-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c685-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
