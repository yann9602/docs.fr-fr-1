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
ms.openlocfilehash: 6b9a5fb2f62c27d278570ad789deab30917bc432
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a><span data-ttu-id="6211f-102">&lt;defaultFtpCachePolicy&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6211f-102">&lt;defaultFtpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="6211f-103">Décrit si la mise en cache FTP est active et décrit la valeur par défaut, la mise en cache de stratégie.</span><span class="sxs-lookup"><span data-stu-id="6211f-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="6211f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6211f-104">\<configuration></span></span>  
<span data-ttu-id="6211f-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="6211f-105">\<system.net></span></span>  
<span data-ttu-id="6211f-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="6211f-106">\<requestCaching></span></span>  
<span data-ttu-id="6211f-107">\<defaultFtpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="6211f-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6211f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6211f-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6211f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6211f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6211f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6211f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6211f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="6211f-111">Attributes</span></span>  
  
|<span data-ttu-id="6211f-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="6211f-112">Attribute</span></span>|<span data-ttu-id="6211f-113">Description</span><span class="sxs-lookup"><span data-stu-id="6211f-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="6211f-114">Spécifie la mise en cache de stratégie FTP.</span><span class="sxs-lookup"><span data-stu-id="6211f-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="6211f-115">La valeur par défaut est `Default`.</span><span class="sxs-lookup"><span data-stu-id="6211f-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="6211f-116">PolicyLevel qui n’est attribut</span><span class="sxs-lookup"><span data-stu-id="6211f-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="6211f-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="6211f-117">Value</span></span>|<span data-ttu-id="6211f-118">Description</span><span class="sxs-lookup"><span data-stu-id="6211f-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="6211f-119">Retourne la ressource mise en cache si la ressource est actualisée, la longueur du contenu est précise et d’expiration, modification et les attributs de la longueur de contenu sont présents.</span><span class="sxs-lookup"><span data-stu-id="6211f-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="6211f-120">Retourne la ressource à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="6211f-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="6211f-121">Retourne la ressource mise en cache si la longueur du contenu est présente et qu’il correspond à la taille de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="6211f-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="6211f-122">Retourne la ressource mise en cache si la longueur du contenu est fournie et correspond à la taille de l’entrée ; Sinon, la ressource est téléchargée à partir du serveur et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="6211f-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="6211f-123">Retourne la ressource mise en cache si l’horodatage de la ressource mise en cache est identique à celui de la ressource sur le serveur ; Sinon, la ressource est téléchargée à partir du serveur, stockée dans le cache et retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="6211f-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="6211f-124">Télécharge la ressource à partir du serveur, il stocke dans le cache et retourne la ressource à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="6211f-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="6211f-125">Si une ressource mise en cache existe, elle est supprimée.</span><span class="sxs-lookup"><span data-stu-id="6211f-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="6211f-126">La ressource est téléchargée à partir du serveur et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="6211f-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="6211f-127">Satisfait une demande à l’aide de la copie mise en cache de la ressource si l’horodatage est le même que l’horodatage de la ressource sur le serveur ; Sinon, la ressource est téléchargée à partir du serveur, présentée à l’appelant et stockée dans le cache.</span><span class="sxs-lookup"><span data-stu-id="6211f-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6211f-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6211f-128">Child Elements</span></span>  
 <span data-ttu-id="6211f-129">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6211f-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6211f-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6211f-130">Parent Elements</span></span>  
  
|<span data-ttu-id="6211f-131">Élément</span><span class="sxs-lookup"><span data-stu-id="6211f-131">Element</span></span>|<span data-ttu-id="6211f-132">Description</span><span class="sxs-lookup"><span data-stu-id="6211f-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6211f-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="6211f-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="6211f-134">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="6211f-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6211f-135">Remarques</span><span class="sxs-lookup"><span data-stu-id="6211f-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="6211f-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="6211f-136">Example</span></span>  
 <span data-ttu-id="6211f-137">L’exemple suivant montre comment spécifier une stratégie de la mise en cache de FTP `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="6211f-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6211f-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6211f-138">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="6211f-139">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="6211f-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
