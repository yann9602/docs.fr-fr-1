---
title: "ICorProfilerCallback2::SurvivingReferences, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.SurvivingReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69bbc5a907a0c6061da877e93ccf1312ea67c826
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="4ad0a-102">ICorProfilerCallback2::SurvivingReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="4ad0a-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="4ad0a-103">Signale la disposition d’objets dans le tas suite à un garbage collection de non-compactage.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ad0a-104">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ad0a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4ad0a-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="4ad0a-106">[in] Nombre de blocs d’objets contigus qui ont survécu à la suite du garbage collection de non-compactage.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="4ad0a-107">Autrement dit, la valeur de `cSurvivingObjectIDRanges` est la taille des tableaux `objectIDRangeStart` et `cObjectIDRangeLength` qui stockent un `ObjectID` et une longueur, respectivement, pour chaque bloc d'objets.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="4ad0a-108">Les deux arguments suivants de `SurvivingReferences` sont des tableaux parallèles.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="4ad0a-109">En d'autres termes, `objectIDRangeStart` et `cObjectIDRangeLength` concernent le même bloc d'objets contigus.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="4ad0a-110">[in] Tableau de valeurs `ObjectID`, chacune d'elles étant l'adresse de début d'un bloc d'objets actifs contigus dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="4ad0a-111">[in] Tableau d'entiers, chacun d'eux correspondant à la taille d'un bloc survivant d'objets contigus dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="4ad0a-112">Une taille est spécifiée pour chaque bloc référencé dans le tableau `objectIDRangeStart`.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ad0a-113">Notes</span><span class="sxs-lookup"><span data-stu-id="4ad0a-113">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4ad0a-114">Cette méthode signale les tailles en tant que `MAX_ULONG` pour les objets qui sont supérieurs à 4 Go sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="4ad0a-115">Pour les objets qui sont supérieurs à 4 Go, utilisez le [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="4ad0a-116">Les éléments des tableaux `objectIDRangeStart` et `cObjectIDRangeLength` doivent être interprétés comme suit pour déterminer si un objet a survécu au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="4ad0a-117">Supposons qu'une valeur `ObjectID` (`ObjectID`) se trouve dans la plage suivante :</span><span class="sxs-lookup"><span data-stu-id="4ad0a-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="4ad0a-118">Pour toute valeur de `i` qui se trouve dans la plage suivante, l'objet a survécu au garbage collection :</span><span class="sxs-lookup"><span data-stu-id="4ad0a-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="4ad0a-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="4ad0a-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="4ad0a-120">Un garbage collection de non-compactage libère la mémoire occupée par des objets « morts », mais ne compacte pas cet espace libéré.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="4ad0a-121">Par conséquent, la mémoire est retournée au tas, mais aucun objet « actif » n'est déplacé.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="4ad0a-122">Le Common Language Runtime (CLR) appelle `SurvivingReferences` pour les garbage collection de non-compactage.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="4ad0a-123">Pour le garbage collection de compactage, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) est appelée à la place.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="4ad0a-124">Un garbage collection unique peut être de compactage pour une génération et de non-compactage pour une autre.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="4ad0a-125">Pour un garbage collection de n'importe quelle génération, le profileur reçoit un rappel `SurvivingReferences` ou un rappel `MovedReferences`, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="4ad0a-126">Plusieurs rappels `SurvivingReferences` peuvent être reçus pendant un garbage collection particulier, en raison de la mise en mémoire tampon interne limitée, du signalement de plusieurs threads lors d'un garbage collection de serveur, etc.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="4ad0a-127">En cas de rappels multiples pendant un garbage collection, les informations se cumulent. Ainsi, toutes les références qui sont signalées dans un rappel `SurvivingReferences` survivent au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4ad0a-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ad0a-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4ad0a-128">Requirements</span></span>  
 <span data-ttu-id="4ad0a-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ad0a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ad0a-130">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4ad0a-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ad0a-131">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ad0a-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ad0a-132">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ad0a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad0a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ad0a-133">See Also</span></span>  
 [<span data-ttu-id="4ad0a-134">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="4ad0a-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="4ad0a-135">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="4ad0a-135">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="4ad0a-136">SurvivingReferences2, méthode</span><span class="sxs-lookup"><span data-stu-id="4ad0a-136">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
