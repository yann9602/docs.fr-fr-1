---
title: '&lt;RSA&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 714036b6f7cb64fd12cd48eabb4203279431e5a6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltrsagt"></a><span data-ttu-id="2e131-102">&lt;RSA&gt;</span><span class="sxs-lookup"><span data-stu-id="2e131-102">&lt;rsa&gt;</span></span>
<span data-ttu-id="2e131-103">Un client WCF sécurisé qui se connecte à un point de terminaison avec cette identité vérifie que les revendications présentées par le serveur contiennent une revendication intégrant la clé publique RSA utilisée pour construire cette identité.</span><span class="sxs-lookup"><span data-stu-id="2e131-103">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="2e131-104">\<identité ></span><span class="sxs-lookup"><span data-stu-id="2e131-104">\<identity></span></span>  
<span data-ttu-id="2e131-105">\<RSA ></span><span class="sxs-lookup"><span data-stu-id="2e131-105">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e131-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e131-106">Syntax</span></span>  
  
```xml  
<rsa value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e131-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2e131-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2e131-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2e131-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e131-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="2e131-109">Attributes</span></span>  
  
|<span data-ttu-id="2e131-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="2e131-110">Attribute</span></span>|<span data-ttu-id="2e131-111">Description</span><span class="sxs-lookup"><span data-stu-id="2e131-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2e131-112">par défaut</span><span class="sxs-lookup"><span data-stu-id="2e131-112">value</span></span>|<span data-ttu-id="2e131-113">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="2e131-113">Optional String.</span></span> <span data-ttu-id="2e131-114">Valeur de clé publique RSA à comparer sur le client.</span><span class="sxs-lookup"><span data-stu-id="2e131-114">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e131-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2e131-115">Child Elements</span></span>  
 <span data-ttu-id="2e131-116">None</span><span class="sxs-lookup"><span data-stu-id="2e131-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2e131-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2e131-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2e131-118">Élément</span><span class="sxs-lookup"><span data-stu-id="2e131-118">Element</span></span>|<span data-ttu-id="2e131-119">Description</span><span class="sxs-lookup"><span data-stu-id="2e131-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e131-120">\<identité ></span><span class="sxs-lookup"><span data-stu-id="2e131-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="2e131-121">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="2e131-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e131-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="2e131-122">Remarks</span></span>  
 <span data-ttu-id="2e131-123">Un contrôle RSA vous permet de limiter l'authentification à un seul certificat basé sur sa clé RSA ou de générer votre propre valeur de clé RSA.</span><span class="sxs-lookup"><span data-stu-id="2e131-123">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="2e131-124">Cette opération active une authentification plus stricte d'une clé RSA spécifique aux dépens du service, qui n'utilise plus les clients existants lorsque la valeur de clé RSA est modifiée.</span><span class="sxs-lookup"><span data-stu-id="2e131-124">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="2e131-125">Pour plus d’informations sur l’utilisation d’identité pour valider un service à un client, consultez [l’identité du Service et l’authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2e131-125">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e131-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="2e131-126">Example</span></span>  
 <span data-ttu-id="2e131-127">Le code de configuration suivant spécifie la valeur de clé publique d'un certificat X.509 utilisé pour authentifier un serveur.</span><span class="sxs-lookup"><span data-stu-id="2e131-127">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <rsa value = "0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"/>  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e131-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e131-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.RsaEndpointIdentity>  
 [<span data-ttu-id="2e131-129">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="2e131-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="2e131-130">\<identité ></span><span class="sxs-lookup"><span data-stu-id="2e131-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
