---
title: "&lt;defaultFtpCachePolicy&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0c62be73db6d9d0b6ce67dd87021c589502d5fec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a><span data-ttu-id="3a691-102">&lt;defaultFtpCachePolicy&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="3a691-102">&lt;defaultFtpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="3a691-103">Décrit si la mise en cache FTP est active et décrit la valeur par défaut, la mise en cache de stratégie.</span><span class="sxs-lookup"><span data-stu-id="3a691-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="3a691-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3a691-104">\<configuration></span></span>  
<span data-ttu-id="3a691-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="3a691-105">\<system.net></span></span>  
<span data-ttu-id="3a691-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="3a691-106">\<requestCaching></span></span>  
<span data-ttu-id="3a691-107">\<defaultFtpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="3a691-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a691-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a691-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a691-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3a691-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3a691-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3a691-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a691-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="3a691-111">Attributes</span></span>  
  
|<span data-ttu-id="3a691-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="3a691-112">Attribute</span></span>|<span data-ttu-id="3a691-113">Description</span><span class="sxs-lookup"><span data-stu-id="3a691-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="3a691-114">Spécifie la mise en cache de stratégie FTP.</span><span class="sxs-lookup"><span data-stu-id="3a691-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="3a691-115">La valeur par défaut est `Default`.</span><span class="sxs-lookup"><span data-stu-id="3a691-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="3a691-116">PolicyLevel qui n’est attribut</span><span class="sxs-lookup"><span data-stu-id="3a691-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="3a691-117">Value</span><span class="sxs-lookup"><span data-stu-id="3a691-117">Value</span></span>|<span data-ttu-id="3a691-118">Description</span><span class="sxs-lookup"><span data-stu-id="3a691-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="3a691-119">Retourne la ressource mise en cache si la ressource est actualisée, la longueur du contenu est précise et d’expiration, modification et les attributs de la longueur de contenu sont présents.</span><span class="sxs-lookup"><span data-stu-id="3a691-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="3a691-120">Retourne la ressource à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="3a691-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="3a691-121">Retourne la ressource mise en cache si la longueur du contenu est présente et qu’il correspond à la taille de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="3a691-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="3a691-122">Retourne la ressource mise en cache si la longueur du contenu est fournie et correspond à la taille de l’entrée ; Sinon, la ressource est téléchargée à partir du serveur et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="3a691-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="3a691-123">Retourne la ressource mise en cache si l’horodatage de la ressource mise en cache est identique à celui de la ressource sur le serveur ; Sinon, la ressource est téléchargée à partir du serveur, stockée dans le cache et retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="3a691-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="3a691-124">Télécharge la ressource à partir du serveur, il stocke dans le cache et retourne la ressource à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="3a691-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="3a691-125">Si une ressource mise en cache existe, elle est supprimée.</span><span class="sxs-lookup"><span data-stu-id="3a691-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="3a691-126">La ressource est téléchargée à partir du serveur et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="3a691-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="3a691-127">Satisfait une demande à l’aide de la copie mise en cache de la ressource si l’horodatage est le même que l’horodatage de la ressource sur le serveur ; Sinon, la ressource est téléchargée à partir du serveur, présentée à l’appelant et stockée dans le cache.</span><span class="sxs-lookup"><span data-stu-id="3a691-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a691-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3a691-128">Child Elements</span></span>  
 <span data-ttu-id="3a691-129">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3a691-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a691-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3a691-130">Parent Elements</span></span>  
  
|<span data-ttu-id="3a691-131">Élément</span><span class="sxs-lookup"><span data-stu-id="3a691-131">Element</span></span>|<span data-ttu-id="3a691-132">Description</span><span class="sxs-lookup"><span data-stu-id="3a691-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a691-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="3a691-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="3a691-134">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="3a691-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a691-135">Notes</span><span class="sxs-lookup"><span data-stu-id="3a691-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a691-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="3a691-136">Example</span></span>  
 <span data-ttu-id="3a691-137">L’exemple suivant montre comment spécifier une stratégie de la mise en cache de FTP `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="3a691-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a691-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a691-138">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="3a691-139">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="3a691-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
