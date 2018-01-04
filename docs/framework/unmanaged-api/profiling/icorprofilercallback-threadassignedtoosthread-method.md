---
title: "ICorProfilerCallback::ThreadAssignedToOSThread, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ThreadAssignedToOSThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42c23a8190ea611d0333ebd96a31428574191b23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="dfa53-102">ICorProfilerCallback::ThreadAssignedToOSThread, méthode</span><span class="sxs-lookup"><span data-stu-id="dfa53-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="dfa53-103">Notifie le profileur qu’un thread managé est implémenté à l’aide d’un thread de système d’exploitation particulier.</span><span class="sxs-lookup"><span data-stu-id="dfa53-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfa53-104">Syntax</span></span>  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfa53-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dfa53-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="dfa53-106">[in] L’identificateur du thread managé.</span><span class="sxs-lookup"><span data-stu-id="dfa53-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="dfa53-107">[in] L’identificateur du thread de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="dfa53-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfa53-108">Notes</span><span class="sxs-lookup"><span data-stu-id="dfa53-108">Remarks</span></span>  
 <span data-ttu-id="dfa53-109">Le `ThreadAssignedToOSThread` rappel existe afin que le profileur peut assurer un mappage précis entre les fibres de threads de système d’exploitation et les threads managés.</span><span class="sxs-lookup"><span data-stu-id="dfa53-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa53-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dfa53-110">Requirements</span></span>  
 <span data-ttu-id="dfa53-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfa53-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfa53-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dfa53-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dfa53-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfa53-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfa53-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfa53-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa53-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfa53-115">See Also</span></span>  
 [<span data-ttu-id="dfa53-116">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="dfa53-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
