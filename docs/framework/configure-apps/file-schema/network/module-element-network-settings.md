---
title: "&lt;module&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a039f6ed985997c5557659abd299fe0fc7699a1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmodulegt-element-network-settings"></a><span data-ttu-id="b6681-102">&lt;module&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b6681-102">&lt;module&gt; Element (Network Settings)</span></span>
<span data-ttu-id="b6681-103">Ajoute un nouveau module proxy à l'application.</span><span class="sxs-lookup"><span data-stu-id="b6681-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="b6681-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b6681-104">\<configuration></span></span>  
<span data-ttu-id="b6681-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="b6681-105">\<system.net></span></span>  
<span data-ttu-id="b6681-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="b6681-106">\<defaultProxy></span></span>  
<span data-ttu-id="b6681-107">\<module ></span><span class="sxs-lookup"><span data-stu-id="b6681-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6681-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6681-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6681-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b6681-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b6681-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b6681-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6681-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="b6681-111">Attributes</span></span>  
  
|<span data-ttu-id="b6681-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="b6681-112">**Attribute**</span></span>|<span data-ttu-id="b6681-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="b6681-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="b6681-114">Le nom de type qualifié complet (indiqué par le <xref:System.Type.FullName%2A> propriété) et le nom de l’assembly (indiqué par le <xref:System.Reflection.Assembly.FullName%2A> propriété), séparés par des virgules, qui implémente le proxy.</span><span class="sxs-lookup"><span data-stu-id="b6681-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6681-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b6681-115">Child Elements</span></span>  
 <span data-ttu-id="b6681-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b6681-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6681-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b6681-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b6681-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="b6681-118">**Element**</span></span>|<span data-ttu-id="b6681-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="b6681-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b6681-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="b6681-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="b6681-121">Configure le serveur proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="b6681-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6681-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="b6681-122">Remarks</span></span>  
 <span data-ttu-id="b6681-123">Le `module` élément inscrit les classes proxy qui implémentent la <xref:System.Net.IWebProxy> interface.</span><span class="sxs-lookup"><span data-stu-id="b6681-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="b6681-124">Après l’inscription de la classe proxy, `module` peut être utilisé pour demander des informations via le proxy pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b6681-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="b6681-125">La valeur de la `type` attribut doit être le nom de classe du module et le nom de la bibliothèque de liens dynamiques (DLL) correspondant.</span><span class="sxs-lookup"><span data-stu-id="b6681-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b6681-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b6681-126">Configuration Files</span></span>  
 <span data-ttu-id="b6681-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b6681-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6681-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6681-128">Example</span></span>  
 <span data-ttu-id="b6681-129">L’exemple suivant inscrit une classe proxy personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b6681-129">The following example registers a custom proxy class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6681-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6681-130">See Also</span></span>  
 <xref:System.Net.IWebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="b6681-131">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="b6681-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
