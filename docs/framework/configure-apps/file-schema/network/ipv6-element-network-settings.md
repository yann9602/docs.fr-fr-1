---
title: "&lt;IPv6&gt; , élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4a98d1d21d7df4e88c668262e60397029fe44c5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltipv6gt-element-network-settings"></a><span data-ttu-id="d1193-102">&lt;IPv6&gt; , élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="d1193-102">&lt;ipv6&gt; Element (Network Settings)</span></span>
<span data-ttu-id="d1193-103">Protocole Internet version 6 (IPv6) permet de réponses à partir des membres obsolètes de la <xref:System.Net.Dns> classe.</span><span class="sxs-lookup"><span data-stu-id="d1193-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="d1193-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d1193-104">\<configuration></span></span>  
<span data-ttu-id="d1193-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="d1193-105">\<system.net></span></span>  
<span data-ttu-id="d1193-106">\<Paramètres ></span><span class="sxs-lookup"><span data-stu-id="d1193-106">\<settings></span></span>  
<span data-ttu-id="d1193-107">\<IPv6 ></span><span class="sxs-lookup"><span data-stu-id="d1193-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1193-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1193-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1193-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d1193-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d1193-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d1193-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1193-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="d1193-111">Attributes</span></span>  
  
|<span data-ttu-id="d1193-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="d1193-112">**Attribute**</span></span>|<span data-ttu-id="d1193-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="d1193-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="d1193-114">Spécifie si les membres de la <xref:System.Net.Dns> classe retourner protocole Internet version 6 (IPv6) adresses.</span><span class="sxs-lookup"><span data-stu-id="d1193-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="d1193-115">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="d1193-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1193-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d1193-116">Child Elements</span></span>  
 <span data-ttu-id="d1193-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d1193-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1193-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d1193-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d1193-119">**Élément**</span><span class="sxs-lookup"><span data-stu-id="d1193-119">**Element**</span></span>|<span data-ttu-id="d1193-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="d1193-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d1193-121">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d1193-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="d1193-122">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="d1193-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1193-123">Notes</span><span class="sxs-lookup"><span data-stu-id="d1193-123">Remarks</span></span>  
 <span data-ttu-id="d1193-124">Ce paramètre permet la prise en charge IPv6 pour les membres obsolètes de la <xref:System.Net.Dns> classe : <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, et <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="d1193-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="d1193-125">Pour les autres membres de le <xref:System.Net?displayProperty=nameWithType> espace de noms, les adresses IPv6 peuvent être retournées si IPv6 est activé dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="d1193-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d1193-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="d1193-126">Configuration Files</span></span>  
 <span data-ttu-id="d1193-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d1193-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1193-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="d1193-128">Example</span></span>  
 <span data-ttu-id="d1193-129">L’exemple suivant montre comment activer la prise en charge IPv6 pour la <xref:System.Net.Dns> classe.</span><span class="sxs-lookup"><span data-stu-id="d1193-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1193-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1193-130">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Dns?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="d1193-131">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="d1193-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
