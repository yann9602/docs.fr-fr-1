---
title: '&lt;DNS&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f2e3dbd0781485336a441c8eacb536ad008ff7a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdnsgt"></a><span data-ttu-id="0c85c-102">&lt;DNS&gt;</span><span class="sxs-lookup"><span data-stu-id="0c85c-102">&lt;dns&gt;</span></span>
<span data-ttu-id="0c85c-103">Spécifie l'identité attendue du serveur.</span><span class="sxs-lookup"><span data-stu-id="0c85c-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="0c85c-104">Cette identité est valide pour le mode d'authentification du certificat X509 si le certificat du serveur contient un DNS avec la même valeur.</span><span class="sxs-lookup"><span data-stu-id="0c85c-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="0c85c-105">Elle est également valide pour le mode d'authentification Windows si le SPN a la même valeur.</span><span class="sxs-lookup"><span data-stu-id="0c85c-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="0c85c-106">Pour plus d’informations sur la définition de la valeur d’élément, consultez [l’identité du Service et l’authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0c85c-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="0c85c-107">\<identité ></span><span class="sxs-lookup"><span data-stu-id="0c85c-107">\<identity></span></span>  
<span data-ttu-id="0c85c-108">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="0c85c-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c85c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c85c-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c85c-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0c85c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0c85c-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0c85c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c85c-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="0c85c-112">Attributes</span></span>  
  
|<span data-ttu-id="0c85c-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="0c85c-113">Attribute</span></span>|<span data-ttu-id="0c85c-114">Description</span><span class="sxs-lookup"><span data-stu-id="0c85c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c85c-115">par défaut</span><span class="sxs-lookup"><span data-stu-id="0c85c-115">value</span></span>|<span data-ttu-id="0c85c-116">Système DNS du certificat.</span><span class="sxs-lookup"><span data-stu-id="0c85c-116">The DNS of the certificate.</span></span> <span data-ttu-id="0c85c-117">Le système DNS est un protocole standard utilisé pour localiser des ordinateurs sur un réseau IP.</span><span class="sxs-lookup"><span data-stu-id="0c85c-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="0c85c-118">Les utilisateurs peuvent se souvenir de noms d’affichage, tel que [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) ou [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), il est plus facile que basée sur le nombre des adresses, telles que 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="0c85c-118">Users can remember display names, such as [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) or [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c85c-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0c85c-119">Child Elements</span></span>  
 <span data-ttu-id="0c85c-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0c85c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c85c-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0c85c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0c85c-122">Élément</span><span class="sxs-lookup"><span data-stu-id="0c85c-122">Element</span></span>|<span data-ttu-id="0c85c-123">Description</span><span class="sxs-lookup"><span data-stu-id="0c85c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c85c-124">\<identité ></span><span class="sxs-lookup"><span data-stu-id="0c85c-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="0c85c-125">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="0c85c-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0c85c-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c85c-126">Example</span></span>  
 <span data-ttu-id="0c85c-127">Le code de configuration suivant spécifie le système DNS d'un certificat X.509 utilisé pour authentifier un serveur.</span><span class="sxs-lookup"><span data-stu-id="0c85c-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c85c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c85c-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="0c85c-129">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="0c85c-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="0c85c-130">\<identité ></span><span class="sxs-lookup"><span data-stu-id="0c85c-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
