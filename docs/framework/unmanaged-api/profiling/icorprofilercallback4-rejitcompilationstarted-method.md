---
title: "ICorProfilerCallback4::ReJITCompilationStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 903db06089f7c68843b503c94483087ff9fce636
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="8fe81-102">ICorProfilerCallback4::ReJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="8fe81-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="8fe81-103">Notifie le profileur que le compilateur (JIT) juste-à-temps a démarré recompiler une fonction.</span><span class="sxs-lookup"><span data-stu-id="8fe81-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fe81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fe81-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationStarted(    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fe81-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8fe81-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="8fe81-106">[in] L’ID de la fonction que le compilateur JIT a commencé à recompiler.</span><span class="sxs-lookup"><span data-stu-id="8fe81-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="8fe81-107">[in] L’ID de la recompilation de la nouvelle version de la fonction.</span><span class="sxs-lookup"><span data-stu-id="8fe81-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="8fe81-108">[in] `true` pour indiquer que le blocage peut entraîner l’exécution pour attendre que le thread appelant à retourner à partir de ce rappel ; `false` pour indiquer que le blocage n’affecte pas le fonctionnement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8fe81-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="8fe81-109">La valeur `true` ne nuise pas au runtime, mais peut affecter les résultats de profilage.</span><span class="sxs-lookup"><span data-stu-id="8fe81-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fe81-110">Notes</span><span class="sxs-lookup"><span data-stu-id="8fe81-110">Remarks</span></span>  
 <span data-ttu-id="8fe81-111">Il est possible de recevoir plusieurs paires de `ReJITCompilationStarted` et [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) appels de méthode pour chaque fonction en raison du mode le runtime gère les constructeurs de classe.</span><span class="sxs-lookup"><span data-stu-id="8fe81-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="8fe81-112">Par exemple, le runtime commence à recompiler la méthode A, mais le constructeur de classe pour la classe B doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="8fe81-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="8fe81-113">Par conséquent, le runtime recompile le constructeur de classe B et l’exécute.</span><span class="sxs-lookup"><span data-stu-id="8fe81-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="8fe81-114">Alors que le constructeur s’exécute, il effectue un appel à la méthode A, ce qui provoque la méthode A de nouveau être recompilée.</span><span class="sxs-lookup"><span data-stu-id="8fe81-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="8fe81-115">Dans ce scénario, la première recompilation de la méthode A est interrompue.</span><span class="sxs-lookup"><span data-stu-id="8fe81-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="8fe81-116">Toutefois, les deux tente de recompiler la méthode A sont signalé avec des événements de recompilation JIT.</span><span class="sxs-lookup"><span data-stu-id="8fe81-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="8fe81-117">Les profileurs doivent prendre en charge la séquence des rappels de recompilation JIT dans les cas où deux threads effectuent simultanément des rappels.</span><span class="sxs-lookup"><span data-stu-id="8fe81-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="8fe81-118">Par exemple, le thread A appelle `ReJITCompilationStarted`; Toutefois, avant que le thread A appelle [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), le thread B appelle [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) avec l’ID de fonction à partir de la `ReJITCompilationStarted` rappel pour le thread A. Il peut apparaître que l’ID de fonction n'est pas encore valide, car un appel à [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) n’a pas encore été reçu par le profileur.</span><span class="sxs-lookup"><span data-stu-id="8fe81-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="8fe81-119">Toutefois, dans ce cas, l’ID de fonction est valide.</span><span class="sxs-lookup"><span data-stu-id="8fe81-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fe81-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8fe81-120">Requirements</span></span>  
 <span data-ttu-id="8fe81-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fe81-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fe81-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8fe81-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8fe81-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fe81-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fe81-124">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fe81-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe81-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fe81-125">See Also</span></span>  
 [<span data-ttu-id="8fe81-126">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="8fe81-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8fe81-127">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="8fe81-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="8fe81-128">JITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="8fe81-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [<span data-ttu-id="8fe81-129">ReJITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="8fe81-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
