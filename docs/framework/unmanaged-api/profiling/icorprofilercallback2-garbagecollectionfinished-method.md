---
title: "ICorProfilerCallback2::GarbageCollectionFinished, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.GarbageCollectionFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ae517fcf9beb2205cf17177ed639ef0bd07adbf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="31256-102">ICorProfilerCallback2::GarbageCollectionFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="31256-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="31256-103">Notifie le profileur que le garbage collection est terminée et que tous les rappels de garbage collection ont été publiés.</span><span class="sxs-lookup"><span data-stu-id="31256-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31256-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31256-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="31256-105">Notes</span><span class="sxs-lookup"><span data-stu-id="31256-105">Remarks</span></span>  
 <span data-ttu-id="31256-106">Il est possible pour le profileur d’inspecter des objets dans leurs emplacements finaux lorsque le `GarbageCollectionFinished` méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="31256-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31256-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="31256-107">Requirements</span></span>  
 <span data-ttu-id="31256-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31256-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31256-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31256-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31256-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31256-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31256-111">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31256-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31256-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31256-112">See Also</span></span>  
 [<span data-ttu-id="31256-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="31256-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="31256-114">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="31256-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
