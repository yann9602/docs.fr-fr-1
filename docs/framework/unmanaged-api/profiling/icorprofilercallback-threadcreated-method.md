---
title: "ICorProfilerCallback::ThreadCreated, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ThreadCreated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b62d5d1129bb71a95ac4e98624558272b08f0683
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="3935b-102">ICorProfilerCallback::ThreadCreated, méthode</span><span class="sxs-lookup"><span data-stu-id="3935b-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="3935b-103">Notifie le profileur qu’un thread a été créé.</span><span class="sxs-lookup"><span data-stu-id="3935b-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3935b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3935b-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="3935b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3935b-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="3935b-106">[in] L’ID du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="3935b-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3935b-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="3935b-107">Remarks</span></span>  
 <span data-ttu-id="3935b-108">Le `threadId` la valeur est valide immédiatement.</span><span class="sxs-lookup"><span data-stu-id="3935b-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3935b-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3935b-109">Requirements</span></span>  
 <span data-ttu-id="3935b-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3935b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3935b-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3935b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3935b-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3935b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3935b-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3935b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3935b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3935b-114">See Also</span></span>  
 [<span data-ttu-id="3935b-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="3935b-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3935b-116">ThreadDestroyed (méthode)</span><span class="sxs-lookup"><span data-stu-id="3935b-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
