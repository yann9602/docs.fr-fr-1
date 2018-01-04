---
title: "ICorProfilerCallback::JITCachedFunctionSearchStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2208a1a1637b3bb8dd7d7963ab806aeae7921dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="8b15d-102">ICorProfilerCallback::JITCachedFunctionSearchStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="8b15d-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="8b15d-103">Notifie le profileur qu’une recherche a démarré pour une fonction qui a été compilée précédemment à l’aide du Générateur d’images natives (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="8b15d-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b15d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b15d-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b15d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8b15d-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="8b15d-106">[in] L’ID de la fonction pour laquelle la recherche est effectuée.</span><span class="sxs-lookup"><span data-stu-id="8b15d-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="8b15d-107">[out] `true` si le moteur d’exécution doit utiliser la version mise en cache d’une fonction (si disponible) ; sinon `false`.</span><span class="sxs-lookup"><span data-stu-id="8b15d-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="8b15d-108">Si la valeur est `false`, le moteur d’exécution JIT-compile la fonction au lieu d’utiliser une version qui n’est pas compilé par JIT.</span><span class="sxs-lookup"><span data-stu-id="8b15d-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b15d-109">Notes</span><span class="sxs-lookup"><span data-stu-id="8b15d-109">Remarks</span></span>  
 <span data-ttu-id="8b15d-110">Dans le .NET Framework version 2.0, le `JITCachedFunctionSearchStarted` et [ICorProfilerCallback::JITCachedFunctionSearchFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) rappels ne sont pas effectués pour toutes les fonctions dans les images NGen normales.</span><span class="sxs-lookup"><span data-stu-id="8b15d-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="8b15d-111">Seules les images NGen optimisées pour un profil généreront des rappels pour toutes les fonctions dans l’image.</span><span class="sxs-lookup"><span data-stu-id="8b15d-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="8b15d-112">Toutefois, en raison de la charge supplémentaire, un profileur doit demander les images NGen optimisées sur le profileur uniquement si elle a l’intention d’utiliser ces rappels pour forcer une fonction compilée juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="8b15d-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="8b15d-113">Sinon, le profileur doit utiliser une stratégie minimale pour la collecte des informations sur la fonction.</span><span class="sxs-lookup"><span data-stu-id="8b15d-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="8b15d-114">Les profileurs doivent prendre en charge les cas où plusieurs threads d’une application profilée appellent simultanément la même méthode.</span><span class="sxs-lookup"><span data-stu-id="8b15d-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="8b15d-115">Par exemple, le thread A appelle `JITCachedFunctionSearchStarted` et le profileur répond en affectant *pbUseCachedFunction*sur FALSE pour forcer la compilation JIT.</span><span class="sxs-lookup"><span data-stu-id="8b15d-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="8b15d-116">Thread, puis appelle [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) et [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="8b15d-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="8b15d-117">Maintenant, le thread B appelle `JITCachedFunctionSearchStarted` pour la même fonction.</span><span class="sxs-lookup"><span data-stu-id="8b15d-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="8b15d-118">Bien que le profileur a déclaré son intention de la fonction de la compilation JIT, le profileur reçoit le deuxième rappel, car le thread B envoie le rappel avant que le profileur n’a répondu à l’appel du thread de A à `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="8b15d-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="8b15d-119">L’ordre dans lequel les threads effectuent des appels dépend de la façon dont les threads sont planifiés.</span><span class="sxs-lookup"><span data-stu-id="8b15d-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="8b15d-120">Lorsque le profileur reçoit des rappels en double, il doit définir la valeur référencée par `pbUseCachedFunction` à la même valeur pour tous les rappels en double.</span><span class="sxs-lookup"><span data-stu-id="8b15d-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="8b15d-121">Autrement dit, lorsque `JITCachedFunctionSearchStarted` est appelée plusieurs fois avec le même `functionId` valeur, le profileur doit répondre de la même chaque fois.</span><span class="sxs-lookup"><span data-stu-id="8b15d-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b15d-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8b15d-122">Requirements</span></span>  
 <span data-ttu-id="8b15d-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b15d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b15d-124">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b15d-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b15d-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b15d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b15d-126">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b15d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b15d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b15d-127">See Also</span></span>  
 [<span data-ttu-id="8b15d-128">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="8b15d-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
