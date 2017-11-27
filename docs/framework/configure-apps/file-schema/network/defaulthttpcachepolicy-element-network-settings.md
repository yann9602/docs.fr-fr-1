---
title: "&lt;defaultHttpCachePolicy&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f2db2fd10ca20209c21c8add71d8ee4f26951ca6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdefaulthttpcachepolicygt-element-network-settings"></a><span data-ttu-id="dd35a-102">&lt;defaultHttpCachePolicy&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="dd35a-102">&lt;defaultHttpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="dd35a-103">Décrit si la mise en cache HTTP est active et décrit la valeur par défaut, la mise en cache de stratégie.</span><span class="sxs-lookup"><span data-stu-id="dd35a-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="dd35a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="dd35a-104">\<configuration></span></span>  
<span data-ttu-id="dd35a-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="dd35a-105">\<system.net></span></span>  
<span data-ttu-id="dd35a-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="dd35a-106">\<requestCaching></span></span>  
<span data-ttu-id="dd35a-107">\<defaultHttpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="dd35a-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd35a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd35a-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd35a-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dd35a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dd35a-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dd35a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd35a-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="dd35a-111">Attributes</span></span>  
  
|<span data-ttu-id="dd35a-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="dd35a-112">Attribute</span></span>|<span data-ttu-id="dd35a-113">Description</span><span class="sxs-lookup"><span data-stu-id="dd35a-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="dd35a-114">Spécifie l’intervalle de temps maximal avant un objet mis en cache est marqué comme étant expirée.</span><span class="sxs-lookup"><span data-stu-id="dd35a-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="dd35a-115">Spécifie la durée maximale postérieure à l’heure de nouveauté calculée avant un objet mis en cache est marqué comme étant expirée.</span><span class="sxs-lookup"><span data-stu-id="dd35a-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="dd35a-116">Spécifie la durée minimale d’un objet mis en cache soit considéré comme nouveau.</span><span class="sxs-lookup"><span data-stu-id="dd35a-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="dd35a-117">Spécifie si la stratégie de mise en cache est automatique, ou si le cache est ignoré.</span><span class="sxs-lookup"><span data-stu-id="dd35a-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="dd35a-118">La valeur par défaut est `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="dd35a-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd35a-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dd35a-119">Child Elements</span></span>  
 <span data-ttu-id="dd35a-120">None</span><span class="sxs-lookup"><span data-stu-id="dd35a-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd35a-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dd35a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="dd35a-122">Élément</span><span class="sxs-lookup"><span data-stu-id="dd35a-122">Element</span></span>|<span data-ttu-id="dd35a-123">Description</span><span class="sxs-lookup"><span data-stu-id="dd35a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd35a-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="dd35a-124">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="dd35a-125">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="dd35a-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd35a-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="dd35a-126">Remarks</span></span>  
 <span data-ttu-id="dd35a-127">La valeur de la `policyLevel` attribut a la valeur `BypassCache` ou `Default`.</span><span class="sxs-lookup"><span data-stu-id="dd35a-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="dd35a-128">Les valeurs pour le `maximumAge`, `maximumStale`, et `minimumFresh` les éléments sont soit un intervalle de temps explicite avec un format de *d*. *hh*:*mm*:*ss* (jours, heures, minutes et secondes), ou l’une des constantes `minValue` ou `maxValue`, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="dd35a-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="dd35a-129">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="dd35a-129">Configuration Files</span></span>  
 <span data-ttu-id="dd35a-130">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="dd35a-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd35a-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd35a-131">Example</span></span>  
 <span data-ttu-id="dd35a-132">L’exemple suivant montre comment spécifier une durée minimale de frais de six heures, une durée maximale de deux jours et une durée maximale obsolète de quatre heures.</span><span class="sxs-lookup"><span data-stu-id="dd35a-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd35a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd35a-133">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="dd35a-134">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="dd35a-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
