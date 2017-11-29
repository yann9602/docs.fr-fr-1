---
title: "ICorProfilerCallback::ExceptionUnwindFinallyLeave, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf373872ada8364fe755162597dc9baf5c527f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="93729-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="93729-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="93729-103">Informe le profileur que la phase de déroulement d’exception gestion a quitté une `finally` clause.</span><span class="sxs-lookup"><span data-stu-id="93729-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93729-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93729-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="93729-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="93729-105">Remarks</span></span>  
 <span data-ttu-id="93729-106">Le profileur ne doit pas bloquer pendant cet appel, car la pile ne peut pas être dans un état qui autorise le garbage collection, et par conséquent, le garbage collection préemptif ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="93729-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="93729-107">Si le profileur bloque et un garbage collection est tentée, le runtime bloque jusqu'à ce que ce rappel retourne.</span><span class="sxs-lookup"><span data-stu-id="93729-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="93729-108">En outre, au cours de cet appel, le profileur doit appeler pas dans le code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="93729-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93729-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="93729-109">Requirements</span></span>  
 <span data-ttu-id="93729-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93729-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93729-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="93729-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93729-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93729-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93729-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93729-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93729-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93729-114">See Also</span></span>  
 [<span data-ttu-id="93729-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="93729-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="93729-116">ExceptionUnwindFinallyEnter (méthode)</span><span class="sxs-lookup"><span data-stu-id="93729-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
