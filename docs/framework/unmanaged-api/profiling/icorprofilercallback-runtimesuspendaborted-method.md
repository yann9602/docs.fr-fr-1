---
title: "ICorProfilerCallback::RuntimeSuspendAborted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendAborted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d1c181a471763ea0220c081d64af915ca6be149
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="a783c-102">ICorProfilerCallback::RuntimeSuspendAborted, méthode</span><span class="sxs-lookup"><span data-stu-id="a783c-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="a783c-103">Notifie le profileur que le runtime a abandonné la suspension de runtime qui était en cours.</span><span class="sxs-lookup"><span data-stu-id="a783c-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a783c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a783c-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a783c-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="a783c-105">Remarks</span></span>  
 <span data-ttu-id="a783c-106">Le runtime peut être abandonné si deux threads essaient simultanément d’arrêter l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a783c-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="a783c-107">Soit le [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) rappel ou `RuntimeSuspendAborted` rappel se produit sur un suivants de thread unique un [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="a783c-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="a783c-108">Le `RuntimeSuspendAborted` rappel est assuré de se produire sur le même thread que le `RuntimeSuspendStarted` rappel.</span><span class="sxs-lookup"><span data-stu-id="a783c-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a783c-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a783c-109">Requirements</span></span>  
 <span data-ttu-id="a783c-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a783c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a783c-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a783c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a783c-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a783c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a783c-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a783c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a783c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a783c-114">See Also</span></span>  
 [<span data-ttu-id="a783c-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a783c-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
