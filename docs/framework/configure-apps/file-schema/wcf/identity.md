---
title: '&lt;identity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 819bb9dc9817050e45a39331361dd5489692f0b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltidentitygt"></a><span data-ttu-id="c184b-102">&lt;identity&gt;</span><span class="sxs-lookup"><span data-stu-id="c184b-102">&lt;identity&gt;</span></span>
<span data-ttu-id="c184b-103">L'élément d'identité autorise un développeur client à spécifier au moment de la conception l'identité attendue du service.</span><span class="sxs-lookup"><span data-stu-id="c184b-103">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="c184b-104">Dans le processus de négociation entre le client et le service, l'infrastructure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] garantit que l'identité du service attendu correspond aux valeurs de cet élément et peut donc être authentifiée.</span><span class="sxs-lookup"><span data-stu-id="c184b-104">In the handshake process between the client and service, the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="c184b-105">Pour plus d’informations, consultez [l’identité du Service et l’authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c184b-105">For more information, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="c184b-106">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c184b-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="c184b-107">\<client ></span><span class="sxs-lookup"><span data-stu-id="c184b-107">\<client></span></span>  
<span data-ttu-id="c184b-108">\<point de terminaison ></span><span class="sxs-lookup"><span data-stu-id="c184b-108">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c184b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c184b-109">Syntax</span></span>  
  
```xml  
<identity>  
    <certificate encodedValue="String"/>  
    <certificateReference findValue="String"   
       isChainIncluded="Boolean"  
       storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
       storeLocation="LocalMachine/CurrentUser"  
       X509FindType= Enumeration./>  
    <dns value="String"/>  
    <rsa value="String"/>  
    <servicePrincipalName value="String"/>  
    <usePrincipalName value="String"/>  
</identity>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c184b-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c184b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c184b-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c184b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c184b-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="c184b-112">Attributes</span></span>  
 <span data-ttu-id="c184b-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c184b-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c184b-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c184b-114">Child Elements</span></span>  
  
|<span data-ttu-id="c184b-115">Élément</span><span class="sxs-lookup"><span data-stu-id="c184b-115">Element</span></span>|<span data-ttu-id="c184b-116">Description</span><span class="sxs-lookup"><span data-stu-id="c184b-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c184b-117">certificate</span><span class="sxs-lookup"><span data-stu-id="c184b-117">certificate</span></span>|<span data-ttu-id="c184b-118">Spécifie les paramètres d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="c184b-118">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="c184b-119">Cet élément est de type <xref:System.ServiceModel.Configuration.CertificateElement>.</span><span class="sxs-lookup"><span data-stu-id="c184b-119">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="c184b-120">Il contient un `encodedValue` d'attribut qui est une chaîne indiquant la valeur encodée par ce certificat.</span><span class="sxs-lookup"><span data-stu-id="c184b-120">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="c184b-121">certificateReference</span><span class="sxs-lookup"><span data-stu-id="c184b-121">certificateReference</span></span>|<span data-ttu-id="c184b-122">Spécifie les paramètres de validation du certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="c184b-122">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="c184b-123">Cet élément est de type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span><span class="sxs-lookup"><span data-stu-id="c184b-123">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="c184b-124">dns</span><span class="sxs-lookup"><span data-stu-id="c184b-124">dns</span></span>|<span data-ttu-id="c184b-125">Spécifie le système DNS d'un certificat X.509 utilisé pour authentifier un service.</span><span class="sxs-lookup"><span data-stu-id="c184b-125">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="c184b-126">Cet élément contient un attribut `value` qui est une chaîne et qui contient l'identité réelle.</span><span class="sxs-lookup"><span data-stu-id="c184b-126">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="c184b-127">rsa</span><span class="sxs-lookup"><span data-stu-id="c184b-127">rsa</span></span>|<span data-ttu-id="c184b-128">Indique la valeur du champ RSA d'un certificat X.509 utilisée pour authentifier un service au niveau d'un client.</span><span class="sxs-lookup"><span data-stu-id="c184b-128">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="c184b-129">Cet élément contient un attribut `value` qui est une chaîne et qui contient l'identité réelle.</span><span class="sxs-lookup"><span data-stu-id="c184b-129">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="c184b-130">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="c184b-130">servicePrincipalName</span></span>|<span data-ttu-id="c184b-131">Indique le nom SPN correspondant au nom principal utilisé par un client pour identifier de manière unique l'instance d'un service.</span><span class="sxs-lookup"><span data-stu-id="c184b-131">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="c184b-132">Cet élément contient un `value` d'attribut qui est une chaîne contenant le nom principal réel.</span><span class="sxs-lookup"><span data-stu-id="c184b-132">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="c184b-133">Cet élément est de type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="c184b-133">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="c184b-134">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="c184b-134">userPrincipalName</span></span>|<span data-ttu-id="c184b-135">Spécifie une identité UPN correspondant au type de nom de connexion d'un utilisateur sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="c184b-135">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="c184b-136">Le nom d'utilisateur principal se compose du nom d'objet utilisateur utilisé dans Active Directory, suivi par le symbole @, puis, généralement, du domaine DNS parent.</span><span class="sxs-lookup"><span data-stu-id="c184b-136">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="c184b-137">Par exemple, dans l’arborescence de domaine Fabrikam.com peut avoir le nom d’utilisateur principal [ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com).  Cet élément contient un `value` d'attribut qui est une chaîne contenant le nom principal réel.</span><span class="sxs-lookup"><span data-stu-id="c184b-137">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).  This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="c184b-138">Cet élément est de type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="c184b-138">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c184b-139">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c184b-139">Parent Elements</span></span>  
  
|<span data-ttu-id="c184b-140">Élément</span><span class="sxs-lookup"><span data-stu-id="c184b-140">Element</span></span>|<span data-ttu-id="c184b-141">Description</span><span class="sxs-lookup"><span data-stu-id="c184b-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c184b-142">\<personnalisé ></span><span class="sxs-lookup"><span data-stu-id="c184b-142">\<custom></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|<span data-ttu-id="c184b-143">Indique le programme de résolution d'homologue personnalisé pour un netPeerTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="c184b-143">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[<span data-ttu-id="c184b-144">\<point de terminaison ></span><span class="sxs-lookup"><span data-stu-id="c184b-144">\<endpoint></span></span>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)|<span data-ttu-id="c184b-145">Configure différents types de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c184b-145">Configures different types of endpoints.</span></span>|  
|[<span data-ttu-id="c184b-146">\<l’émetteur ></span><span class="sxs-lookup"><span data-stu-id="c184b-146">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="c184b-147">Spécifie le service STS pour le service fédéré.</span><span class="sxs-lookup"><span data-stu-id="c184b-147">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[<span data-ttu-id="c184b-148">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="c184b-148">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="c184b-149">Spécifie le point de terminaison de métadonnées pour le service STS d'un service fédéré.</span><span class="sxs-lookup"><span data-stu-id="c184b-149">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[<span data-ttu-id="c184b-150">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="c184b-150">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="c184b-151">Définit des paramètres correspondant à un jeton émis dans une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c184b-151">Defines parameters for an issued token in a custom binding.</span></span>|  
|[<span data-ttu-id="c184b-152">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="c184b-152">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="c184b-153">Spécifie un service STS local.</span><span class="sxs-lookup"><span data-stu-id="c184b-153">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c184b-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c184b-154">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 [<span data-ttu-id="c184b-155">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="c184b-155">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="c184b-156">Points de terminaison : adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="c184b-156">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
