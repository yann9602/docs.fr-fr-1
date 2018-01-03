---
title: '&lt;met en cache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b9dfa7b2f0952f3f9e224ad51fd4d9c0c263ce04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcachesgt"></a><span data-ttu-id="a0ae6-102">&lt;met en cache&gt;</span><span class="sxs-lookup"><span data-stu-id="a0ae6-102">&lt;caches&gt;</span></span>
<span data-ttu-id="a0ae6-103">Inscrit le met en cache utilisés pour les jetons de session et de la détection de relecture de jetons.</span><span class="sxs-lookup"><span data-stu-id="a0ae6-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="a0ae6-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="a0ae6-104">\<system.identityModel></span></span>  
<span data-ttu-id="a0ae6-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a0ae6-105">\<identityConfiguration></span></span>  
<span data-ttu-id="a0ae6-106">\<met en cache ></span><span class="sxs-lookup"><span data-stu-id="a0ae6-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0ae6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0ae6-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0ae6-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a0ae6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a0ae6-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a0ae6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0ae6-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="a0ae6-110">Attributes</span></span>  
 <span data-ttu-id="a0ae6-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a0ae6-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a0ae6-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a0ae6-112">Child Elements</span></span>  
  
|<span data-ttu-id="a0ae6-113">Élément</span><span class="sxs-lookup"><span data-stu-id="a0ae6-113">Element</span></span>|<span data-ttu-id="a0ae6-114">Description</span><span class="sxs-lookup"><span data-stu-id="a0ae6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0ae6-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="a0ae6-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="a0ae6-116">Inscrit un cache pour les jetons de session avec un service ou d’une collection de gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a0ae6-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="a0ae6-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="a0ae6-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="a0ae6-118">Inscrit un cache de relecture de jetons avec un service ou d’une collection de gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a0ae6-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0ae6-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a0ae6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a0ae6-120">Élément</span><span class="sxs-lookup"><span data-stu-id="a0ae6-120">Element</span></span>|<span data-ttu-id="a0ae6-121">Description</span><span class="sxs-lookup"><span data-stu-id="a0ae6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0ae6-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a0ae6-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="a0ae6-123">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="a0ae6-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="a0ae6-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a0ae6-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="a0ae6-125">Fournit des gestionnaires de jetons de configuration pour une collection de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a0ae6-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0ae6-126">Notes</span><span class="sxs-lookup"><span data-stu-id="a0ae6-126">Remarks</span></span>  
 <span data-ttu-id="a0ae6-127">A `<caches>` élément peut être spécifié au niveau du service sous le `<identityConfiguration>` élément ou sur le niveau de regroupement de gestionnaire de jetons de sécurité sous le `<securityTokenHandlerConfiguration>` élément.</span><span class="sxs-lookup"><span data-stu-id="a0ae6-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="a0ae6-128">Paramètres sur une collection de gestionnaire de jetons remplacent celles spécifiées sur le service.</span><span class="sxs-lookup"><span data-stu-id="a0ae6-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="a0ae6-129">Le `<caches>` élément est représenté par la <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> classe.</span><span class="sxs-lookup"><span data-stu-id="a0ae6-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="a0ae6-130">Les caches configurés sont représentées par la <xref:System.IdentityModel.Configuration.IdentityModelCaches> classe.</span><span class="sxs-lookup"><span data-stu-id="a0ae6-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0ae6-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="a0ae6-131">Example</span></span>  
 <span data-ttu-id="a0ae6-132">Le code XML suivant illustre la configuration d’un cache personnalisé destiné à accueillir des jetons de sécurité de session (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="a0ae6-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="a0ae6-133">La configuration est extraite la `ClaimsAwareWebFarm` exemple.</span><span class="sxs-lookup"><span data-stu-id="a0ae6-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
