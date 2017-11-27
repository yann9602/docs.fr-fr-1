---
title: "&lt;proxy&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7178527f369c698b0ab53aa41cb28dd0126436b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltproxygt-element-network-settings"></a><span data-ttu-id="e4d34-102">&lt;proxy&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="e4d34-102">&lt;proxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="e4d34-103">Définit un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="e4d34-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="e4d34-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e4d34-104">\<configuration></span></span>  
<span data-ttu-id="e4d34-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="e4d34-105">\<system.net></span></span>  
<span data-ttu-id="e4d34-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="e4d34-106">\<defaultProxy></span></span>  
<span data-ttu-id="e4d34-107">\<proxy ></span><span class="sxs-lookup"><span data-stu-id="e4d34-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4d34-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4d34-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4d34-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e4d34-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e4d34-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e4d34-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4d34-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e4d34-111">Attributes</span></span>  
  
|<span data-ttu-id="e4d34-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="e4d34-112">**Attribute**</span></span>|<span data-ttu-id="e4d34-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="e4d34-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="e4d34-114">Spécifie si le proxy est détecté automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e4d34-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="e4d34-115">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="e4d34-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="e4d34-116">Spécifie si le proxy est contourné pour les ressources locales.</span><span class="sxs-lookup"><span data-stu-id="e4d34-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="e4d34-117">Les ressources locales incluent le serveur local (http://localhost, http://loopback ou http://127.0.0.1) et un URI sans point (http://webserver).</span><span class="sxs-lookup"><span data-stu-id="e4d34-117">Local resources include the local server (http://localhost, http://loopback, or http://127.0.0.1) and a URI without a period (http://webserver).</span></span> <span data-ttu-id="e4d34-118">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="e4d34-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="e4d34-119">Spécifie l’URI de proxy à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e4d34-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="e4d34-120">Spécifie l’emplacement du script de configuration.</span><span class="sxs-lookup"><span data-stu-id="e4d34-120">Specifies the location of the configuration script.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="e4d34-121">Spécifie s’il faut utiliser les paramètres de proxy Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e4d34-121">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="e4d34-122">Si la valeur `true`, les attributs suivants remplacent les paramètres de proxy Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e4d34-122">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="e4d34-123">La valeur par défaut est `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="e4d34-123">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4d34-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e4d34-124">Child Elements</span></span>  
 <span data-ttu-id="e4d34-125">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e4d34-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4d34-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e4d34-126">Parent Elements</span></span>  
  
|<span data-ttu-id="e4d34-127">**Élément**</span><span class="sxs-lookup"><span data-stu-id="e4d34-127">**Element**</span></span>|<span data-ttu-id="e4d34-128">**Description**</span><span class="sxs-lookup"><span data-stu-id="e4d34-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e4d34-129">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="e4d34-129">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="e4d34-130">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="e4d34-130">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="e4d34-131">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="e4d34-131">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4d34-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="e4d34-132">Remarks</span></span>  
 <span data-ttu-id="e4d34-133">Le `proxy` élément définit un serveur proxy pour une application.</span><span class="sxs-lookup"><span data-stu-id="e4d34-133">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="e4d34-134">Si cet élément est manquant dans le fichier de configuration, le .NET Framework utilise les paramètres de proxy dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e4d34-134">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="e4d34-135">La valeur de la `proxyaddress` attribut doit être un bien formé URI Uniform Resource Indicator ().</span><span class="sxs-lookup"><span data-stu-id="e4d34-135">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="e4d34-136">Le `scriptLocation` attribut fait référence à la détection automatique des scripts de configuration de proxy.</span><span class="sxs-lookup"><span data-stu-id="e4d34-136">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="e4d34-137">Le <xref:System.Net.WebProxy> classe tente de localiser un script de configuration (généralement nommé Wpad.dat) lorsque le **utiliser le script de configuration automatique** option est sélectionnée dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e4d34-137">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span>  
  
 <span data-ttu-id="e4d34-138">Utilisez le `usesystemdefault` attribut pour les applications .NET Framework version 1.1 qui effectuent une migration vers la version 2.0.</span><span class="sxs-lookup"><span data-stu-id="e4d34-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="e4d34-139">Une exception est levée si le `proxyaddress` attribut spécifie un proxy par défaut non valide.</span><span class="sxs-lookup"><span data-stu-id="e4d34-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="e4d34-140">La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="e4d34-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e4d34-141">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="e4d34-141">Configuration Files</span></span>  
 <span data-ttu-id="e4d34-142">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e4d34-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4d34-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="e4d34-143">Example</span></span>  
 <span data-ttu-id="e4d34-144">L’exemple suivant utilise les valeurs par défaut du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local.</span><span class="sxs-lookup"><span data-stu-id="e4d34-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4d34-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4d34-145">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="e4d34-146">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="e4d34-146">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
