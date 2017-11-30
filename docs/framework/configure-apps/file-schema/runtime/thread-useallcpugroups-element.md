---
title: "&lt;Thread_UseAllCpuGroups&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 187e391acf3b80a5ae2dfe795c4a3b397af815ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltthreaduseallcpugroupsgt-element"></a><span data-ttu-id="0e50c-102">&lt;Thread_UseAllCpuGroups&gt; élément</span><span class="sxs-lookup"><span data-stu-id="0e50c-102">&lt;Thread_UseAllCpuGroups&gt; Element</span></span>
<span data-ttu-id="0e50c-103">Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="0e50c-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>  
  
 <span data-ttu-id="0e50c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0e50c-104">\<configuration></span></span>  
<span data-ttu-id="0e50c-105">\<runtime ></span><span class="sxs-lookup"><span data-stu-id="0e50c-105">\<runtime></span></span>  
<span data-ttu-id="0e50c-106">< Thread_UseAllCpuGroups ></span><span class="sxs-lookup"><span data-stu-id="0e50c-106"><Thread_UseAllCpuGroups></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e50c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e50c-107">Syntax</span></span>  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e50c-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0e50c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0e50c-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0e50c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e50c-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0e50c-110">Attributes</span></span>  
  
|<span data-ttu-id="0e50c-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="0e50c-111">Attribute</span></span>|<span data-ttu-id="0e50c-112">Description</span><span class="sxs-lookup"><span data-stu-id="0e50c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0e50c-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="0e50c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="0e50c-114">Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.</span><span class="sxs-lookup"><span data-stu-id="0e50c-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0e50c-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="0e50c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="0e50c-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="0e50c-116">Value</span></span>|<span data-ttu-id="0e50c-117">Description</span><span class="sxs-lookup"><span data-stu-id="0e50c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0e50c-118">Le runtime ne distribue pas les threads managés sur plusieurs groupes de l’UC.</span><span class="sxs-lookup"><span data-stu-id="0e50c-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="0e50c-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0e50c-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="0e50c-120">Le runtime répartit les threads managés sur plusieurs groupes d’UC, si l’ordinateur dispose de plusieurs groupes de l’UC et la [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) élément est activé.</span><span class="sxs-lookup"><span data-stu-id="0e50c-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e50c-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0e50c-121">Child Elements</span></span>  
 <span data-ttu-id="0e50c-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0e50c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e50c-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0e50c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0e50c-124">Élément</span><span class="sxs-lookup"><span data-stu-id="0e50c-124">Element</span></span>|<span data-ttu-id="0e50c-125">Description</span><span class="sxs-lookup"><span data-stu-id="0e50c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0e50c-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0e50c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0e50c-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0e50c-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e50c-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="0e50c-128">Remarks</span></span>  
 <span data-ttu-id="0e50c-129">Lorsqu’un ordinateur a plusieurs groupes de l’UC, l’activation de cet élément, le runtime répartir les threads managés sur tous les groupes de l’UC.</span><span class="sxs-lookup"><span data-stu-id="0e50c-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="0e50c-130">Pour utiliser cette fonctionnalité, vous devez également activer le [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) élément, qui étend le garbage collection pour tous les groupes de l’UC et prend tous les cœurs en compte lors de la création et l’équilibrage des segments de mémoire.</span><span class="sxs-lookup"><span data-stu-id="0e50c-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="0e50c-131">L’activation de la [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) élément requiert l’activation de la [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="0e50c-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="0e50c-132">Si ces éléments ne sont pas activées, l’activation de la `<Thread_UseAllCpuGroups>` élément n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="0e50c-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e50c-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="0e50c-133">Example</span></span>  
 <span data-ttu-id="0e50c-134">L’exemple suivant montre comment activer la prise en charge de plusieurs groupes de l’UC.</span><span class="sxs-lookup"><span data-stu-id="0e50c-134">The following example shows how to enable support for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e50c-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e50c-135">See Also</span></span>  
 [<span data-ttu-id="0e50c-136">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="0e50c-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="0e50c-137">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="0e50c-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="0e50c-138">\<GCCpuGroup > élément</span><span class="sxs-lookup"><span data-stu-id="0e50c-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
