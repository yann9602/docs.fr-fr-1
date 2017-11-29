---
title: "&lt;UseSmallInternalThreadStacks&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2558423b412333a4d6ac9f650ad8ff3dab449d74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a><span data-ttu-id="ad1c8-102">&lt;UseSmallInternalThreadStacks&gt; élément</span><span class="sxs-lookup"><span data-stu-id="ad1c8-102">&lt;UseSmallInternalThreadStacks&gt; Element</span></span>
<span data-ttu-id="ad1c8-103">Demandes de réduire la mémoire que le common language runtime (CLR) utilisent en spécifiant des tailles de pile explicites lorsqu’il crée certains threads qu’il utilise en interne, au lieu d’utiliser la taille de pile par défaut pour ces threads.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="ad1c8-104">\<configuration > élément</span><span class="sxs-lookup"><span data-stu-id="ad1c8-104">\<configuration> Element</span></span>  
<span data-ttu-id="ad1c8-105">\<runtime > élément</span><span class="sxs-lookup"><span data-stu-id="ad1c8-105">\<runtime> Element</span></span>  
<span data-ttu-id="ad1c8-106">\<UseSmallInternalThreadStacks > élément</span><span class="sxs-lookup"><span data-stu-id="ad1c8-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad1c8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad1c8-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad1c8-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ad1c8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ad1c8-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad1c8-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="ad1c8-110">Attributes</span></span>  
  
|<span data-ttu-id="ad1c8-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="ad1c8-111">Attribute</span></span>|<span data-ttu-id="ad1c8-112">Description</span><span class="sxs-lookup"><span data-stu-id="ad1c8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad1c8-113">enabled</span><span class="sxs-lookup"><span data-stu-id="ad1c8-113">enabled</span></span>|<span data-ttu-id="ad1c8-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ad1c8-115">Spécifie s’il faut demander que le CLR utilisation explicite des tailles de pile au lieu de la taille de pile par défaut lorsqu’il crée certains threads qu’il utilise en interne.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="ad1c8-116">Les tailles de pile explicites sont inférieures à la taille de pile par défaut de 1 Mo.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ad1c8-117">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="ad1c8-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="ad1c8-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="ad1c8-118">Value</span></span>|<span data-ttu-id="ad1c8-119">Description</span><span class="sxs-lookup"><span data-stu-id="ad1c8-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ad1c8-120">true</span><span class="sxs-lookup"><span data-stu-id="ad1c8-120">true</span></span>|<span data-ttu-id="ad1c8-121">Demander des tailles de pile explicite.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="ad1c8-122">false</span><span class="sxs-lookup"><span data-stu-id="ad1c8-122">false</span></span>|<span data-ttu-id="ad1c8-123">Utilisez la taille de pile par défaut.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-123">Use the default stack size.</span></span> <span data-ttu-id="ad1c8-124">Ceci est la valeur par défaut pour le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad1c8-124">This is the default for the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad1c8-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ad1c8-125">Child Elements</span></span>  
 <span data-ttu-id="ad1c8-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad1c8-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ad1c8-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ad1c8-128">Élément</span><span class="sxs-lookup"><span data-stu-id="ad1c8-128">Element</span></span>|<span data-ttu-id="ad1c8-129">Description</span><span class="sxs-lookup"><span data-stu-id="ad1c8-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ad1c8-130">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ad1c8-131">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad1c8-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="ad1c8-132">Remarks</span></span>  
 <span data-ttu-id="ad1c8-133">Cet élément de configuration est utilisé pour demander l’utilisation réduite de la mémoire virtuelle dans un processus, car les tailles de threads explicites que le CLR utilise pour ses threads internes, si la demande est honorée, sont plus petites que la taille par défaut.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ad1c8-134">Cet élément de configuration est une demande au CLR plutôt qu’une spécification absolue.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="ad1c8-135">Dans la [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], la demande est honorée uniquement pour les x86 architecture.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-135">In the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="ad1c8-136">Cet élément peut complètement ignoré dans les futures versions du CLR ou remplacé par des tailles de pile explicites qui sont toujours utilisés pour les threads internes sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="ad1c8-137">Spécification de que cet élément de configuration de transactions fiabilité pour une utilisation de mémoire virtuelle plus petite si le CLR répond à la demande, car la plus petite taille de pile peut augmenter dépasse plus probable.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad1c8-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="ad1c8-138">Example</span></span>  
 <span data-ttu-id="ad1c8-139">L’exemple suivant montre comment demander que la CLR utilisation explicite des tailles de pile pour certains threads qu’il utilise en interne.</span><span class="sxs-lookup"><span data-stu-id="ad1c8-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad1c8-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad1c8-140">See Also</span></span>  
 [<span data-ttu-id="ad1c8-141">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="ad1c8-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ad1c8-142">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="ad1c8-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
