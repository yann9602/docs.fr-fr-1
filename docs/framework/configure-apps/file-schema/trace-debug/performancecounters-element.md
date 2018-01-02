---
title: "&lt;performanceCounters&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 64afd62c6eeca7bce14e331fdc65fccfa3d02bce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltperformancecountersgt-element"></a><span data-ttu-id="84aa1-102">&lt;performanceCounters&gt; élément</span><span class="sxs-lookup"><span data-stu-id="84aa1-102">&lt;performanceCounters&gt; Element</span></span>
<span data-ttu-id="84aa1-103">Spécifie la taille de la mémoire globale partagée par les compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="84aa1-103">Specifies the size of the global memory shared by performance counters.</span></span>  
  
 <span data-ttu-id="84aa1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="84aa1-104">\<configuration></span></span>  
<span data-ttu-id="84aa1-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="84aa1-105">\<system.diagnostics></span></span>  
<span data-ttu-id="84aa1-106">\<performanceCounters ></span><span class="sxs-lookup"><span data-stu-id="84aa1-106">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84aa1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84aa1-107">Syntax</span></span>  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84aa1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="84aa1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="84aa1-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="84aa1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84aa1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="84aa1-110">Attributes</span></span>  
  
|<span data-ttu-id="84aa1-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="84aa1-111">Attribute</span></span>|<span data-ttu-id="84aa1-112">Description</span><span class="sxs-lookup"><span data-stu-id="84aa1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84aa1-113">FileMappingSize</span><span class="sxs-lookup"><span data-stu-id="84aa1-113">filemappingsize</span></span>|<span data-ttu-id="84aa1-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="84aa1-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="84aa1-115">Spécifie la taille, en octets, de la mémoire globale partagée par les compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="84aa1-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="84aa1-116">La valeur par défaut est 524288.</span><span class="sxs-lookup"><span data-stu-id="84aa1-116">The default is 524288.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84aa1-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="84aa1-117">Child Elements</span></span>  
 <span data-ttu-id="84aa1-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="84aa1-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84aa1-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="84aa1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="84aa1-120">Élément</span><span class="sxs-lookup"><span data-stu-id="84aa1-120">Element</span></span>|<span data-ttu-id="84aa1-121">Description</span><span class="sxs-lookup"><span data-stu-id="84aa1-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="84aa1-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84aa1-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="84aa1-123">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="84aa1-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84aa1-124">Notes</span><span class="sxs-lookup"><span data-stu-id="84aa1-124">Remarks</span></span>  
 <span data-ttu-id="84aa1-125">Compteurs de performance utilisent un fichier mappé en mémoire, ou mémoire partagée, pour publier les données de performances.</span><span class="sxs-lookup"><span data-stu-id="84aa1-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="84aa1-126">La taille de la mémoire partagée détermine le nombre d’instances peut être utilisé à la fois.</span><span class="sxs-lookup"><span data-stu-id="84aa1-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="84aa1-127">Il existe deux types de mémoire partagée : mémoire partagée globale et mémoire partagée séparée.</span><span class="sxs-lookup"><span data-stu-id="84aa1-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="84aa1-128">La mémoire partagée globale est utilisée par toutes les catégories de compteur de performance installés avec les versions de .NET Framework 1.0 ou 1.1.</span><span class="sxs-lookup"><span data-stu-id="84aa1-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="84aa1-129">Catégories de compteur de performance installés avec le .NET Framework version 2.0 utilisent une mémoire partagée distincte, chaque catégorie de compteur de performance possédant sa propre mémoire.</span><span class="sxs-lookup"><span data-stu-id="84aa1-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>  
  
 <span data-ttu-id="84aa1-130">La taille de la mémoire partagée globale peut être définie uniquement avec un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="84aa1-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="84aa1-131">La taille par défaut est 524 288 octets, la taille maximale est de 33 554 432 octets et la taille minimale est de 32 768 octets.</span><span class="sxs-lookup"><span data-stu-id="84aa1-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="84aa1-132">Étant donné que la mémoire partagée globale est partagée par tous les processus et les catégories, le créateur du premier spécifie la taille.</span><span class="sxs-lookup"><span data-stu-id="84aa1-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="84aa1-133">Si vous définissez la taille de votre fichier de configuration d’application, cette taille est utilisée uniquement si votre application est la première application qui provoque les compteurs de performances à exécuter.</span><span class="sxs-lookup"><span data-stu-id="84aa1-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="84aa1-134">Par conséquent, l’emplacement correct pour spécifier le `filemappingsize` valeur est le fichier Machine.config.</span><span class="sxs-lookup"><span data-stu-id="84aa1-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="84aa1-135">La mémoire dans la mémoire partagée globale ne peut pas être libérée par les compteurs de performances individuels, forScope mémoire partagée globale est épuisée si un grand nombre d’instances de compteur de performance avec des noms différents est créé.</span><span class="sxs-lookup"><span data-stu-id="84aa1-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>  
  
 <span data-ttu-id="84aa1-136">La taille de mémoire partagée séparée, la valeur DWORD FileMappingSize dans le Registre de clé HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<nom de la catégorie >*\Performance est référencé. tout d’abord, suivi par la valeur spécifiée pour la mémoire partagée globale dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="84aa1-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>*\Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="84aa1-137">Si la valeur FileMappingSize n’existe pas, alors que la taille de la mémoire partagée séparée est définie à un quart (1/4) le paramètre global dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="84aa1-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84aa1-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84aa1-138">See Also</span></span>  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
