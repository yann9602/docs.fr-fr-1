---
title: "Énumérations de profilage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84ac67b35bdbf686edb2fa35cc651aad4c19516b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-enumerations"></a><span data-ttu-id="f2465-102">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="f2465-102">Profiling Enumerations</span></span>
<span data-ttu-id="f2465-103">Cette section décrit les énumérations non managées utilisées par l'API de profilage.</span><span class="sxs-lookup"><span data-stu-id="f2465-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2465-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f2465-104">In This Section</span></span>  
 [<span data-ttu-id="f2465-105">COR_PRF_CLAUSE_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="f2465-106">Indique le type de clause d'exception où le code vient d'entrer ou qu'il vient de quitter.</span><span class="sxs-lookup"><span data-stu-id="f2465-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="f2465-107">COR_PRF_CODEGEN_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="f2465-108">Définit les indicateurs de génération de code qui peuvent être définies avec la [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="f2465-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="f2465-109">COR_PRF_FINALIZER_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="f2465-110">Décrit le finaliseur pour un objet.</span><span class="sxs-lookup"><span data-stu-id="f2465-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="f2465-111">COR_PRF_GC_GENERATION, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-111">COR_PRF_GC_GENERATION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="f2465-112">Identifie une génération de récupération de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f2465-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="f2465-113">COR_PRF_GC_REASON, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-113">COR_PRF_GC_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="f2465-114">Indique la raison pour laquelle une récupération de mémoire se produit.</span><span class="sxs-lookup"><span data-stu-id="f2465-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="f2465-115">COR_PRF_GC_ROOT_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="f2465-116">Indique les propriétés d'une racine de récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f2465-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="f2465-117">COR_PRF_GC_ROOT_KIND, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="f2465-118">Indique le type de racine de garbage collector qui est exposé par le [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="f2465-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="f2465-119">COR_PRF_MODULE_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="f2465-120">Fournit des indicateurs en plus de celles disponibles dans le [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) énumération que le profileur peut spécifier à la [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) méthode lors de son chargement.</span><span class="sxs-lookup"><span data-stu-id="f2465-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="f2465-121">COR_PRF_JIT_CACHE, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-121">COR_PRF_JIT_CACHE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="f2465-122">Indique le résultat de la recherche d'une fonction mise en cache.</span><span class="sxs-lookup"><span data-stu-id="f2465-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="f2465-123">COR_PRF_MISC, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-123">COR_PRF_MISC Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 <span data-ttu-id="f2465-124">Contient des valeurs de constante qui spécifient des identificateurs spéciaux.</span><span class="sxs-lookup"><span data-stu-id="f2465-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="f2465-125">COR_PRF_MODULE_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="f2465-126">Spécifie les propriétés d'un module.</span><span class="sxs-lookup"><span data-stu-id="f2465-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="f2465-127">COR_PRF_MONITOR, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="f2465-128">Contient des valeurs utilisées pour spécifier un comportement, des fonctionnalités ou des événements auxquels le profileur veut s'abonner.</span><span class="sxs-lookup"><span data-stu-id="f2465-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="f2465-129">COR_PRF_RUNTIME_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="f2465-130">Contient des valeurs qui indiquent la version du CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="f2465-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="f2465-131">COR_PRF_SNAPSHOT_INFO, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="f2465-132">Spécifie la quantité de données à passer en retour avec une capture instantanée de la pile dans chaque appel à la fonction `StackSnapshotCallback` du profileur.</span><span class="sxs-lookup"><span data-stu-id="f2465-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="f2465-133">COR_PRF_STATIC_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="f2465-134">Indique si un champ est statique et si oui, la qualité statique qui s'y applique.</span><span class="sxs-lookup"><span data-stu-id="f2465-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="f2465-135">COR_PRF_SUSPEND_REASON, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="f2465-136">Indique la raison pour laquelle le runtime a été suspendu.</span><span class="sxs-lookup"><span data-stu-id="f2465-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="f2465-137">COR_PRF_TRANSITION_REASON, énumération</span><span class="sxs-lookup"><span data-stu-id="f2465-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="f2465-138">Indique la raison d'une transition de code managé en code non managé, ou l'inverse.</span><span class="sxs-lookup"><span data-stu-id="f2465-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f2465-139">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="f2465-139">Related Sections</span></span>  
 [<span data-ttu-id="f2465-140">Vue d’ensemble du profilage</span><span class="sxs-lookup"><span data-stu-id="f2465-140">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="f2465-141">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="f2465-141">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="f2465-142">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="f2465-142">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="f2465-143">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="f2465-143">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
