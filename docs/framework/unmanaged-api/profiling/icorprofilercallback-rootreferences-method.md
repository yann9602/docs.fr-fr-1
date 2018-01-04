---
title: "ICorProfilerCallback::RootReferences, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RootReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd057538450deeb46a72178c725103e04a8dd126
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="59b37-102">ICorProfilerCallback::RootReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="59b37-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="59b37-103">Notifie le profileur avec les informations concernant les références racine après le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="59b37-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59b37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59b37-104">Syntax</span></span>  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59b37-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="59b37-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="59b37-106">[in] Le nombre de références dans le `rootRefIds` tableau.</span><span class="sxs-lookup"><span data-stu-id="59b37-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="59b37-107">[in] Tableau d’ID d’objet qui font référence à un objet statique ou un objet sur la pile.</span><span class="sxs-lookup"><span data-stu-id="59b37-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59b37-108">Notes</span><span class="sxs-lookup"><span data-stu-id="59b37-108">Remarks</span></span>  
 <span data-ttu-id="59b37-109">Les deux `RootReferences` et [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) sont appelées pour notifier le profileur.</span><span class="sxs-lookup"><span data-stu-id="59b37-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="59b37-110">Les profileurs implémentera normalement un ou l’autre, mais pas les deux, car les informations passées dans `RootReferences2` est un sur-ensemble de celles passées dans `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="59b37-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="59b37-111">Il est possible pour le `rootRefIds` tableau destiné à contenir un objet null.</span><span class="sxs-lookup"><span data-stu-id="59b37-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="59b37-112">Par exemple, toutes les références d’objet déclarées sur la pile sont traités comme des racines par le garbage collector et seront toujours signalées.</span><span class="sxs-lookup"><span data-stu-id="59b37-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="59b37-113">Les ID d’objet retourné par `RootReferences` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être occupé à déplacer les objets des anciennes adresses vers de nouvelles adresses.</span><span class="sxs-lookup"><span data-stu-id="59b37-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="59b37-114">Par conséquent, les profileurs ne doivent pas essayer d’inspecter les objets pendant un `RootReferences` appeler.</span><span class="sxs-lookup"><span data-stu-id="59b37-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="59b37-115">Lorsque [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) est appelée, tous les objets ont été déplacés vers leurs nouveaux emplacements et peuvent être inspectés sans risque.</span><span class="sxs-lookup"><span data-stu-id="59b37-115">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59b37-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="59b37-116">Requirements</span></span>  
 <span data-ttu-id="59b37-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59b37-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59b37-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="59b37-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="59b37-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59b37-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59b37-120">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59b37-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b37-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59b37-121">See Also</span></span>  
 [<span data-ttu-id="59b37-122">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="59b37-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
