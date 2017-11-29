---
title: "ICorProfilerCallback::RuntimeThreadSuspended, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeThreadSuspended
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4d2ab0244e898a60db8fe392ccbd8c0ebfd5523
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="079e2-102">ICorProfilerCallback::RuntimeThreadSuspended, méthode</span><span class="sxs-lookup"><span data-stu-id="079e2-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="079e2-103">Notifie le profileur que le thread spécifié a été suspendu ou est sur le point d’être suspendue.</span><span class="sxs-lookup"><span data-stu-id="079e2-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="079e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="079e2-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="079e2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="079e2-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="079e2-106">[in] L’ID du thread qui a été suspendu.</span><span class="sxs-lookup"><span data-stu-id="079e2-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="079e2-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="079e2-107">Remarks</span></span>  
 <span data-ttu-id="079e2-108">Le `RuntimeThreadSuspended` notification peut se produire à tout moment entre le [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) et associé [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) rappels.</span><span class="sxs-lookup"><span data-stu-id="079e2-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="079e2-109">Les notifications qui se produisent entre [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) et `RuntimeResumeStarted` pour les threads qui étaient exécutés dans du code non managé et ont été suspendus lors de l’entrée à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="079e2-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="079e2-110">En règle générale, ce rappel se produit juste après la suspension d’un thread.</span><span class="sxs-lookup"><span data-stu-id="079e2-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="079e2-111">Toutefois, si le thread en cours d’exécution (le thread qui a appelé ce rappel) est celui qui est suspendu, ce rappel se produit juste avant que le thread est suspendu.</span><span class="sxs-lookup"><span data-stu-id="079e2-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="079e2-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="079e2-112">Requirements</span></span>  
 <span data-ttu-id="079e2-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="079e2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="079e2-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="079e2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="079e2-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="079e2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="079e2-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="079e2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="079e2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="079e2-117">See Also</span></span>  
 [<span data-ttu-id="079e2-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="079e2-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="079e2-119">RuntimeThreadResumed (méthode)</span><span class="sxs-lookup"><span data-stu-id="079e2-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
