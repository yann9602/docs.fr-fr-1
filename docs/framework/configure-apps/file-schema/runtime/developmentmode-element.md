---
title: "&lt;developmentMode&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4573c3a5e0cf64996f2a4e109736d966b754494a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdevelopmentmodegt-element"></a><span data-ttu-id="e44c3-102">&lt;developmentMode&gt; élément</span><span class="sxs-lookup"><span data-stu-id="e44c3-102">&lt;developmentMode&gt; Element</span></span>
<span data-ttu-id="e44c3-103">Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="e44c3-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="e44c3-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e44c3-104">\<configuration></span></span>  
<span data-ttu-id="e44c3-105">\<runtime ></span><span class="sxs-lookup"><span data-stu-id="e44c3-105">\<runtime></span></span>  
<span data-ttu-id="e44c3-106">\<developmentMode ></span><span class="sxs-lookup"><span data-stu-id="e44c3-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e44c3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e44c3-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e44c3-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e44c3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e44c3-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e44c3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e44c3-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e44c3-110">Attributes</span></span>  
  
|<span data-ttu-id="e44c3-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="e44c3-111">Attribute</span></span>|<span data-ttu-id="e44c3-112">Description</span><span class="sxs-lookup"><span data-stu-id="e44c3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e44c3-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="e44c3-113">**developerInstallation**</span></span>|<span data-ttu-id="e44c3-114">Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="e44c3-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="e44c3-115">Attribut de developerInstallation</span><span class="sxs-lookup"><span data-stu-id="e44c3-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="e44c3-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="e44c3-116">Value</span></span>|<span data-ttu-id="e44c3-117">Description</span><span class="sxs-lookup"><span data-stu-id="e44c3-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e44c3-118">**true**</span><span class="sxs-lookup"><span data-stu-id="e44c3-118">**true**</span></span>|<span data-ttu-id="e44c3-119">Recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="e44c3-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="e44c3-120">**false**</span><span class="sxs-lookup"><span data-stu-id="e44c3-120">**false**</span></span>|<span data-ttu-id="e44c3-121">Ne recherche pas les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="e44c3-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="e44c3-122">Ceci est la valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e44c3-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e44c3-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e44c3-123">Child Elements</span></span>  
 <span data-ttu-id="e44c3-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e44c3-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e44c3-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e44c3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e44c3-126">Élément</span><span class="sxs-lookup"><span data-stu-id="e44c3-126">Element</span></span>|<span data-ttu-id="e44c3-127">Description</span><span class="sxs-lookup"><span data-stu-id="e44c3-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e44c3-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e44c3-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e44c3-129">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e44c3-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e44c3-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="e44c3-130">Remarks</span></span>  
 <span data-ttu-id="e44c3-131">Utilisez ce paramètre uniquement au moment du développement.</span><span class="sxs-lookup"><span data-stu-id="e44c3-131">Use this setting only at development time.</span></span> <span data-ttu-id="e44c3-132">Le runtime ne vérifie pas les versions sur les assemblys avec nom fort trouvés dans DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="e44c3-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="e44c3-133">Elle utilise simplement le premier assembly qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="e44c3-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e44c3-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="e44c3-134">Example</span></span>  
 <span data-ttu-id="e44c3-135">L’exemple suivant montre comment le runtime recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="e44c3-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e44c3-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e44c3-136">See Also</span></span>  
 [<span data-ttu-id="e44c3-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="e44c3-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="e44c3-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="e44c3-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="e44c3-139">Comment : localiser des assemblys à l'aide de DEVPATH</span><span class="sxs-lookup"><span data-stu-id="e44c3-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
