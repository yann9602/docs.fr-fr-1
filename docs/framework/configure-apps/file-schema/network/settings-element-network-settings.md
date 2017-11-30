---
title: "&lt;paramètres&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 07f356c0425b071ac320e702a9ba7cd6b9537341
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsettingsgt-element-network-settings"></a><span data-ttu-id="5d083-102">&lt;paramètres&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="5d083-102">&lt;settings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="5d083-103">Configure les options réseau de base pour l’espace de noms <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5d083-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="5d083-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5d083-104">\<configuration></span></span>  
<span data-ttu-id="5d083-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="5d083-105">\<system.net></span></span>  
<span data-ttu-id="5d083-106">\<Paramètres ></span><span class="sxs-lookup"><span data-stu-id="5d083-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d083-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d083-107">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener> … </httpListener>  
  <httpWebRequest> … </httpWebRequest>  
  <ipv6> … </ipv6>  
  <performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
  <socket> … </socket>  
  <webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d083-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5d083-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5d083-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5d083-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d083-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="5d083-110">Attributes</span></span>  
 <span data-ttu-id="5d083-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="5d083-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5d083-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5d083-112">Child Elements</span></span>  
  
|<span data-ttu-id="5d083-113">Élément</span><span class="sxs-lookup"><span data-stu-id="5d083-113">Element</span></span>|<span data-ttu-id="5d083-114">Description</span><span class="sxs-lookup"><span data-stu-id="5d083-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d083-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="5d083-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="5d083-116">Personnalise les paramètres utilisés par la <xref:System.Net.HttpListener> classe.</span><span class="sxs-lookup"><span data-stu-id="5d083-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="5d083-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="5d083-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="5d083-118">Personnalise les paramètres de la demande Web.</span><span class="sxs-lookup"><span data-stu-id="5d083-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="5d083-119">IPv6</span><span class="sxs-lookup"><span data-stu-id="5d083-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="5d083-120">Protocole Internet version 6 (IPv6) permet de prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="5d083-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="5d083-121">\<performanceCounter >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="5d083-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="5d083-122">Active les compteurs de performance réseau.</span><span class="sxs-lookup"><span data-stu-id="5d083-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="5d083-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="5d083-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="5d083-124">Configure les connexions aux ressources réseau.</span><span class="sxs-lookup"><span data-stu-id="5d083-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="5d083-125">Socket</span><span class="sxs-lookup"><span data-stu-id="5d083-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="5d083-126">Spécifie si les opérations de socket utilisent des ports de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5d083-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="5d083-127">\<webProxyScript >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="5d083-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="5d083-128">Configure les caractéristiques du script utilisé pour découvrir les serveurs proxy Web.</span><span class="sxs-lookup"><span data-stu-id="5d083-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d083-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5d083-129">Parent Elements</span></span>  
  
|<span data-ttu-id="5d083-130">Élément</span><span class="sxs-lookup"><span data-stu-id="5d083-130">Element</span></span>|<span data-ttu-id="5d083-131">Description</span><span class="sxs-lookup"><span data-stu-id="5d083-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d083-132">System.NET</span><span class="sxs-lookup"><span data-stu-id="5d083-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="5d083-133">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="5d083-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d083-134">Remarques</span><span class="sxs-lookup"><span data-stu-id="5d083-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5d083-135">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5d083-135">Configuration Files</span></span>  
 <span data-ttu-id="5d083-136">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5d083-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d083-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d083-137">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 [<span data-ttu-id="5d083-138">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="5d083-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
