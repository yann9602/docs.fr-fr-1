---
title: "&lt;messageSenderAuthentication&gt;, élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20d452a6aa9047032d989d62d6c1121d7edc5ee3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagesenderauthenticationgt-element"></a><span data-ttu-id="bf314-102">&lt;messageSenderAuthentication&gt;, élément</span><span class="sxs-lookup"><span data-stu-id="bf314-102">&lt;messageSenderAuthentication&gt; element</span></span>
<span data-ttu-id="bf314-103">Spécifie les options d'authentification pour les expéditeurs du message du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="bf314-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="bf314-104">Pour plus d’informations sur la programmation d’égal à égal, consultez [mise en réseau pair à pair](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="bf314-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="bf314-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bf314-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="bf314-106">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="bf314-106">\<behaviors></span></span>  
<span data-ttu-id="bf314-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="bf314-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="bf314-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="bf314-108">\<behavior></span></span>  
<span data-ttu-id="bf314-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="bf314-109">\<clientCredentials></span></span>  
<span data-ttu-id="bf314-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="bf314-110">\<peer></span></span>  
<span data-ttu-id="bf314-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="bf314-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf314-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf314-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf314-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bf314-113">Attributes and Elements</span></span>  
 <span data-ttu-id="bf314-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bf314-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf314-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="bf314-115">Attributes</span></span>  
  
|<span data-ttu-id="bf314-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="bf314-116">Attribute</span></span>|<span data-ttu-id="bf314-117">Description</span><span class="sxs-lookup"><span data-stu-id="bf314-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf314-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="bf314-118">customCertificateValidatorType</span></span>|<span data-ttu-id="bf314-119">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="bf314-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="bf314-120">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="bf314-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="bf314-121">certifcateValidationMode</span><span class="sxs-lookup"><span data-stu-id="bf314-121">certifcateValidationMode</span></span>|<span data-ttu-id="bf314-122">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="bf314-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="bf314-123">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="bf314-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|<span data-ttu-id="bf314-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="bf314-124">revocationMode</span></span>|<span data-ttu-id="bf314-125">Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL).</span><span class="sxs-lookup"><span data-stu-id="bf314-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|<span data-ttu-id="bf314-126">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="bf314-126">trustedStoreLocation</span></span>|<span data-ttu-id="bf314-127">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="bf314-127">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="bf314-128">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="bf314-128">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="bf314-129">La validation est exécutée sur le **personnes** stocker dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="bf314-129">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="bf314-130">customCertificateValidatorType, attribut</span><span class="sxs-lookup"><span data-stu-id="bf314-130">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="bf314-131">Valeur</span><span class="sxs-lookup"><span data-stu-id="bf314-131">Value</span></span>|<span data-ttu-id="bf314-132">Description</span><span class="sxs-lookup"><span data-stu-id="bf314-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf314-133">Chaîne</span><span class="sxs-lookup"><span data-stu-id="bf314-133">String</span></span>|<span data-ttu-id="bf314-134">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="bf314-134">Optional.</span></span> <span data-ttu-id="bf314-135">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="bf314-135">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="bf314-136">Au minimum, un espace de noms et un nom de type sont requis.</span><span class="sxs-lookup"><span data-stu-id="bf314-136">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="bf314-137">Les informations facultatives incluent : le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="bf314-137">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="bf314-138">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="bf314-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="bf314-139">Valeur</span><span class="sxs-lookup"><span data-stu-id="bf314-139">Value</span></span>|<span data-ttu-id="bf314-140">Description</span><span class="sxs-lookup"><span data-stu-id="bf314-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf314-141">Énumération</span><span class="sxs-lookup"><span data-stu-id="bf314-141">Enumeration</span></span>|<span data-ttu-id="bf314-142">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="bf314-142">Optional.</span></span> <span data-ttu-id="bf314-143">Une des valeurs suivantes : `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust` et `Custom`.</span><span class="sxs-lookup"><span data-stu-id="bf314-143">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="bf314-144">La valeur par défaut est `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="bf314-144">The default is `ChainTrust`.</span></span> <span data-ttu-id="bf314-145">La valeur par défaut est `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="bf314-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="bf314-146">Pour plus d’informations, consultez [utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="bf314-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="bf314-147">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="bf314-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="bf314-148">Valeur</span><span class="sxs-lookup"><span data-stu-id="bf314-148">Value</span></span>|<span data-ttu-id="bf314-149">Description</span><span class="sxs-lookup"><span data-stu-id="bf314-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf314-150">Énumération</span><span class="sxs-lookup"><span data-stu-id="bf314-150">Enumeration</span></span>|<span data-ttu-id="bf314-151">Une des valeurs suivantes : `NoCheck`, `Online` et `Offline`.</span><span class="sxs-lookup"><span data-stu-id="bf314-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="bf314-152">La valeur par défaut est `Online`.</span><span class="sxs-lookup"><span data-stu-id="bf314-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="bf314-153">Pour plus d’informations, consultez [utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="bf314-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="bf314-154">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="bf314-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="bf314-155">Valeur</span><span class="sxs-lookup"><span data-stu-id="bf314-155">Value</span></span>|<span data-ttu-id="bf314-156">Description</span><span class="sxs-lookup"><span data-stu-id="bf314-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf314-157">Énumération</span><span class="sxs-lookup"><span data-stu-id="bf314-157">Enumeration</span></span>|<span data-ttu-id="bf314-158">Une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="bf314-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="bf314-159">La valeur par défaut est `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="bf314-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="bf314-160">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="bf314-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="bf314-161">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="bf314-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="bf314-162">La valeur par défaut est `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="bf314-162">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf314-163">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bf314-163">Child Elements</span></span>  
 <span data-ttu-id="bf314-164">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bf314-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf314-165">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bf314-165">Parent Elements</span></span>  
  
|<span data-ttu-id="bf314-166">Élément</span><span class="sxs-lookup"><span data-stu-id="bf314-166">Element</span></span>|<span data-ttu-id="bf314-167">Description</span><span class="sxs-lookup"><span data-stu-id="bf314-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf314-168">\<peer></span><span class="sxs-lookup"><span data-stu-id="bf314-168">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="bf314-169">Spécifie une information d'identification utilisée pour authentifier le client auprès d'un service homologue.</span><span class="sxs-lookup"><span data-stu-id="bf314-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf314-170">Notes</span><span class="sxs-lookup"><span data-stu-id="bf314-170">Remarks</span></span>  
 <span data-ttu-id="bf314-171">Cet élément doit être configuré si l'authentification des messages est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="bf314-171">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="bf314-172">Pour les canaux de sortie, chaque message est signé à l’aide du certificat fourni par [ \<certificat >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="bf314-172">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="bf314-173">Avant d'être remis à l'application, tous les messages sont vérifiés par rapport aux informations d'identification de message à l'aide du validateur spécifié par l'attribut `customCertificateValidatorType` de cet élément.</span><span class="sxs-lookup"><span data-stu-id="bf314-173">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="bf314-174">Le validateur peut accepter ou rejeter les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="bf314-174">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf314-175">Exemple</span><span class="sxs-lookup"><span data-stu-id="bf314-175">Example</span></span>  
 <span data-ttu-id="bf314-176">Les jeux de codes suivants affectent le mode de validation de l'expéditeur du message à `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="bf314-176">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
      <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
        <messageSenderAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
       <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf314-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf314-177">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="bf314-178">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="bf314-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="bf314-179">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="bf314-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="bf314-180">Authentification de Message de canal homologue</span><span class="sxs-lookup"><span data-stu-id="bf314-180">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="bf314-181">Authentification personnalisée de canal homologue</span><span class="sxs-lookup"><span data-stu-id="bf314-181">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="bf314-182">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="bf314-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
