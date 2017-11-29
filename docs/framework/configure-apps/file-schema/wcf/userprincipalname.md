---
title: '&lt;userPrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b93a0cc24953024e265df418ec6dd738598dd0f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="b86e1-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="b86e1-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="b86e1-103">Indique le nom d'utilisateur principal (UPN) d'un service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="b86e1-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="b86e1-104">Pour plus d’informations sur la définition de l’UPN, consultez [l’identité du Service et l’authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b86e1-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="b86e1-105">\<identité ></span><span class="sxs-lookup"><span data-stu-id="b86e1-105">\<identity></span></span>  
<span data-ttu-id="b86e1-106">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="b86e1-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b86e1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b86e1-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b86e1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b86e1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b86e1-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b86e1-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b86e1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b86e1-110">Attributes</span></span>  
  
|<span data-ttu-id="b86e1-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="b86e1-111">Attribute</span></span>|<span data-ttu-id="b86e1-112">Description</span><span class="sxs-lookup"><span data-stu-id="b86e1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b86e1-113">par défaut</span><span class="sxs-lookup"><span data-stu-id="b86e1-113">value</span></span>|<span data-ttu-id="b86e1-114">Nom de compte d'utilisateur (parfois connu sous le nom de connexion d'utilisateur) et nom de domaine identifiant le domaine dans lequel se trouve le compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b86e1-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="b86e1-115">Il s'agit de la méthode de connexion standard à un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="b86e1-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="b86e1-116">Le format est : someone@example.com (comme pour une adresse de messagerie).</span><span class="sxs-lookup"><span data-stu-id="b86e1-116">The format is: someone@example.com (as for an e-mail address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b86e1-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b86e1-117">Child Elements</span></span>  
 <span data-ttu-id="b86e1-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b86e1-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b86e1-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b86e1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b86e1-120">Élément</span><span class="sxs-lookup"><span data-stu-id="b86e1-120">Element</span></span>|<span data-ttu-id="b86e1-121">Description</span><span class="sxs-lookup"><span data-stu-id="b86e1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b86e1-122">\<identité ></span><span class="sxs-lookup"><span data-stu-id="b86e1-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="b86e1-123">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="b86e1-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b86e1-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="b86e1-124">Remarks</span></span>  
 <span data-ttu-id="b86e1-125">Un client [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] sécurisé qui se connecte à un point de terminaison avec cette identité utilise l'UPN pour effectuer l'authentification SSPI avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b86e1-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b86e1-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="b86e1-126">Example</span></span>  
 <span data-ttu-id="b86e1-127">Le code de configuration suivant indique le nom UPN du service devant être authentifié par le client.</span><span class="sxs-lookup"><span data-stu-id="b86e1-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b86e1-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b86e1-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="b86e1-129">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="b86e1-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b86e1-130">\<identité ></span><span class="sxs-lookup"><span data-stu-id="b86e1-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
