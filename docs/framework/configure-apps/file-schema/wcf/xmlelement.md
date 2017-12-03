---
title: '&lt;xmlElement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b36eb762de3864eb786d0b7157d316ab071dc2fa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="d0693-102">&lt;xmlElement&gt;</span><span class="sxs-lookup"><span data-stu-id="d0693-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="d0693-103">Spécifie un élément XML qui est envoyé dans le corps du message au service d'émission de jeton de sécurité (STS) lors de la demande d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="d0693-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="d0693-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d0693-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0693-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="d0693-105">\<bindings></span></span>  
<span data-ttu-id="d0693-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="d0693-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="d0693-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="d0693-107">\<binding></span></span>  
<span data-ttu-id="d0693-108">\<sécurité ></span><span class="sxs-lookup"><span data-stu-id="d0693-108">\<security></span></span>  
<span data-ttu-id="d0693-109">\<message ></span><span class="sxs-lookup"><span data-stu-id="d0693-109">\<message></span></span>  
<span data-ttu-id="d0693-110">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="d0693-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0693-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0693-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>  
      <xmlElement xmlElement="String" />  
</tokenRequestParameters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0693-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d0693-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d0693-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d0693-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0693-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="d0693-114">Attributes</span></span>  
  
|<span data-ttu-id="d0693-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="d0693-115">Attribute</span></span>|<span data-ttu-id="d0693-116">Description</span><span class="sxs-lookup"><span data-stu-id="d0693-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0693-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="d0693-117">xmlElement</span></span>|<span data-ttu-id="d0693-118">Chaîne spécifiant un élément XML qui est envoyé dans le corps du message au service d'émission de jeton de sécurité (STS) lors de la demande d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="d0693-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0693-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d0693-119">Child Elements</span></span>  
 <span data-ttu-id="d0693-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d0693-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0693-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d0693-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d0693-122">Élément</span><span class="sxs-lookup"><span data-stu-id="d0693-122">Element</span></span>|<span data-ttu-id="d0693-123">Description</span><span class="sxs-lookup"><span data-stu-id="d0693-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0693-124">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="d0693-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="d0693-125">Collection de paramètres de demande de jeton.</span><span class="sxs-lookup"><span data-stu-id="d0693-125">A collection of token request parameters.</span></span> <span data-ttu-id="d0693-126">Chaque paramètre est un élément XML.</span><span class="sxs-lookup"><span data-stu-id="d0693-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0693-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0693-127">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>  
 [<span data-ttu-id="d0693-128">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="d0693-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="d0693-129">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="d0693-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="d0693-130">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="d0693-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="d0693-131">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="d0693-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="d0693-132">Liaisons</span><span class="sxs-lookup"><span data-stu-id="d0693-132">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
