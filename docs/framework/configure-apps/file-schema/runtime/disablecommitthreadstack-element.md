---
title: "&lt;disableCommitThreadStack&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a7961c62d46a10767b119c4c55a4b620e1ad782
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablecommitthreadstackgt-element"></a><span data-ttu-id="71bc6-102">&lt;disableCommitThreadStack&gt; élément</span><span class="sxs-lookup"><span data-stu-id="71bc6-102">&lt;disableCommitThreadStack&gt; Element</span></span>
<span data-ttu-id="71bc6-103">Spécifie si la pile des threads complète est validée quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="71bc6-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="71bc6-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="71bc6-104">\<configuration></span></span>  
<span data-ttu-id="71bc6-105">\<runtime ></span><span class="sxs-lookup"><span data-stu-id="71bc6-105">\<runtime></span></span>  
<span data-ttu-id="71bc6-106">\<disableCommitThreadStack ></span><span class="sxs-lookup"><span data-stu-id="71bc6-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71bc6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71bc6-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71bc6-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="71bc6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="71bc6-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="71bc6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71bc6-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="71bc6-110">Attributes</span></span>  
  
|<span data-ttu-id="71bc6-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="71bc6-111">Attribute</span></span>|<span data-ttu-id="71bc6-112">Description</span><span class="sxs-lookup"><span data-stu-id="71bc6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71bc6-113">enabled</span><span class="sxs-lookup"><span data-stu-id="71bc6-113">enabled</span></span>|<span data-ttu-id="71bc6-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="71bc6-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="71bc6-115">Spécifie si la validation de la pile des threads complète lors du démarrage de thread (comportement par défaut) est désactivée.</span><span class="sxs-lookup"><span data-stu-id="71bc6-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="71bc6-116">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="71bc6-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="71bc6-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="71bc6-117">Value</span></span>|<span data-ttu-id="71bc6-118">Description</span><span class="sxs-lookup"><span data-stu-id="71bc6-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71bc6-119">0</span><span class="sxs-lookup"><span data-stu-id="71bc6-119">0</span></span>|<span data-ttu-id="71bc6-120">Ne pas désactiver le comportement par défaut du Common Language Runtime, qui consiste à valider la pile des threads complète quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="71bc6-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="71bc6-121">1</span><span class="sxs-lookup"><span data-stu-id="71bc6-121">1</span></span>|<span data-ttu-id="71bc6-122">Désactiver le comportement par défaut du Common Language Runtime, qui consiste à valider la pile des threads complète quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="71bc6-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71bc6-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="71bc6-123">Child Elements</span></span>  
 <span data-ttu-id="71bc6-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="71bc6-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71bc6-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="71bc6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="71bc6-126">Élément</span><span class="sxs-lookup"><span data-stu-id="71bc6-126">Element</span></span>|<span data-ttu-id="71bc6-127">Description</span><span class="sxs-lookup"><span data-stu-id="71bc6-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="71bc6-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="71bc6-128">The root element in every configuration file used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
|`runtime`|<span data-ttu-id="71bc6-129">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="71bc6-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71bc6-130">Notes</span><span class="sxs-lookup"><span data-stu-id="71bc6-130">Remarks</span></span>  
 <span data-ttu-id="71bc6-131">Le comportement par défaut du Common Language Runtime consiste à valider la pile des threads complète quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="71bc6-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="71bc6-132">Si un grand nombre de threads doivent être créés sur un serveur disposant d’une mémoire limitée, et que la plupart de ces threads utilisent très peu d’espace de pile, les performances du serveur peuvent être améliorées si le Common Language Runtime ne valide pas la pile des threads complète immédiatement quand un thread est démarré.</span><span class="sxs-lookup"><span data-stu-id="71bc6-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71bc6-133">Les hôtes non managés peuvent utiliser l’indicateur de démarrage `STARTUP_DISABLE_COMMITTHREADSTACK` dans l’énumération [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) pour obtenir le même résultat.</span><span class="sxs-lookup"><span data-stu-id="71bc6-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71bc6-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="71bc6-134">Example</span></span>  
 <span data-ttu-id="71bc6-135">L’exemple suivant montre comment désactiver le comportement par défaut du Common Language Runtime, qui consiste à valider la pile des threads complète lors du démarrage d’un thread.</span><span class="sxs-lookup"><span data-stu-id="71bc6-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="71bc6-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71bc6-136">See Also</span></span>  
 [<span data-ttu-id="71bc6-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="71bc6-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="71bc6-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="71bc6-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
