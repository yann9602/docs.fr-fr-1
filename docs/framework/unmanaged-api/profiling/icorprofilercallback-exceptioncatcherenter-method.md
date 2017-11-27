---
title: "ICorProfilerCallback::ExceptionCatcherEnter, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCatcherEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b1605fdca3f5aa13ce4e29c0ff2fb42383512e6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="b7e21-102">ICorProfilerCallback::ExceptionCatcherEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="b7e21-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="b7e21-103">Notifie le profileur que le contrôle est passé à approprié `catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="b7e21-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7e21-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7e21-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b7e21-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b7e21-106">[in] L’identificateur de la fonction contenant le `catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="b7e21-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="b7e21-107">[in] Identificateur de l’exception en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="b7e21-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7e21-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="b7e21-108">Remarks</span></span>  
 <span data-ttu-id="b7e21-109">Le `ExceptionCatcherEnter` méthode est appelée uniquement si le point catch est dans le code compilé avec le compilateur juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="b7e21-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="b7e21-110">Une exception est interceptée dans le code non managé ou dans le code interne du runtime n’appellera pas cette notification.</span><span class="sxs-lookup"><span data-stu-id="b7e21-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="b7e21-111">Le `objectId` la valeur est passée à nouveau dans la mesure où un garbage collection peut avoir déplacer l’objet depuis le `ExceptionThrown` notification.</span><span class="sxs-lookup"><span data-stu-id="b7e21-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="b7e21-112">Le profileur ne doit pas bloquer dans son implémentation de cette méthode, car la pile ne peut pas être dans un état qui autorise le garbage collection, et par conséquent, le garbage collection préemptif ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="b7e21-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b7e21-113">Si le profileur bloque ici et le garbage collection est tenté, le runtime bloque jusqu'à ce que ce rappel retourne.</span><span class="sxs-lookup"><span data-stu-id="b7e21-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b7e21-114">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="b7e21-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7e21-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b7e21-115">Requirements</span></span>  
 <span data-ttu-id="b7e21-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7e21-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7e21-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b7e21-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b7e21-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7e21-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7e21-119">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7e21-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e21-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7e21-120">See Also</span></span>  
 [<span data-ttu-id="b7e21-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b7e21-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="b7e21-122">ExceptionCatcherLeave (méthode)</span><span class="sxs-lookup"><span data-stu-id="b7e21-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
