---
title: "ICorProfilerCallback::JITCachedFunctionSearchFinished, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ffbe331399334d179cf8325e7d9e6773b5bf7012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="f0c87-102">ICorProfilerCallback::JITCachedFunctionSearchFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="f0c87-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="f0c87-103">Notifie le profileur qu’une recherche est terminée pour une fonction qui a été compilée précédemment à l’aide du Générateur d’images natives (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="f0c87-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0c87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0c87-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0c87-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0c87-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f0c87-106">[in] L’ID de la fonction pour laquelle la recherche a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="f0c87-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="f0c87-107">[in] Une valeur de la [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) énumération qui indique le résultat de la recherche.</span><span class="sxs-lookup"><span data-stu-id="f0c87-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0c87-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="f0c87-108">Remarks</span></span>  
 <span data-ttu-id="f0c87-109">Dans le .NET Framework version 2.0, le [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) et `JITCachedFunctionSearchFinished` rappels ne sont pas effectués pour toutes les fonctions dans les images NGen normales.</span><span class="sxs-lookup"><span data-stu-id="f0c87-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="f0c87-110">Seules les images NGen optimisées pour un profileur généreront des rappels pour toutes les fonctions dans l’image.</span><span class="sxs-lookup"><span data-stu-id="f0c87-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="f0c87-111">Toutefois, en raison de la charge supplémentaire, un profileur doit demander les images NGen optimisées sur le profileur uniquement si elle a l’intention d’utiliser ces rappels pour forcer une fonction compilée juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="f0c87-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="f0c87-112">Sinon, le profileur doit utiliser une stratégie minimale pour la collecte des informations sur la fonction.</span><span class="sxs-lookup"><span data-stu-id="f0c87-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0c87-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f0c87-113">Requirements</span></span>  
 <span data-ttu-id="f0c87-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0c87-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0c87-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0c87-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0c87-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0c87-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0c87-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0c87-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c87-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0c87-118">See Also</span></span>  
 [<span data-ttu-id="f0c87-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f0c87-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
