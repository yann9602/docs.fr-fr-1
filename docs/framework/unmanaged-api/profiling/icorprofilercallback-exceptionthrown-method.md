---
title: "ICorProfilerCallback::ExceptionThrown, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionThrown
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3986ca8205297a36bb54825a7af72aeb9821f75b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="f1e36-102">ICorProfilerCallback::ExceptionThrown, méthode</span><span class="sxs-lookup"><span data-stu-id="f1e36-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="f1e36-103">Notifie le profileur qu’une exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="f1e36-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1e36-104">Cette fonction est appelée uniquement si l’exception atteint du code managé.</span><span class="sxs-lookup"><span data-stu-id="f1e36-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1e36-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1e36-105">Syntax</span></span>  
  
```  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1e36-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f1e36-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="f1e36-107">[in] L’ID de l’objet qui a provoqué l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="f1e36-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1e36-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="f1e36-108">Remarks</span></span>  
 <span data-ttu-id="f1e36-109">Le profileur ne doit pas bloquer dans son implémentation de cette méthode, car la pile ne peut pas être dans un état qui autorise le garbage collection, et par conséquent, le garbage collection préemptif ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="f1e36-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="f1e36-110">Si le profileur bloque ici et le garbage collection est tenté, le runtime bloque jusqu'à ce que ce rappel retourne.</span><span class="sxs-lookup"><span data-stu-id="f1e36-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="f1e36-111">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="f1e36-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1e36-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f1e36-112">Requirements</span></span>  
 <span data-ttu-id="f1e36-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1e36-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1e36-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f1e36-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1e36-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1e36-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1e36-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1e36-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e36-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1e36-117">See Also</span></span>  
 [<span data-ttu-id="f1e36-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f1e36-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
