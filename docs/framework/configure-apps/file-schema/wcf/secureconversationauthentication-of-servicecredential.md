---
title: '&lt;secureConversationAuthentication&gt; de &lt;serviceCredential&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f80b0570055edbe15fa467ea83e11aba2b62a8fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="68126-102">&lt;secureConversationAuthentication&gt; de &lt;serviceCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="68126-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="68126-103">Spécifie les paramètres pour un service de conversation sécurisé.</span><span class="sxs-lookup"><span data-stu-id="68126-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="68126-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="68126-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="68126-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="68126-105">\<behaviors></span></span>  
<span data-ttu-id="68126-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="68126-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="68126-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="68126-107">\<behavior></span></span>  
<span data-ttu-id="68126-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="68126-108">\<serviceCredentials></span></span>  
<span data-ttu-id="68126-109">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="68126-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68126-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68126-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68126-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="68126-111">Attributes and Elements</span></span>  
 <span data-ttu-id="68126-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="68126-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68126-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="68126-113">Attributes</span></span>  
  
|<span data-ttu-id="68126-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="68126-114">Attribute</span></span>|<span data-ttu-id="68126-115">Description</span><span class="sxs-lookup"><span data-stu-id="68126-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="68126-116">Chaîne qui spécifie le type de <xref:System.ServiceModel.Security.SecurityStateEncoder> à utiliser.</span><span class="sxs-lookup"><span data-stu-id="68126-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68126-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="68126-117">Child Elements</span></span>  
 <span data-ttu-id="68126-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="68126-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68126-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="68126-119">Parent Elements</span></span>  
  
|<span data-ttu-id="68126-120">Élément</span><span class="sxs-lookup"><span data-stu-id="68126-120">Element</span></span>|<span data-ttu-id="68126-121">Description</span><span class="sxs-lookup"><span data-stu-id="68126-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68126-122">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="68126-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="68126-123">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="68126-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68126-124">Notes</span><span class="sxs-lookup"><span data-stu-id="68126-124">Remarks</span></span>  
 <span data-ttu-id="68126-125">Utilisez cet élément de configuration pour spécifier la liste des types de revendication connus pour la sérialisation des cookies SCT (Security Context Token), ainsi qu'un encodeur pour encoder et sécuriser les informations de cookies.</span><span class="sxs-lookup"><span data-stu-id="68126-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="68126-126">Pour plus d'informations sur SCT, consultez <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="68126-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68126-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68126-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
