---
title: "ICorProfilerCallback5::ConditionalWeakTableElementReferences, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback5.ConditionalWeakTableReferences
api_location: Mscorwks.dll
api_type: COM
f1_keywords: CondiitonalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cfe86ac7d0cd5b4a5c6adb9f12ffe9577b6e611
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="51921-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="51921-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>
<span data-ttu-id="51921-103">Identifie la fermeture transitive des objets référencés par ces racines via les références des champs des membres directs et via les dépendances de `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="51921-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51921-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51921-104">Syntax</span></span>  
  
```  
HRESULT ConditionalWeakTableElementReferences(     [in]                     ULONG    cRootRefs,     [in, size_is(cRootRefs)] ObjectID keyRefIds[],     [in, size_is(cRootRefs)] ObjectID valueRefIds[],     [in, size_is(cRootRefs)] GCHandleID rootIds[]);};  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51921-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51921-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="51921-106">[en entrée] Le nombre d'éléments dans les tableaux `keyRefIds`, `valueRefIds` et `rootIds`.</span><span class="sxs-lookup"><span data-stu-id="51921-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>  
  
 `keyRefIds`  
 <span data-ttu-id="51921-107">[en entrée] Un tableau d'ID d'objets, chacun contenant l'`ObjectID` pour l'élément principal de la paire de handles dépendants.</span><span class="sxs-lookup"><span data-stu-id="51921-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>  
  
 `valueRefIds`  
 <span data-ttu-id="51921-108">[en entrée] Un tableau d'ID d'objets, chacun contenant l'`ObjectID` pour l'élément secondaire de la paire de handles dépendants.</span><span class="sxs-lookup"><span data-stu-id="51921-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="51921-109">(`keyRefIds[i]` conserve `valueRefIds[i]` actif.)</span><span class="sxs-lookup"><span data-stu-id="51921-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>  
  
 `rootIds`  
 <span data-ttu-id="51921-110">[en entrée] Un tableau de valeurs de `GCHandleID` qui pointent vers un entier contenant des informations supplémentaires sur la racine de récupération de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="51921-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>  
  
 <span data-ttu-id="51921-111">Aucune des valeurs d'`ObjectID` retournées par la méthode `ConditionalWeakTableElementReferences` ne sont valides pendant le rappel lui-même, car le récupérateur de mémoire peut être occupé à déplacer des objets depuis des anciens emplacements vers des nouveaux.</span><span class="sxs-lookup"><span data-stu-id="51921-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="51921-112">Les profileurs ne doivent donc pas essayer d'inspecter des objets pendant un appel de `ConditionalWeakTableElementReferences`.</span><span class="sxs-lookup"><span data-stu-id="51921-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="51921-113">Quand l'état est `GarbageCollectionFinished`, tous les objets ont été déplacés à leur nouvel emplacement et une inspection peut être effectuée.</span><span class="sxs-lookup"><span data-stu-id="51921-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51921-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="51921-114">Example</span></span>  
 <span data-ttu-id="51921-115">L’exemple de code suivant montre comment implémenter [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) et utiliser cette méthode.</span><span class="sxs-lookup"><span data-stu-id="51921-115">The following code example demonstrates how to implement [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) and use this method.</span></span>  
  
```  
HRESULT Callback5Impl::ConditionalWeakTableElementReferences(  
    ULONG      cRootRefs,  
    ObjectID   keyRefIds[],  
    ObjectID   valueRefIds[],  
    GCHandleID rootIds[])  
{  
    printf("Callback5Impl::ConditionalWeakTableElementReferences called\n");  
    for (unsigned int i = 0; i < cRootRefs; ++i)  
    {  
        // Save dependency to XML for later retrieval  
        PersistDependencyToXml(rootIds[i], keyRefIds[i], valueRefIds[i]);  
        // or store dependency to an internal map  
        m_cwt_deps->add_dep(rootIds[i], keyRefIds[i], valueRefIds[i]);  
        // or add arc to object graph  
        m_obj_graph->add_arc(keyRefIds[i], valueRefIds[i], rootIds[i]);  
    }  
    return S_OK;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="51921-116">Notes</span><span class="sxs-lookup"><span data-stu-id="51921-116">Remarks</span></span>  
 <span data-ttu-id="51921-117">Un profileur pour le [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] ou ultérieur implémente la [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) interface et enregistre les dépendances spécifiées par le `ConditionalWeakTableElementReferences` (méthode).</span><span class="sxs-lookup"><span data-stu-id="51921-117">A profiler for the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] or later versions implements the [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="51921-118">`ICorProfilerCallback5`fournit l’ensemble complet des dépendances entre les objets actifs représentés par `ConditionalWeakTable` entrées.</span><span class="sxs-lookup"><span data-stu-id="51921-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="51921-119">Ces dépendances et le membre spécifiés par les références de champ la [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) méthode activer un profileur managé générer le graphique complet des objets actifs.</span><span class="sxs-lookup"><span data-stu-id="51921-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51921-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="51921-120">Requirements</span></span>  
 <span data-ttu-id="51921-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51921-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51921-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="51921-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="51921-123">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51921-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51921-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51921-124">See Also</span></span>  
 [<span data-ttu-id="51921-125">ICorProfilerCallback5, interface</span><span class="sxs-lookup"><span data-stu-id="51921-125">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)
