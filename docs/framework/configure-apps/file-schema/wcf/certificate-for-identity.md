---
title: '&lt;certificate&gt; de &lt;identity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a9eabd25712136ef98f452cc15470bce1893527e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcertificategt-for-ltidentitygt"></a><span data-ttu-id="2a7d2-102">&lt;certificate&gt; de &lt;identity&gt;</span><span class="sxs-lookup"><span data-stu-id="2a7d2-102">&lt;certificate&gt; for &lt;identity&gt;</span></span>
<span data-ttu-id="2a7d2-103">Spécifie un certificat X.509 utilisé pour valider un serveur auprès d'un client.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="2a7d2-104">Pour plus d’informations sur la définition de la valeur d’élément, consultez [l’identité du Service et l’authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2a7d2-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="2a7d2-105">\<identité ></span><span class="sxs-lookup"><span data-stu-id="2a7d2-105">\<identity></span></span>  
<span data-ttu-id="2a7d2-106">\<certificat ></span><span class="sxs-lookup"><span data-stu-id="2a7d2-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a7d2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a7d2-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a7d2-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2a7d2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2a7d2-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a7d2-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="2a7d2-110">Attributes</span></span>  
  
|<span data-ttu-id="2a7d2-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="2a7d2-111">Attribute</span></span>|<span data-ttu-id="2a7d2-112">Description</span><span class="sxs-lookup"><span data-stu-id="2a7d2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a7d2-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="2a7d2-113">encodedValue</span></span>|<span data-ttu-id="2a7d2-114">Encodage Base64 du certificat.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a7d2-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2a7d2-115">Child Elements</span></span>  
 <span data-ttu-id="2a7d2-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a7d2-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2a7d2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2a7d2-118">Élément</span><span class="sxs-lookup"><span data-stu-id="2a7d2-118">Element</span></span>|<span data-ttu-id="2a7d2-119">Description</span><span class="sxs-lookup"><span data-stu-id="2a7d2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a7d2-120">\<identité ></span><span class="sxs-lookup"><span data-stu-id="2a7d2-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="2a7d2-121">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2a7d2-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="2a7d2-122">Example</span></span>  
 <span data-ttu-id="2a7d2-123">Le code suivant spécifie la représentation encodée d'un certificat qui est utilisée pour valider un serveur auprès d'un client.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>  
  <certificate encodedValue = " MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a7d2-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a7d2-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.EndpointIdentity>  
 [<span data-ttu-id="2a7d2-125">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="2a7d2-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="2a7d2-126">\<identité ></span><span class="sxs-lookup"><span data-stu-id="2a7d2-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
