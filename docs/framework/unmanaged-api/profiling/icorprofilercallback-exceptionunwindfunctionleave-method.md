---
title: "ICorProfilerCallback::ExceptionUnwindFunctionLeave, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eba7f6e5123108a7040bd2185eb57fc703c72c30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="c7e2a-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="c7e2a-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="c7e2a-103">Notifie le profileur que la phase de déroulement de la gestion des exceptions a terminé le déroulement d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="c7e2a-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7e2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7e2a-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c7e2a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="c7e2a-105">Remarks</span></span>  
 <span data-ttu-id="c7e2a-106">Lorsque le `ExceptionUnwindFunctionLeave` est appelée, l’instance de la fonction et ses données de pile sont supprimées de la pile.</span><span class="sxs-lookup"><span data-stu-id="c7e2a-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="c7e2a-107">Le profileur ne doit pas bloquer pendant cet appel, car la pile ne peut pas être dans un état qui autorise le garbage collection, et par conséquent, le garbage collection préemptif ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="c7e2a-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="c7e2a-108">Si le profileur bloque et un garbage collection est tentée, le runtime bloque jusqu'à ce que ce rappel retourne.</span><span class="sxs-lookup"><span data-stu-id="c7e2a-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="c7e2a-109">En outre, au cours de cet appel, le profileur doit appeler pas dans le code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="c7e2a-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7e2a-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c7e2a-110">Requirements</span></span>  
 <span data-ttu-id="c7e2a-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7e2a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7e2a-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c7e2a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c7e2a-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7e2a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7e2a-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7e2a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e2a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7e2a-115">See Also</span></span>  
 [<span data-ttu-id="c7e2a-116">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="c7e2a-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="c7e2a-117">ExceptionUnwindFunctionEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="c7e2a-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
