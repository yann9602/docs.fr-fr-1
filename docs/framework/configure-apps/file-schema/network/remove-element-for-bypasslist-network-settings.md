---
title: "&lt;Supprimez&gt; , élément pour bypasslist (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove elemment, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a87632ec9725aa24d085ca6c1bf1e54545b324fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-bypasslist-network-settings"></a><span data-ttu-id="c6352-102">&lt;Supprimez&gt; , élément pour bypasslist (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="c6352-102">&lt;remove&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="c6352-103">Supprime une adresse IP ou le nom DNS de la liste de contournement du proxy.</span><span class="sxs-lookup"><span data-stu-id="c6352-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>  
  
 <span data-ttu-id="c6352-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c6352-104">\<configuration></span></span>  
<span data-ttu-id="c6352-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="c6352-105">\<system.net></span></span>  
<span data-ttu-id="c6352-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="c6352-106">\<defaultProxy></span></span>  
<span data-ttu-id="c6352-107">\<BypassList ></span><span class="sxs-lookup"><span data-stu-id="c6352-107">\<bypasslist></span></span>  
<span data-ttu-id="c6352-108">\<Supprimer ></span><span class="sxs-lookup"><span data-stu-id="c6352-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6352-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6352-109">Syntax</span></span>  
  
```xml  
<remove   
  address="regular expression"   
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6352-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c6352-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c6352-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c6352-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6352-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="c6352-112">Attributes</span></span>  
  
|<span data-ttu-id="c6352-113">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="c6352-113">**Attribute**</span></span>|<span data-ttu-id="c6352-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="c6352-114">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="c6352-115">Une expression régulière décrivant une adresse IP ou un nom DNS.</span><span class="sxs-lookup"><span data-stu-id="c6352-115">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6352-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c6352-116">Child Elements</span></span>  
 <span data-ttu-id="c6352-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c6352-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6352-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c6352-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c6352-119">**Élément**</span><span class="sxs-lookup"><span data-stu-id="c6352-119">**Element**</span></span>|<span data-ttu-id="c6352-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="c6352-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c6352-121">BypassList</span><span class="sxs-lookup"><span data-stu-id="c6352-121">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="c6352-122">Fournit un ensemble d’expressions régulières décrivant les adresses qui n’utilisent pas un proxy.</span><span class="sxs-lookup"><span data-stu-id="c6352-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6352-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="c6352-123">Remarks</span></span>  
 <span data-ttu-id="c6352-124">Le `remove` élément supprime des expressions régulières décrivant les adresses IP ou des noms de serveur DNS dans la liste des adresses qui contournent un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="c6352-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="c6352-125">Les adresses ont été définis précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="c6352-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="c6352-126">La valeur de la `address` attribut doit être une expression régulière qui décrit un ensemble d’adresses IP ou des noms d’hôte.</span><span class="sxs-lookup"><span data-stu-id="c6352-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="c6352-127">Pour plus d’informations sur les expressions régulières, consultez. [Expressions régulières .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c6352-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c6352-128">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="c6352-128">Configuration Files</span></span>  
 <span data-ttu-id="c6352-129">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c6352-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6352-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6352-130">Example</span></span>  
 <span data-ttu-id="c6352-131">L’exemple suivant supprime toute définition précédente pour le domaine adventure-works.com, puis ajoute le domaine contoso.com à la liste d’exclusion.</span><span class="sxs-lookup"><span data-stu-id="c6352-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <remove address="[a-z]+\.adventure-works\.com$" />  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6352-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6352-132">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="c6352-133">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="c6352-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
