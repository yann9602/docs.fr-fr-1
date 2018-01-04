---
title: "ICorProfilerCallback::ObjectReferences, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30b8f6b5f424ff81ace36baa8d2ae39e0a2f1d1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="fb1a6-102">ICorProfilerCallback::ObjectReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="fb1a6-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="fb1a6-103">Notifie le profileur sur les objets en mémoire qui sont référencés par l’objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="fb1a6-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb1a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb1a6-104">Syntax</span></span>  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb1a6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fb1a6-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="fb1a6-106">[in] L’ID de l’objet qui fait référence à des objets.</span><span class="sxs-lookup"><span data-stu-id="fb1a6-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="fb1a6-107">[in] L’ID de l’objet spécifié est une instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="fb1a6-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="fb1a6-108">[in] Le nombre d’objets référencés par l’objet spécifié (autrement dit, le nombre d’éléments dans le `objectRefIds` tableau).</span><span class="sxs-lookup"><span data-stu-id="fb1a6-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="fb1a6-109">[in] Un tableau d’ID d’objets qui sont référencés par `objectId`.</span><span class="sxs-lookup"><span data-stu-id="fb1a6-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb1a6-110">Notes</span><span class="sxs-lookup"><span data-stu-id="fb1a6-110">Remarks</span></span>  
 <span data-ttu-id="fb1a6-111">Le `ObjectReferences` méthode est appelée pour chaque objet reste dans le tas après l’exécution d’un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="fb1a6-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="fb1a6-112">Si le profileur retourne une erreur à partir de ce rappel, les services de profilage cessent d’appeler ce rappel jusqu’au garbage collection suivant.</span><span class="sxs-lookup"><span data-stu-id="fb1a6-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="fb1a6-113">Le `ObjectReferences` rappel peut être utilisé conjointement avec la [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) rappel pour créer un graphique de référence d’objet complet pour le runtime.</span><span class="sxs-lookup"><span data-stu-id="fb1a6-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="fb1a6-114">Le common language runtime (CLR) garantit que chaque référence d’objet est signalé qu’une seule fois par le `ObjectReferences` (méthode).</span><span class="sxs-lookup"><span data-stu-id="fb1a6-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="fb1a6-115">Les ID d’objet retourné par `ObjectReferences` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être occupé à déplacer des objets.</span><span class="sxs-lookup"><span data-stu-id="fb1a6-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="fb1a6-116">Par conséquent, les profileurs ne doivent pas essayer d’inspecter les objets pendant un `ObjectReferences` appeler.</span><span class="sxs-lookup"><span data-stu-id="fb1a6-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="fb1a6-117">Lorsque [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) est appelée, le garbage collection est terminé et l’inspection peut être effectuée en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="fb1a6-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="fb1a6-118">Une valeur null `ClassId` indique que `objectId` a un type qui est déchargement.</span><span class="sxs-lookup"><span data-stu-id="fb1a6-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb1a6-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fb1a6-119">Requirements</span></span>  
 <span data-ttu-id="fb1a6-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb1a6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb1a6-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb1a6-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb1a6-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb1a6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb1a6-123">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb1a6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb1a6-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb1a6-124">See Also</span></span>  
 [<span data-ttu-id="fb1a6-125">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="fb1a6-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
