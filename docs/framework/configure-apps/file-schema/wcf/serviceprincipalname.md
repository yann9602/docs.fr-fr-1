---
title: '&lt;nom principal de service&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e472c7fcfd57341074489a75f7954be38291523b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="9cdc0-102">&lt;nom principal de service&gt;</span><span class="sxs-lookup"><span data-stu-id="9cdc0-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="9cdc0-103">Spécifie l'identité d'un service par son nom de principal du service (SPN).</span><span class="sxs-lookup"><span data-stu-id="9cdc0-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="9cdc0-104">Pour plus d’informations sur la configuration du SPN, consultez [l’identité du Service et l’authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9cdc0-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="9cdc0-105">\<identité ></span><span class="sxs-lookup"><span data-stu-id="9cdc0-105">\<identity></span></span>  
<span data-ttu-id="9cdc0-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="9cdc0-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cdc0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cdc0-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cdc0-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9cdc0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9cdc0-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9cdc0-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cdc0-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="9cdc0-110">Attributes</span></span>  
  
|<span data-ttu-id="9cdc0-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="9cdc0-111">Attribute</span></span>|<span data-ttu-id="9cdc0-112">Description</span><span class="sxs-lookup"><span data-stu-id="9cdc0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9cdc0-113">par défaut</span><span class="sxs-lookup"><span data-stu-id="9cdc0-113">value</span></span>|<span data-ttu-id="9cdc0-114">Nom SPN par lequel un client identifie de manière unique l'instance d'un service.</span><span class="sxs-lookup"><span data-stu-id="9cdc0-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="9cdc0-115">Si vous installez plusieurs instances d'un service sur les ordinateurs d'une forêt, chaque instance doit posséder son propre SPN.</span><span class="sxs-lookup"><span data-stu-id="9cdc0-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="9cdc0-116">Une instance de service donnée peut posséder plusieurs noms SPN si les clients peuvent utiliser plusieurs noms pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="9cdc0-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9cdc0-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9cdc0-117">Child Elements</span></span>  
 <span data-ttu-id="9cdc0-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9cdc0-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9cdc0-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9cdc0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9cdc0-120">Élément</span><span class="sxs-lookup"><span data-stu-id="9cdc0-120">Element</span></span>|<span data-ttu-id="9cdc0-121">Description</span><span class="sxs-lookup"><span data-stu-id="9cdc0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9cdc0-122">\<identité ></span><span class="sxs-lookup"><span data-stu-id="9cdc0-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="9cdc0-123">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="9cdc0-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cdc0-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="9cdc0-124">Remarks</span></span>  
 <span data-ttu-id="9cdc0-125">Un client [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] sécurisé qui se connecte à un point de terminaison avec cette identité utilise le SPN pour effectuer l'authentification SSPI avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9cdc0-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdc0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9cdc0-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="9cdc0-127">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="9cdc0-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="9cdc0-128">\<identité ></span><span class="sxs-lookup"><span data-stu-id="9cdc0-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
