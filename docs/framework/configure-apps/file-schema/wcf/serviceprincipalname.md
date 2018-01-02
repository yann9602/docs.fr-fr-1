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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f9b4ec506097cf010af78b3504def08102e0774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="5c112-102">&lt;nom principal de service&gt;</span><span class="sxs-lookup"><span data-stu-id="5c112-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="5c112-103">Spécifie l'identité d'un service par son nom de principal du service (SPN).</span><span class="sxs-lookup"><span data-stu-id="5c112-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="5c112-104">Pour plus d’informations sur la configuration du SPN, consultez [l’identité du Service et l’authentification](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5c112-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="5c112-105">\<identité ></span><span class="sxs-lookup"><span data-stu-id="5c112-105">\<identity></span></span>  
<span data-ttu-id="5c112-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="5c112-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c112-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c112-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c112-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5c112-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5c112-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5c112-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c112-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="5c112-110">Attributes</span></span>  
  
|<span data-ttu-id="5c112-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="5c112-111">Attribute</span></span>|<span data-ttu-id="5c112-112">Description</span><span class="sxs-lookup"><span data-stu-id="5c112-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c112-113">par défaut</span><span class="sxs-lookup"><span data-stu-id="5c112-113">value</span></span>|<span data-ttu-id="5c112-114">Nom SPN par lequel un client identifie de manière unique l'instance d'un service.</span><span class="sxs-lookup"><span data-stu-id="5c112-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="5c112-115">Si vous installez plusieurs instances d'un service sur les ordinateurs d'une forêt, chaque instance doit posséder son propre SPN.</span><span class="sxs-lookup"><span data-stu-id="5c112-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="5c112-116">Une instance de service donnée peut posséder plusieurs noms SPN si les clients peuvent utiliser plusieurs noms pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="5c112-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c112-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5c112-117">Child Elements</span></span>  
 <span data-ttu-id="5c112-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5c112-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c112-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5c112-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5c112-120">Élément</span><span class="sxs-lookup"><span data-stu-id="5c112-120">Element</span></span>|<span data-ttu-id="5c112-121">Description</span><span class="sxs-lookup"><span data-stu-id="5c112-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c112-122">\<identité ></span><span class="sxs-lookup"><span data-stu-id="5c112-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="5c112-123">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="5c112-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c112-124">Notes</span><span class="sxs-lookup"><span data-stu-id="5c112-124">Remarks</span></span>  
 <span data-ttu-id="5c112-125">Un client [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] sécurisé qui se connecte à un point de terminaison avec cette identité utilise le SPN pour effectuer l'authentification SSPI avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5c112-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c112-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c112-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="5c112-127">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="5c112-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="5c112-128">\<identité ></span><span class="sxs-lookup"><span data-stu-id="5c112-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
