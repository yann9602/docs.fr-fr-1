---
title: "ICorProfilerCallback2::RootReferences2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.RootReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8a0b2e23ba586e7a20ed11de6433b2d87cbe7219
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="4e206-102">ICorProfilerCallback2::RootReferences2, méthode</span><span class="sxs-lookup"><span data-stu-id="4e206-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="4e206-103">Notifie le profileur concernant les références racine après qu’un garbage collection s’est produite.</span><span class="sxs-lookup"><span data-stu-id="4e206-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="4e206-104">Cette méthode est une extension de la [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="4e206-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e206-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e206-105">Syntax</span></span>  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e206-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4e206-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="4e206-107">[in] Le nombre d’éléments dans le `rootRefIds`, `rootKinds`, `rootFlags`, et `rootIds` tableaux.</span><span class="sxs-lookup"><span data-stu-id="4e206-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="4e206-108">[in] Tableau d’ID d’objet, dont chacun fait référence à un objet statique ou un objet sur la pile.</span><span class="sxs-lookup"><span data-stu-id="4e206-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="4e206-109">Les éléments dans le `rootKinds` tableau fournissent des informations pour classer les éléments correspondants dans le `rootRefIds` tableau.</span><span class="sxs-lookup"><span data-stu-id="4e206-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="4e206-110">[in] Un tableau de [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) valeurs qui indiquent le type de la racine de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4e206-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="4e206-111">[in] Un tableau de [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) valeurs qui décrivent les propriétés d’une racine de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4e206-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="4e206-112">[in] Un tableau de valeurs UINT_PTR qui pointent vers un entier qui contient des informations supplémentaires sur la racine de garbage collection, selon la valeur de le `rootKinds` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e206-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="4e206-113">Si le type de la racine est une pile, l’ID de la racine est pour la fonction qui contient la variable.</span><span class="sxs-lookup"><span data-stu-id="4e206-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="4e206-114">Si cet ID racine est 0, la fonction est une fonction sans nom qui est interne au CLR.</span><span class="sxs-lookup"><span data-stu-id="4e206-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="4e206-115">Si le type de la racine est un handle, l’ID de la racine est pour le handle de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4e206-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="4e206-116">Pour les autres types racine, l’ID est une valeur opaque et doit être ignorée.</span><span class="sxs-lookup"><span data-stu-id="4e206-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e206-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="4e206-117">Remarks</span></span>  
 <span data-ttu-id="4e206-118">Le `rootRefIds`, `rootKinds`, `rootFlags`, et `rootIds` tableaux sont des tableaux parallèles.</span><span class="sxs-lookup"><span data-stu-id="4e206-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="4e206-119">Autrement dit, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, et `rootIds[i]` concernent la même racine.</span><span class="sxs-lookup"><span data-stu-id="4e206-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="4e206-120">Les deux `RootReferences` et `RootReferences2` sont appelées pour notifier le profileur.</span><span class="sxs-lookup"><span data-stu-id="4e206-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="4e206-121">Les profileurs normalement implémentera une méthode ou l’autre, mais pas les deux, car les informations passées dans `RootReferences2` est un sur-ensemble de celles passées dans `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="4e206-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="4e206-122">Il est possible pour les entrées dans `rootRefIds` à zéro, ce qui implique que la référence racine correspondante est null et ne fait pas référence à un objet sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="4e206-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="4e206-123">Les ID d’objet retourné par `RootReferences2` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être occupé à déplacer les objets des anciennes adresses vers de nouvelles adresses.</span><span class="sxs-lookup"><span data-stu-id="4e206-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="4e206-124">Les profileurs ne doivent donc pas essayer d'inspecter des objets pendant un appel de `RootReferences2`.</span><span class="sxs-lookup"><span data-stu-id="4e206-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="4e206-125">Lorsque [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) est appelée, tous les objets ont été déplacés vers leurs nouveaux emplacements et peuvent être inspectés sans risque.</span><span class="sxs-lookup"><span data-stu-id="4e206-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e206-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4e206-126">Requirements</span></span>  
 <span data-ttu-id="4e206-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e206-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e206-128">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4e206-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e206-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e206-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e206-130">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e206-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e206-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e206-131">See Also</span></span>  
 [<span data-ttu-id="4e206-132">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="4e206-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="4e206-133">ICorProfilerCallback2, Interface</span><span class="sxs-lookup"><span data-stu-id="4e206-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
