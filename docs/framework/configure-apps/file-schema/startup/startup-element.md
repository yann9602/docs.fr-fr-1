---
title: "&lt;démarrage&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4299775cd23162839ab9846adc7d2c64cc18a404
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltstartupgt-element"></a><span data-ttu-id="d5a2d-102">&lt;démarrage&gt; élément</span><span class="sxs-lookup"><span data-stu-id="d5a2d-102">&lt;startup&gt; Element</span></span>
<span data-ttu-id="d5a2d-103">Spécifie les informations de démarrage du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-103">Specifies common language runtime startup information.</span></span>  
  
 <span data-ttu-id="d5a2d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d5a2d-104">\<configuration></span></span>  
<span data-ttu-id="d5a2d-105">\<startup></span><span class="sxs-lookup"><span data-stu-id="d5a2d-105">\<startup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a2d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5a2d-106">Syntax</span></span>  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5a2d-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d5a2d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d5a2d-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5a2d-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="d5a2d-109">Attributes</span></span>  
  
|<span data-ttu-id="d5a2d-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="d5a2d-110">Attribute</span></span>|<span data-ttu-id="d5a2d-111">Description</span><span class="sxs-lookup"><span data-stu-id="d5a2d-111">Description</span></span>|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="d5a2d-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d5a2d-113">Spécifie s’il faut activer la [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] stratégie d’activation du runtime ou d’utiliser le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] stratégie d’activation.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-113">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] activation policy.</span></span>|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="d5a2d-114">Attribut d’useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="d5a2d-114">useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
  
|<span data-ttu-id="d5a2d-115">Value</span><span class="sxs-lookup"><span data-stu-id="d5a2d-115">Value</span></span>|<span data-ttu-id="d5a2d-116">Description</span><span class="sxs-lookup"><span data-stu-id="d5a2d-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="d5a2d-117">Activer [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] stratégie d’activation du runtime pour le runtime choisi, qui consiste à lier les techniques d’activation runtime hérité (telles que la [fonction CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) au runtime choisi dans le fichier de configuration au lieu de coupe les CLR version 2.0.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-117">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="d5a2d-118">Par conséquent, si CLR version 4 ou ultérieure est choisie dans le fichier de configuration, les assemblys en mode mixte créés avec les versions antérieures du .NET Framework sont chargées avec la version CLR choisie.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="d5a2d-119">Ce paramètre empêche CLR version 1.1 ou CLR version 2.0 de se charger dans le même processus, en désactivant efficacement la fonctionnalité côte à côte in-process.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|  
|`false`|<span data-ttu-id="d5a2d-120">Utilisez la stratégie d’activation par défaut pour le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et versions ultérieures, qui consiste à autoriser runtime hérité techniques charger le CLR version 1.1 ou 2.0 dans le processus d’activation.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-120">Use the default activation policy for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="d5a2d-121">Ce paramètre empêche les assemblys en mode mixte de charger dans le .NET Framework 4 ou version ultérieure, sauf si elles ont été générées avec le .NET Framework 4 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="d5a2d-122">Cette valeur est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-122">This value is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5a2d-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d5a2d-123">Child Elements</span></span>  
  
|<span data-ttu-id="d5a2d-124">Élément</span><span class="sxs-lookup"><span data-stu-id="d5a2d-124">Element</span></span>|<span data-ttu-id="d5a2d-125">Description</span><span class="sxs-lookup"><span data-stu-id="d5a2d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5a2d-126">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="d5a2d-126">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="d5a2d-127">Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="d5a2d-128">Applications générées avec la version 1.1 ou ultérieure du runtime doivent utiliser le  **\<supportedRuntime >** élément.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="d5a2d-129">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="d5a2d-129">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="d5a2d-130">Spécifie quelles versions du Common Language Runtime sont prises en charge par l'application.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-130">Specifies which versions of the common language runtime the application supports.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d5a2d-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d5a2d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="d5a2d-132">Élément</span><span class="sxs-lookup"><span data-stu-id="d5a2d-132">Element</span></span>|<span data-ttu-id="d5a2d-133">Description</span><span class="sxs-lookup"><span data-stu-id="d5a2d-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d5a2d-134">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5a2d-135">Notes</span><span class="sxs-lookup"><span data-stu-id="d5a2d-135">Remarks</span></span>  
 <span data-ttu-id="d5a2d-136">Le  **\<supportedRuntime >** élément doit être utilisé par toutes les applications générées à l’aide de la version 1.1 ou ultérieure du runtime.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="d5a2d-137">Les applications générées pour prendre en charge uniquement la version 1.0 du runtime doivent utiliser le  **\<requiredRuntime >** élément.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>  
  
 <span data-ttu-id="d5a2d-138">Le code de démarrage d’une application hébergée dans Microsoft Internet Explorer ignore la  **\<démarrage >** élément et ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="d5a2d-139">L’attribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="d5a2d-139">The useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
 <span data-ttu-id="d5a2d-140">Cet attribut est utile si votre application utilise des chemins d’activation hérités, tels que les [fonction CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), et vous souhaitez que ces chemins activent la version 4 du CLR au lieu d’une version antérieure, ou si votre application est génération avec la [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] mais a une dépendance sur un assembly en mode mixte généré avec une version antérieure du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="d5a2d-141">Dans ces scénarios, affectez à l’attribut `true`.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-141">In those scenarios, set the attribute to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5a2d-142">Affectez à l’attribut `true` empêche le chargement dans le même processus, en désactivant efficacement la fonctionnalité côte à côte in-process CLR version 1.1 ou CLR version 2.0 (voir [exécution côte à côte pour COM Interop](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span><span class="sxs-lookup"><span data-stu-id="d5a2d-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5a2d-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5a2d-143">Example</span></span>  
 <span data-ttu-id="d5a2d-144">L’exemple suivant montre comment spécifier la version du runtime dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d5a2d-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5a2d-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5a2d-145">See Also</span></span>  
 [<span data-ttu-id="d5a2d-146">Schéma des paramètres de démarrage</span><span class="sxs-lookup"><span data-stu-id="d5a2d-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="d5a2d-147">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="d5a2d-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d5a2d-148">\<PaveOver> Spécification de la version du runtime à utiliser</span><span class="sxs-lookup"><span data-stu-id="d5a2d-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [<span data-ttu-id="d5a2d-149">Exécution côte à côte pour COM Interop</span><span class="sxs-lookup"><span data-stu-id="d5a2d-149">Side-by-Side Execution for COM Interop</span></span>](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [<span data-ttu-id="d5a2d-150">Exécution côte à côte in-process</span><span class="sxs-lookup"><span data-stu-id="d5a2d-150">In-Process Side-by-Side Execution</span></span>](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
