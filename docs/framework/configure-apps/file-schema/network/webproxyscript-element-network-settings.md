---
title: "&lt;webProxyScript&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d1258301af903ef5c36df854c7c6dd504d6eef15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="22342-102">&lt;webProxyScript&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="22342-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="22342-103">Configure les caractéristiques du script utilisé pour découvrir les serveurs proxy Web.</span><span class="sxs-lookup"><span data-stu-id="22342-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="22342-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="22342-104">\<configuration></span></span>  
<span data-ttu-id="22342-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="22342-105">\<system.net></span></span>  
<span data-ttu-id="22342-106">\<Paramètres ></span><span class="sxs-lookup"><span data-stu-id="22342-106">\<settings></span></span>  
<span data-ttu-id="22342-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="22342-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22342-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22342-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22342-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="22342-109">Attributes and Elements</span></span>  
 <span data-ttu-id="22342-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="22342-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22342-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="22342-111">Attributes</span></span>  
  
|<span data-ttu-id="22342-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="22342-112">Attribute</span></span>|<span data-ttu-id="22342-113">Description</span><span class="sxs-lookup"><span data-stu-id="22342-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="22342-114">Spécifie la durée maximale de téléchargement du script en heures, minutes et secondes.</span><span class="sxs-lookup"><span data-stu-id="22342-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="22342-115">La valeur par défaut est une minute.</span><span class="sxs-lookup"><span data-stu-id="22342-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22342-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="22342-116">Child Elements</span></span>  
 <span data-ttu-id="22342-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="22342-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22342-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="22342-118">Parent Elements</span></span>  
  
|<span data-ttu-id="22342-119">Élément</span><span class="sxs-lookup"><span data-stu-id="22342-119">Element</span></span>|<span data-ttu-id="22342-120">Description</span><span class="sxs-lookup"><span data-stu-id="22342-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22342-121">Paramètres</span><span class="sxs-lookup"><span data-stu-id="22342-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="22342-122">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="22342-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22342-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="22342-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="22342-124">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="22342-124">Configuration Files</span></span>  
 <span data-ttu-id="22342-125">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="22342-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22342-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22342-126">See Also</span></span>  
 [<span data-ttu-id="22342-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="22342-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
