---
title: "ICorProfilerInfo2::SetEnterLeaveFunctionHooks2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bea9be4db2730a67485ef9a504bbc69c096e76c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="15056-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="15056-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="15056-103">Spécifie les fonctions implémentées par le profileur à être appelée sur les versions mises à jour des « entrer », « quitter » et « tailcall » de fonctions managées.</span><span class="sxs-lookup"><span data-stu-id="15056-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15056-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15056-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15056-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="15056-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="15056-106">[in] Un pointeur vers l’implémentation à utiliser comme le [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="15056-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="15056-107">[in] Un pointeur vers l’implémentation à utiliser comme le [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="15056-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="15056-108">[in] Un pointeur vers l’implémentation à utiliser comme le [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="15056-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15056-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="15056-109">Remarks</span></span>  
 <span data-ttu-id="15056-110">Le `SetEnterLeaveFunctionHooks2` méthode est similaire à la [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="15056-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="15056-111">Utilisez la première pour spécifier les fonctions à utiliser comme les versions plus récentes de l’entrée/leave/tailcall et ce dernier pour spécifier les fonctions à utiliser comme les versions précédentes des rappels entrée/leave/tailcall.</span><span class="sxs-lookup"><span data-stu-id="15056-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="15056-112">Qu’un seul jeu de rappels peut être actif à la fois.</span><span class="sxs-lookup"><span data-stu-id="15056-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="15056-113">Par conséquent, si un profileur appelle `ICorProfilerInfo::SetEnterLeaveFunctionHooks` et `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="15056-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="15056-114">Le `SetEnterLeaveFunctionHooks2` méthode peut être appelée uniquement à partir du profileur [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="15056-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15056-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="15056-115">Requirements</span></span>  
 <span data-ttu-id="15056-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15056-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15056-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="15056-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15056-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15056-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15056-119">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15056-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15056-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15056-120">See Also</span></span>  
 [<span data-ttu-id="15056-121">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="15056-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="15056-122">ICorProfilerInfo2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="15056-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
