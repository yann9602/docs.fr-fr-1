---
title: "ICorProfilerCallback::JITCompilationStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a12ae3e33d5553ed99a5a26b8fc872f0d07de81e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="3c374-102">ICorProfilerCallback::JITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="3c374-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="3c374-103">Notifie le profileur que le compilateur (JIT) juste-à-temps a démarré à compiler une fonction.</span><span class="sxs-lookup"><span data-stu-id="3c374-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c374-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c374-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c374-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3c374-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3c374-106">[in] L’ID de la fonction pour laquelle la compilation démarre.</span><span class="sxs-lookup"><span data-stu-id="3c374-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="3c374-107">[in] Une valeur qui indique au profileur si un blocage affectera le fonctionnement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3c374-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="3c374-108">La valeur est `true` si blocage peut provoquer l’exécution pour attendre que le thread appelant à retourner à partir de ce rappel ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="3c374-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="3c374-109">Bien que la valeur de `true` ne nuise pas au runtime, elle peut fausser les résultats de profilage.</span><span class="sxs-lookup"><span data-stu-id="3c374-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c374-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="3c374-110">Remarks</span></span>  
 <span data-ttu-id="3c374-111">Il est possible de recevoir plusieurs paires de `JITCompilationStarted` et [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) appelle pour chaque fonction en raison du mode le runtime gère les constructeurs de classe.</span><span class="sxs-lookup"><span data-stu-id="3c374-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="3c374-112">Par exemple, le runtime commence la compilation JIT de la méthode A, mais le constructeur de classe pour la classe B doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="3c374-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="3c374-113">Par conséquent, le runtime JIT-compile le constructeur de classe B et l’exécute.</span><span class="sxs-lookup"><span data-stu-id="3c374-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="3c374-114">Lorsque le constructeur s’exécute, il effectue un appel à la méthode A, ce qui provoque la méthode A compilé juste-à nouveau.</span><span class="sxs-lookup"><span data-stu-id="3c374-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="3c374-115">Dans ce scénario, la première compilation JIT de la méthode A est interrompue.</span><span class="sxs-lookup"><span data-stu-id="3c374-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="3c374-116">Toutefois, les deux tentatives de compilation JIT de la méthode A sont signalés par les événements de compilation JIT.</span><span class="sxs-lookup"><span data-stu-id="3c374-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="3c374-117">Si le profileur doit remplacer le code de Microsoft intermediate language (MSIL) pour la méthode A en appelant le [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) (méthode), il doit le faire pour les deux `JITCompilationStarted` événements, mais il peut utiliser le même bloc MSIL pour les deux.</span><span class="sxs-lookup"><span data-stu-id="3c374-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="3c374-118">Les profileurs doivent prendre en charge de la séquence de rappels JIT dans les cas où deux threads effectuent simultanément des rappels.</span><span class="sxs-lookup"><span data-stu-id="3c374-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="3c374-119">Par exemple, le thread A appelle `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="3c374-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="3c374-120">Toutefois, avant le thread A appelle `JITCompilationFinished`, le thread B appelle [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) avec l’ID de la fonction à partir du thread de `JITCompilationStarted` rappel.</span><span class="sxs-lookup"><span data-stu-id="3c374-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="3c374-121">Il peut apparaître que l’ID de fonction n'est pas encore valide, car un appel à `JITCompilationFinished` n’a pas encore été reçu par le profileur.</span><span class="sxs-lookup"><span data-stu-id="3c374-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="3c374-122">Toutefois, dans un cas comme celui-ci, l’ID de fonction est valide.</span><span class="sxs-lookup"><span data-stu-id="3c374-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c374-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3c374-123">Requirements</span></span>  
 <span data-ttu-id="3c374-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c374-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c374-125">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3c374-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c374-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c374-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c374-127">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c374-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c374-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c374-128">See Also</span></span>  
 [<span data-ttu-id="3c374-129">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="3c374-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3c374-130">JITCompilationFinished (méthode)</span><span class="sxs-lookup"><span data-stu-id="3c374-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
