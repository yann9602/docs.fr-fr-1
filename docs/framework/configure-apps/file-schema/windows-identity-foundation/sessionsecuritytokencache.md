---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: a1d1af398073e15ce7f73b3359366df9e5629ac6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="74d04-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="74d04-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="74d04-103">Inscrit un cache pour les jetons de session avec un service ou d’une collection de gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="74d04-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="74d04-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="74d04-104">\<system.identityModel></span></span>  
<span data-ttu-id="74d04-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="74d04-105">\<identityConfiguration></span></span>  
<span data-ttu-id="74d04-106">\<met en cache ></span><span class="sxs-lookup"><span data-stu-id="74d04-106">\<caches></span></span>  
<span data-ttu-id="74d04-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="74d04-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74d04-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74d04-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74d04-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="74d04-109">Attributes and Elements</span></span>  
 <span data-ttu-id="74d04-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="74d04-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74d04-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="74d04-111">Attributes</span></span>  
  
|<span data-ttu-id="74d04-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="74d04-112">Attribute</span></span>|<span data-ttu-id="74d04-113">Description</span><span class="sxs-lookup"><span data-stu-id="74d04-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74d04-114">type</span><span class="sxs-lookup"><span data-stu-id="74d04-114">type</span></span>|<span data-ttu-id="74d04-115">Un type qui dérive de la <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe.</span><span class="sxs-lookup"><span data-stu-id="74d04-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74d04-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="74d04-116">Child Elements</span></span>  
 <span data-ttu-id="74d04-117">None</span><span class="sxs-lookup"><span data-stu-id="74d04-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74d04-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="74d04-118">Parent Elements</span></span>  
  
|<span data-ttu-id="74d04-119">Élément</span><span class="sxs-lookup"><span data-stu-id="74d04-119">Element</span></span>|<span data-ttu-id="74d04-120">Description</span><span class="sxs-lookup"><span data-stu-id="74d04-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74d04-121">\<met en cache ></span><span class="sxs-lookup"><span data-stu-id="74d04-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="74d04-122">Inscrit le met en cache utilisé par un service ou une collection de gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="74d04-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="74d04-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="74d04-123">Example</span></span>  
 <span data-ttu-id="74d04-124">Le code XML suivant illustre la configuration d’un cache personnalisé destiné à accueillir des jetons de sécurité de session (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="74d04-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="74d04-125">La configuration est extraite la `ClaimsAwareWebFarm` exemple.</span><span class="sxs-lookup"><span data-stu-id="74d04-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="74d04-126">Pour plus d’informations sur cet exemple, consultez [exemple d’Index de Code WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="74d04-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74d04-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74d04-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
