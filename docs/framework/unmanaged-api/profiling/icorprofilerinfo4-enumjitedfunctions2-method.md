---
title: "ICorProfilerInfo4::EnumJITedFunctions2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.EnumJITedFunctions2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9b9c8739a8ab47b4e24dba1b15c228d2800290d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="5ece2-102">ICorProfilerInfo4::EnumJITedFunctions2, méthode</span><span class="sxs-lookup"><span data-stu-id="5ece2-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="5ece2-103">Retourne un énumérateur pour toutes les fonctions qui étaient précédemment compilé par JIT et recompilée juste.</span><span class="sxs-lookup"><span data-stu-id="5ece2-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="5ece2-104">Cette méthode remplace la [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) (méthode), qui n’énumère pas les ID recompilé juste-.</span><span class="sxs-lookup"><span data-stu-id="5ece2-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ece2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ece2-105">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ece2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5ece2-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="5ece2-107">[out] Un pointeur vers le [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) énumérateur.</span><span class="sxs-lookup"><span data-stu-id="5ece2-107">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ece2-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="5ece2-108">Remarks</span></span>  
 <span data-ttu-id="5ece2-109">Cette méthode peut se chevaucher avec `JITCompilation` rappels tels que les [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5ece2-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="5ece2-110">L’énumération retournée inclut des valeurs pour le `COR_PRF_FUNCTION::reJitId` champ.</span><span class="sxs-lookup"><span data-stu-id="5ece2-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="5ece2-111">Le [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) (méthode), qui remplace de cette méthode, n’énumère pas recompilée juste-ID, car le `COR_PRF_FUNCTION::reJitId` champ est toujours défini sur 0.</span><span class="sxs-lookup"><span data-stu-id="5ece2-111">The [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="5ece2-112">Le `ICorProfilerInfo4::EnumJITedFunctions` méthode énumère recompilée juste-ID, car le `COR_PRF_FUNCTION::reJitId` champ est correctement défini.</span><span class="sxs-lookup"><span data-stu-id="5ece2-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="5ece2-113">Notez que la [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) méthode peut déclencher un garbage collection, tandis que [ICorProfilerInfo3::EnumJITedFunctions, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) ne seront pas.</span><span class="sxs-lookup"><span data-stu-id="5ece2-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="5ece2-114">Pour plus d’informations, consultez [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="5ece2-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ece2-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5ece2-115">Requirements</span></span>  
 <span data-ttu-id="5ece2-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ece2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ece2-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ece2-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ece2-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ece2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ece2-119">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ece2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ece2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ece2-120">See Also</span></span>  
 [<span data-ttu-id="5ece2-121">EnumJITedFunctions (méthode)</span><span class="sxs-lookup"><span data-stu-id="5ece2-121">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)  
 [<span data-ttu-id="5ece2-122">Icorprofilerinfo4, Interface</span><span class="sxs-lookup"><span data-stu-id="5ece2-122">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="5ece2-123">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="5ece2-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="5ece2-124">Profilage</span><span class="sxs-lookup"><span data-stu-id="5ece2-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
