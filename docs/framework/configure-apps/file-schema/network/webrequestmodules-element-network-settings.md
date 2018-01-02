---
title: "&lt;webRequestModules&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f0da0e8afb2a9f89116b0d30992ce27b8520271d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a><span data-ttu-id="50a60-102">&lt;webRequestModules&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="50a60-102">&lt;webRequestModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="50a60-103">Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="50a60-103">Specifies modules to use to request information from network hosts.</span></span>  
  
 <span data-ttu-id="50a60-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="50a60-104">\<configuration></span></span>  
<span data-ttu-id="50a60-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="50a60-105">\<system.net></span></span>  
<span data-ttu-id="50a60-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="50a60-106">\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50a60-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50a60-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50a60-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="50a60-108">Attributes and Elements</span></span>  
 <span data-ttu-id="50a60-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="50a60-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50a60-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="50a60-110">Attributes</span></span>  
 <span data-ttu-id="50a60-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="50a60-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="50a60-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="50a60-112">Child Elements</span></span>  
  
|<span data-ttu-id="50a60-113">**Élément**</span><span class="sxs-lookup"><span data-stu-id="50a60-113">**Element**</span></span>|<span data-ttu-id="50a60-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="50a60-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="50a60-115">add</span><span class="sxs-lookup"><span data-stu-id="50a60-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="50a60-116">Ajoute un module de demande Web personnalisé à l’application.</span><span class="sxs-lookup"><span data-stu-id="50a60-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="50a60-117">clear</span><span class="sxs-lookup"><span data-stu-id="50a60-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="50a60-118">Supprime tous les modules de demande Web inscrits de l’application.</span><span class="sxs-lookup"><span data-stu-id="50a60-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="50a60-119">remove</span><span class="sxs-lookup"><span data-stu-id="50a60-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="50a60-120">Supprime un module de demande Web personnalisé de l’application.</span><span class="sxs-lookup"><span data-stu-id="50a60-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="50a60-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="50a60-121">Parent Elements</span></span>  
  
|<span data-ttu-id="50a60-122">**Élément**</span><span class="sxs-lookup"><span data-stu-id="50a60-122">**Element**</span></span>|<span data-ttu-id="50a60-123">**Description**</span><span class="sxs-lookup"><span data-stu-id="50a60-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="50a60-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="50a60-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="50a60-125">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="50a60-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50a60-126">Notes</span><span class="sxs-lookup"><span data-stu-id="50a60-126">Remarks</span></span>  
 <span data-ttu-id="50a60-127">Le `webRequestModules` élément inscrit les descendants de le <xref:System.Net.WebRequest> classe pour gérer les demandes d’informations sur les hôtes de réseau.</span><span class="sxs-lookup"><span data-stu-id="50a60-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="50a60-128">Les modules de demande Web doivent implémenter le <xref:System.Net.IWebRequestCreate> interface.</span><span class="sxs-lookup"><span data-stu-id="50a60-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="50a60-129">Le .NET Framework inclut des modules de demande Web pour les URI commençant par http://, https:// et file://.</span><span class="sxs-lookup"><span data-stu-id="50a60-129">The .NET Framework includes Web request modules for URIs that begin with http://, https://, and file://.</span></span> <span data-ttu-id="50a60-130">Vous pouvez substituer les modules par défaut qu’en inscrivant un module personnalisé dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="50a60-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="50a60-131">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="50a60-131">Configuration Files</span></span>  
 <span data-ttu-id="50a60-132">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="50a60-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50a60-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="50a60-133">Example</span></span>  
 <span data-ttu-id="50a60-134">L’exemple suivant inscrit le module HTTP par défaut.</span><span class="sxs-lookup"><span data-stu-id="50a60-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="50a60-135">Vous devez remplacer les valeurs de Version et de PublicKeyToken par les valeurs correctes pour le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="50a60-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="50a60-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50a60-136">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.IWebRequestCreate>  
 [<span data-ttu-id="50a60-137">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="50a60-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
