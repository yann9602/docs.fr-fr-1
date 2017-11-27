---
title: "&lt;shadowCopyVerifyByTimestamp&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 261962819e9b2b37682a13bffb53d2912a660566
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a><span data-ttu-id="3f863-102">&lt;shadowCopyVerifyByTimestamp&gt; élément</span><span class="sxs-lookup"><span data-stu-id="3f863-102">&lt;shadowCopyVerifyByTimestamp&gt; Element</span></span>
<span data-ttu-id="3f863-103">Indique si les clichés instantanés utilisent le comportement de démarrage par défaut introduit dans le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], ou reviennent au comportement de démarrage des versions précédentes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f863-103">Specifies whether shadow copying uses the default startup behavior introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="3f863-104">\<configuration > élément</span><span class="sxs-lookup"><span data-stu-id="3f863-104">\<configuration> Element</span></span>  
<span data-ttu-id="3f863-105">\<runtime > élément</span><span class="sxs-lookup"><span data-stu-id="3f863-105">\<runtime> Element</span></span>  
<span data-ttu-id="3f863-106">\<shadowCopyVerifyByTimestamp > élément</span><span class="sxs-lookup"><span data-stu-id="3f863-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f863-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f863-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f863-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3f863-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3f863-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3f863-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f863-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="3f863-110">Attributes</span></span>  
  
|<span data-ttu-id="3f863-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="3f863-111">Attribute</span></span>|<span data-ttu-id="3f863-112">Description</span><span class="sxs-lookup"><span data-stu-id="3f863-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f863-113">enabled</span><span class="sxs-lookup"><span data-stu-id="3f863-113">enabled</span></span>|<span data-ttu-id="3f863-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="3f863-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="3f863-115">Spécifie si les domaines d’application qui utilisent les clichés instantanés comparer les horodatages des assemblys au démarrage, afin de déterminer si un assembly a été mis à jour avant la création de l’assembly de clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="3f863-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3f863-116">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="3f863-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="3f863-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="3f863-117">Value</span></span>|<span data-ttu-id="3f863-118">Description</span><span class="sxs-lookup"><span data-stu-id="3f863-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3f863-119">true</span><span class="sxs-lookup"><span data-stu-id="3f863-119">true</span></span>|<span data-ttu-id="3f863-120">Au démarrage, copie uniquement les assemblys qui ont été mis à jour depuis leur dernière copie dans le répertoire des clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="3f863-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="3f863-121">Ceci est la valeur par défaut pour le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f863-121">This is the default for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>|  
|<span data-ttu-id="3f863-122">false</span><span class="sxs-lookup"><span data-stu-id="3f863-122">false</span></span>|<span data-ttu-id="3f863-123">Rétablit le comportement de démarrage des versions antérieures du .NET Framework, qui consiste à copier tous les fichiers au démarrage.</span><span class="sxs-lookup"><span data-stu-id="3f863-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f863-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3f863-124">Child Elements</span></span>  
 <span data-ttu-id="3f863-125">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3f863-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f863-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3f863-126">Parent Elements</span></span>  
  
|<span data-ttu-id="3f863-127">Élément</span><span class="sxs-lookup"><span data-stu-id="3f863-127">Element</span></span>|<span data-ttu-id="3f863-128">Description</span><span class="sxs-lookup"><span data-stu-id="3f863-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3f863-129">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f863-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3f863-130">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="3f863-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f863-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="3f863-131">Remarks</span></span>  
 <span data-ttu-id="3f863-132">En commençant par le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], les assemblys sont des clichés instantanés uniquement si leurs horodatages indiquent qu’ils ont été modifiés depuis leur dernière copie dans le répertoire des clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="3f863-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="3f863-133">Cela améliore les temps de démarrage pour de nombreuses applications qui utilisent les clichés instantanés, comme décrit dans [clichés instantanés d’assemblys](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="3f863-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="3f863-134">Les applications disposant d’un pourcentage élevé et la fréquence des mises à jour de l’assembly ne peuvent pas bénéficier de ce changement de comportement.</span><span class="sxs-lookup"><span data-stu-id="3f863-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="3f863-135">Dans ce cas, vous pouvez utiliser cet élément pour restaurer le comportement des versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f863-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f863-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f863-136">Example</span></span>  
 <span data-ttu-id="3f863-137">L’exemple suivant montre comment désactiver le comportement de démarrage par défaut de clichés instantanés dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]et de rétablir le comportement au démarrage des versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f863-137">The following example shows how to disable the default startup behavior of shadow copying in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f863-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f863-138">See Also</span></span>  
 [<span data-ttu-id="3f863-139">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="3f863-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="3f863-140">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="3f863-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="3f863-141">Clichés instantanés d'assemblys</span><span class="sxs-lookup"><span data-stu-id="3f863-141">Shadow Copying Assemblies</span></span>](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
