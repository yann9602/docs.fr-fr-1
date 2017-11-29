---
title: "&lt;Supprimez&gt; , élément pour webRequestModules (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 43f0d30f8c18c4755f31d0c851c773207bc15b78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="df38f-102">&lt;Supprimez&gt; , élément pour webRequestModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="df38f-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="df38f-103">Supprime un module de demande Web personnalisé de l’application.</span><span class="sxs-lookup"><span data-stu-id="df38f-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="df38f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="df38f-104">\<configuration></span></span>  
<span data-ttu-id="df38f-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="df38f-105">\<system.net></span></span>  
<span data-ttu-id="df38f-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="df38f-106">\<webRequestModules></span></span>  
<span data-ttu-id="df38f-107">\<Supprimer ></span><span class="sxs-lookup"><span data-stu-id="df38f-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df38f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df38f-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df38f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="df38f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="df38f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="df38f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df38f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="df38f-111">Attributes</span></span>  
  
|<span data-ttu-id="df38f-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="df38f-112">**Attribute**</span></span>|<span data-ttu-id="df38f-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="df38f-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="df38f-114">Le préfixe URI pour les demandes gérées par ce module de demande Web.</span><span class="sxs-lookup"><span data-stu-id="df38f-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df38f-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="df38f-115">Child Elements</span></span>  
 <span data-ttu-id="df38f-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="df38f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df38f-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="df38f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="df38f-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="df38f-118">**Element**</span></span>|<span data-ttu-id="df38f-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="df38f-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="df38f-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="df38f-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="df38f-121">Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="df38f-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df38f-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="df38f-122">Remarks</span></span>  
 <span data-ttu-id="df38f-123">Le `remove` élément supprime le module de demande Web inscrit pour le préfixe URI spécifié.</span><span class="sxs-lookup"><span data-stu-id="df38f-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="df38f-124">La valeur de la `prefix` attribut doit-elle être les premiers caractères d’un URI valide, par exemple, « http » ou « http://www.contoso.com ».</span><span class="sxs-lookup"><span data-stu-id="df38f-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "http", or "http://www.contoso.com".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="df38f-125">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="df38f-125">Configuration Files</span></span>  
 <span data-ttu-id="df38f-126">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="df38f-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df38f-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="df38f-127">Example</span></span>  
 <span data-ttu-id="df38f-128">L’exemple suivant supprime le module de demande Web existant pour HTTP et inscrit un nouveau module de demande Web personnalisé pour les demandes HTTP www.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="df38f-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to www.contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="df38f-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df38f-129">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="df38f-130">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="df38f-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
