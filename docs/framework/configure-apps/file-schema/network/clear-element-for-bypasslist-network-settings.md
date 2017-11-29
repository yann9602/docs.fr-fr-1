---
title: "&lt;Désactivez&gt; , élément pour bypasslist (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5ee20b9177d519010c40351e335973dce10256f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-bypasslist-network-settings"></a><span data-ttu-id="882cc-102">&lt;Désactivez&gt; , élément pour bypasslist (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="882cc-102">&lt;clear&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="882cc-103">Efface la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="882cc-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="882cc-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="882cc-104">\<configuration></span></span>  
<span data-ttu-id="882cc-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="882cc-105">\<system.net></span></span>  
<span data-ttu-id="882cc-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="882cc-106">\<defaultProxy></span></span>  
<span data-ttu-id="882cc-107">\<BypassList ></span><span class="sxs-lookup"><span data-stu-id="882cc-107">\<bypasslist></span></span>  
<span data-ttu-id="882cc-108">\<Désactivez ></span><span class="sxs-lookup"><span data-stu-id="882cc-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="882cc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="882cc-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="882cc-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="882cc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="882cc-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="882cc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="882cc-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="882cc-112">Attributes</span></span>  
 <span data-ttu-id="882cc-113">Aucun</span><span class="sxs-lookup"><span data-stu-id="882cc-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="882cc-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="882cc-114">Child Elements</span></span>  
 <span data-ttu-id="882cc-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="882cc-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="882cc-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="882cc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="882cc-117">**Élément**</span><span class="sxs-lookup"><span data-stu-id="882cc-117">**Element**</span></span>|<span data-ttu-id="882cc-118">**Description**</span><span class="sxs-lookup"><span data-stu-id="882cc-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="882cc-119">BypassList</span><span class="sxs-lookup"><span data-stu-id="882cc-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="882cc-120">Fournit un ensemble d’expressions régulières décrivant les adresses qui n’utilisent pas un proxy.</span><span class="sxs-lookup"><span data-stu-id="882cc-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="882cc-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="882cc-121">Remarks</span></span>  
 <span data-ttu-id="882cc-122">Le `clear` élément efface toutes les entrées de la liste d’exclusion.</span><span class="sxs-lookup"><span data-stu-id="882cc-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="882cc-123">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="882cc-123">Configuration Files</span></span>  
 <span data-ttu-id="882cc-124">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="882cc-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="882cc-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="882cc-125">Example</span></span>  
 <span data-ttu-id="882cc-126">L’exemple suivant efface la liste d’exclusion, puis ajoute deux adresses à la liste d’exclusion.</span><span class="sxs-lookup"><span data-stu-id="882cc-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="882cc-127">La première contourne le proxy pour tous les serveurs dans le domaine contoso.com ; la deuxième contourne le proxy pour tous les serveurs dont l’adresse IP commence par 192.168.</span><span class="sxs-lookup"><span data-stu-id="882cc-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="882cc-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="882cc-128">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="882cc-129">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="882cc-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
