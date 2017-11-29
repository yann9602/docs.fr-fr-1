---
title: "&lt;ajouter&gt; , élément pour webRequestModules (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fd407f77e75bce4bdbc37acd5f28bbe39f92d564
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="d93e2-102">&lt;ajouter&gt; , élément pour webRequestModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="d93e2-102">&lt;add&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="d93e2-103">Ajoute un module de demande Web personnalisé à l’application.</span><span class="sxs-lookup"><span data-stu-id="d93e2-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="d93e2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d93e2-104">\<configuration></span></span>  
<span data-ttu-id="d93e2-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="d93e2-105">\<system.net></span></span>  
<span data-ttu-id="d93e2-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="d93e2-106">\<webRequestModules></span></span>  
<span data-ttu-id="d93e2-107">\<add></span><span class="sxs-lookup"><span data-stu-id="d93e2-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d93e2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d93e2-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d93e2-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d93e2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d93e2-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d93e2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d93e2-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="d93e2-111">Attributes</span></span>  
  
|<span data-ttu-id="d93e2-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="d93e2-112">**Attribute**</span></span>|<span data-ttu-id="d93e2-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="d93e2-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="d93e2-114">Le préfixe URI pour les demandes gérées par ce module de demande Web.</span><span class="sxs-lookup"><span data-stu-id="d93e2-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="d93e2-115">Le nom de type qualifié complet (indiqué par le <xref:System.Type.FullName%2A> propriété) et le nom de l’assembly (indiqué par le <xref:System.Reflection.Assembly.FullName%2A> propriété), séparés par des virgules, qui implémente ce module de demande Web.</span><span class="sxs-lookup"><span data-stu-id="d93e2-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d93e2-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d93e2-116">Child Elements</span></span>  
 <span data-ttu-id="d93e2-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d93e2-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d93e2-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d93e2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d93e2-119">**Élément**</span><span class="sxs-lookup"><span data-stu-id="d93e2-119">**Element**</span></span>|<span data-ttu-id="d93e2-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="d93e2-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d93e2-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="d93e2-121">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="d93e2-122">Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="d93e2-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d93e2-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="d93e2-123">Remarks</span></span>  
 <span data-ttu-id="d93e2-124">Le `prefix` attribut définit le préfixe URI qui utilise le module de demande Web spécifié.</span><span class="sxs-lookup"><span data-stu-id="d93e2-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="d93e2-125">Modules de demande Web sont généralement inscrits pour gérer un protocole spécifique, tel que HTTP ou FTP, mais peuvent être inscrits pour gérer une demande à un serveur spécifique ou un chemin d’accès sur un serveur.</span><span class="sxs-lookup"><span data-stu-id="d93e2-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="d93e2-126">Le module de demande Web est créé lorsqu’un préfixe URI correspondant est passé à la <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="d93e2-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="d93e2-127">La valeur de la `prefix` attribut doit-elle être les premiers caractères d’un URI valide, par exemple, « http » ou « http://www.contoso.com ».</span><span class="sxs-lookup"><span data-stu-id="d93e2-127">The value for the `prefix` attribute should be the leading characters of a valid URI --for example, "http", or "http://www.contoso.com".</span></span>  
  
 <span data-ttu-id="d93e2-128">La valeur de la `type` attribut doit être un nom de type valide et le nom de l’assembly correspondant, séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="d93e2-128">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma .</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d93e2-129">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="d93e2-129">Configuration Files</span></span>  
 <span data-ttu-id="d93e2-130">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d93e2-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d93e2-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="d93e2-131">Example</span></span>  
 <span data-ttu-id="d93e2-132">L’exemple suivant inscrit un module de demande Web personnalisé pour HTTP.</span><span class="sxs-lookup"><span data-stu-id="d93e2-132">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="d93e2-133">Vous devez remplacer les valeurs de Version et de PublicKeyToken par les valeurs correctes pour le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="d93e2-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d93e2-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d93e2-134">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="d93e2-135">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="d93e2-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
