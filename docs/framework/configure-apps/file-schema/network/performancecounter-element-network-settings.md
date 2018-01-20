---
title: "&lt;performanceCounter&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c50bf9e882ade86e70db217a75fef2a893c45572
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltperformancecountergt-element-network-settings"></a><span data-ttu-id="33489-102">&lt;performanceCounter&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="33489-102">&lt;performanceCounter&gt; Element (Network Settings)</span></span>
<span data-ttu-id="33489-103">Active ou désactive les compteurs de performance réseau.</span><span class="sxs-lookup"><span data-stu-id="33489-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="33489-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="33489-104">\<configuration></span></span>  
<span data-ttu-id="33489-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="33489-105">\<system.net></span></span>  
<span data-ttu-id="33489-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="33489-106">\<settings></span></span>  
<span data-ttu-id="33489-107">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="33489-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33489-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33489-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33489-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="33489-109">Attributes and Elements</span></span>  
 <span data-ttu-id="33489-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="33489-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33489-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="33489-111">Attributes</span></span>  
  
|<span data-ttu-id="33489-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="33489-112">Attribute</span></span>|<span data-ttu-id="33489-113">Description</span><span class="sxs-lookup"><span data-stu-id="33489-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="33489-114">Spécifie si les compteurs de performance réseau sont activés.</span><span class="sxs-lookup"><span data-stu-id="33489-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="33489-115">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="33489-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33489-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="33489-116">Child Elements</span></span>  
 <span data-ttu-id="33489-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="33489-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="33489-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="33489-118">Parent Elements</span></span>  
  
|<span data-ttu-id="33489-119">Élément</span><span class="sxs-lookup"><span data-stu-id="33489-119">Element</span></span>|<span data-ttu-id="33489-120">Description</span><span class="sxs-lookup"><span data-stu-id="33489-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33489-121">settings</span><span class="sxs-lookup"><span data-stu-id="33489-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="33489-122">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="33489-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33489-123">Notes</span><span class="sxs-lookup"><span data-stu-id="33489-123">Remarks</span></span>  
 <span data-ttu-id="33489-124">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="33489-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="33489-125">Les compteurs de performance réseau doivent être activés dans le fichier de configuration pour pouvoir être utilisés.</span><span class="sxs-lookup"><span data-stu-id="33489-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="33489-126">L'ensemble des compteurs de performance réseau sont activés ou désactivés avec un paramètre unique dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="33489-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="33489-127">Il n'est pas possible d'activer ou de désactiver ces compteurs de manière individuelle.</span><span class="sxs-lookup"><span data-stu-id="33489-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="33489-128">Pour plus d’informations sur les compteurs de performance réseau spécifiques, consultez [compteurs de Performance réseau](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd).</span><span class="sxs-lookup"><span data-stu-id="33489-128">For more information on the specific networking performance counters, see [Networking Performance Counters](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd).</span></span>  
  
 <span data-ttu-id="33489-129">La valeur par défaut est que les performances réseau les compteurs sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="33489-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="33489-130">Le <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> propriété peut être utilisée pour obtenir la valeur actuelle de la **activé** attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="33489-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33489-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="33489-131">Example</span></span>  
 <span data-ttu-id="33489-132">L’exemple suivant montre comment configurer le <xref:System.Net> et les espaces de noms pour activer les compteurs de performance réseau.</span><span class="sxs-lookup"><span data-stu-id="33489-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33489-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33489-133">See Also</span></span>  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="33489-134">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="33489-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="33489-135">Compteurs de Performance réseau</span><span class="sxs-lookup"><span data-stu-id="33489-135">Networking Performance Counters</span></span>](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd)
