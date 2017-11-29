---
title: '&lt;trustedIssuers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 33ef3ca88462595d81d269a92a643b43c9aea025
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lttrustedissuersgt"></a><span data-ttu-id="3e103-102">&lt;trustedIssuers&gt;</span><span class="sxs-lookup"><span data-stu-id="3e103-102">&lt;trustedIssuers&gt;</span></span>
<span data-ttu-id="3e103-103">Configure la liste des certificats d’émetteur de confiance utilisé par le Registre de nom de base de configuration de l’émetteur (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span><span class="sxs-lookup"><span data-stu-id="3e103-103">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="3e103-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="3e103-104">\<system.identityModel></span></span>  
<span data-ttu-id="3e103-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3e103-105">\<identityConfiguration></span></span>  
<span data-ttu-id="3e103-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="3e103-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3e103-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3e103-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="3e103-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="3e103-108">\<issuerNameRegistry></span></span>  
<span data-ttu-id="3e103-109">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="3e103-109">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e103-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e103-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e103-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3e103-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3e103-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3e103-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e103-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="3e103-113">Attributes</span></span>  
 <span data-ttu-id="3e103-114">Aucun</span><span class="sxs-lookup"><span data-stu-id="3e103-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3e103-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3e103-115">Child Elements</span></span>  
  
|<span data-ttu-id="3e103-116">Élément</span><span class="sxs-lookup"><span data-stu-id="3e103-116">Element</span></span>|<span data-ttu-id="3e103-117">Description</span><span class="sxs-lookup"><span data-stu-id="3e103-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="3e103-118">Ajoute un certificat à la collection des émetteurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="3e103-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="3e103-119">Le certificat est spécifié avec la `thumbprint` attribut.</span><span class="sxs-lookup"><span data-stu-id="3e103-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="3e103-120">Cet attribut est obligatoire et doit contenir le formulaire ASN.1 codé de l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="3e103-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="3e103-121">Le `name` attribut est facultatif et peut être utilisé pour spécifier un nom convivial pour le certificat.</span><span class="sxs-lookup"><span data-stu-id="3e103-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="3e103-122">Efface tous les certificats de la collection des émetteurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="3e103-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="3e103-123">Supprime un certificat à partir de la collection des émetteurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="3e103-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="3e103-124">Le certificat est spécifié avec la `thumbprint` attribut.</span><span class="sxs-lookup"><span data-stu-id="3e103-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="3e103-125">Cet attribut est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3e103-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e103-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3e103-126">Parent Elements</span></span>  
  
|<span data-ttu-id="3e103-127">Élément</span><span class="sxs-lookup"><span data-stu-id="3e103-127">Element</span></span>|<span data-ttu-id="3e103-128">Description</span><span class="sxs-lookup"><span data-stu-id="3e103-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e103-129">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="3e103-129">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="3e103-130">Configure le Registre de nom de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="3e103-130">Configures the issuer name registry.</span></span> <span data-ttu-id="3e103-131">**Important :** le `type` attribut de la `<issuerNameRegistry>` élément doit faire référence à la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> de classes pour la `<trustedIssuers>` élément soit valide.</span><span class="sxs-lookup"><span data-stu-id="3e103-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e103-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="3e103-132">Remarks</span></span>  
 <span data-ttu-id="3e103-133">Windows Identity Foundation (WIF) fournit une implémentation unique de la <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe prêtes à l’emploi, la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="3e103-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="3e103-134">Le Registre de nom d’émetteur configuration gère une liste d’émetteurs approuvés qui est chargée à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="3e103-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="3e103-135">La liste associe chaque nom de l’émetteur du certificat X.509 qui est nécessaire pour vérifier la signature de jetons généré par l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="3e103-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="3e103-136">La liste de certificats de confiance de l’émetteur est spécifiée sous la `<trustedIssuers>` élément.</span><span class="sxs-lookup"><span data-stu-id="3e103-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="3e103-137">Chaque élément dans la liste associe un nom mnémonique de l’émetteur du certificat X.509 qui est nécessaire pour vérifier la signature des jetons générés par cet émetteur.</span><span class="sxs-lookup"><span data-stu-id="3e103-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="3e103-138">Certificats de confiance sont spécifiés à l’aide de la ASN.1 forme encodée de l’empreinte numérique du certificat et sont ajoutés de la collection à l’aide de `<add>` élément.</span><span class="sxs-lookup"><span data-stu-id="3e103-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="3e103-139">Vous pouvez effacer ou supprimer des émetteurs (certificats) dans la liste à l’aide de la `<clear>` et `<remove>` éléments.</span><span class="sxs-lookup"><span data-stu-id="3e103-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="3e103-140">Le `type` attribut de la `<issuerNameRegistry>` élément doit faire référence à la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> de classes pour la `<trustedIssuers>` élément soit valide.</span><span class="sxs-lookup"><span data-stu-id="3e103-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e103-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="3e103-141">Example</span></span>  
 <span data-ttu-id="3e103-142">Le code XML suivant montre comment spécifier l’émetteur de la configuration en fonction du Registre des noms.</span><span class="sxs-lookup"><span data-stu-id="3e103-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e103-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e103-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
