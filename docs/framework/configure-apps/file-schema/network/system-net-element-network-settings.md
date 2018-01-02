---
title: "&lt;system.Net&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6140a5a66d39cbee3c2a8477dcab88aaa717e745
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemnetgt-element-network-settings"></a><span data-ttu-id="9c59d-102">&lt;system.Net&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="9c59d-102">&lt;system.Net&gt; Element (Network Settings)</span></span>
<span data-ttu-id="9c59d-103">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="9c59d-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="9c59d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9c59d-104">\<configuration></span></span>  
<span data-ttu-id="9c59d-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="9c59d-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c59d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c59d-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c59d-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9c59d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="9c59d-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9c59d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c59d-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="9c59d-109">Attributes</span></span>  
 <span data-ttu-id="9c59d-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9c59d-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9c59d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9c59d-111">Child Elements</span></span>  
  
|<span data-ttu-id="9c59d-112">**Élément**</span><span class="sxs-lookup"><span data-stu-id="9c59d-112">**Element**</span></span>|<span data-ttu-id="9c59d-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="9c59d-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9c59d-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="9c59d-114">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="9c59d-115">Spécifie les modules qui servent à authentifier les demandes Internet.</span><span class="sxs-lookup"><span data-stu-id="9c59d-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="9c59d-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="9c59d-116">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="9c59d-117">Spécifie le nombre maximal de connexions à un hôte Internet.</span><span class="sxs-lookup"><span data-stu-id="9c59d-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="9c59d-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="9c59d-118">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="9c59d-119">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="9c59d-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="9c59d-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="9c59d-120">mailSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="9c59d-121">Configure les options d’envoi du courrier SMTP Simple Mail Transport Protocol ().</span><span class="sxs-lookup"><span data-stu-id="9c59d-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="9c59d-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="9c59d-122">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="9c59d-123">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="9c59d-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="9c59d-124">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9c59d-124">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="9c59d-125">Configure les options réseau de base pour les classes dans le <xref:System.Net> et les espaces de noms enfants.</span><span class="sxs-lookup"><span data-stu-id="9c59d-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="9c59d-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="9c59d-126">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="9c59d-127">Spécifie les modules à utiliser pour demander des informations à partir d’hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="9c59d-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c59d-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9c59d-128">Parent Elements</span></span>  
  
|<span data-ttu-id="9c59d-129">**Élément**</span><span class="sxs-lookup"><span data-stu-id="9c59d-129">**Element**</span></span>|<span data-ttu-id="9c59d-130">**Description**</span><span class="sxs-lookup"><span data-stu-id="9c59d-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9c59d-131">configuration</span><span class="sxs-lookup"><span data-stu-id="9c59d-131">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="9c59d-132">Contient des paramètres pour tous les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="9c59d-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c59d-133">Notes</span><span class="sxs-lookup"><span data-stu-id="9c59d-133">Remarks</span></span>  
 <span data-ttu-id="9c59d-134">Le [ \<system.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) élément contient des paramètres pour les classes dans le <xref:System.Net> et les espaces de noms enfants.</span><span class="sxs-lookup"><span data-stu-id="9c59d-134">The [\<system.net>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="9c59d-135">Ces paramètres configurent les modules d’authentification, gestion des connexions, les paramètres de messagerie, le serveur proxy et les modules de demandes Internet pour recevoir des informations à partir d’hôtes Internet.</span><span class="sxs-lookup"><span data-stu-id="9c59d-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c59d-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c59d-136">Example</span></span>  
 <span data-ttu-id="9c59d-137">L’exemple suivant montre une configuration classique utilisée par <xref:System.Net> classes.</span><span class="sxs-lookup"><span data-stu-id="9c59d-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c59d-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c59d-138">See Also</span></span>  
 [<span data-ttu-id="9c59d-139">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="9c59d-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
