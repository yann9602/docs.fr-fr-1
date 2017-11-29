---
title: "ICorProfilerCallback::ExceptionCatcherLeave, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCatcherLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 328bc3960a7c456b454ee35ff5ca467f02ef2303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="6ddd0-102">ICorProfilerCallback::ExceptionCatcherLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="6ddd0-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="6ddd0-103">Notifie le profileur que le contrôle est passé hors approprié `catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="6ddd0-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ddd0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ddd0-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6ddd0-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="6ddd0-105">Remarks</span></span>  
 <span data-ttu-id="6ddd0-106">Le profileur ne doit pas bloquer dans son implémentation de cette méthode, car la pile ne peut pas être dans un état qui autorise le garbage collection, et par conséquent, le garbage collection préemptif ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="6ddd0-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="6ddd0-107">Si le profileur bloque ici et le garbage collection est tenté, le runtime bloque jusqu'à ce que ce rappel retourne.</span><span class="sxs-lookup"><span data-stu-id="6ddd0-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="6ddd0-108">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="6ddd0-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ddd0-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6ddd0-109">Requirements</span></span>  
 <span data-ttu-id="6ddd0-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ddd0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ddd0-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6ddd0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6ddd0-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ddd0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ddd0-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ddd0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ddd0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ddd0-114">See Also</span></span>  
 [<span data-ttu-id="6ddd0-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="6ddd0-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="6ddd0-116">ExceptionCatcherEnter (méthode)</span><span class="sxs-lookup"><span data-stu-id="6ddd0-116">ExceptionCatcherEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
