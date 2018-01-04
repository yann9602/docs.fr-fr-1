---
title: "ICorProfilerCallback::ObjectAllocated, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectAllocated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37f4701271f299698d7cd323b7d701f4cb7adb25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="2843c-102">ICorProfilerCallback::ObjectAllocated, méthode</span><span class="sxs-lookup"><span data-stu-id="2843c-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="2843c-103">Notifie le profileur de mémoire dans le tas a été allouée pour un objet.</span><span class="sxs-lookup"><span data-stu-id="2843c-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2843c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2843c-104">Syntax</span></span>  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2843c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2843c-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="2843c-106">[in] L’ID de l’objet pour lequel la mémoire a été allouée.</span><span class="sxs-lookup"><span data-stu-id="2843c-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="2843c-107">[in] L’ID de la classe dont l’objet est une instance.</span><span class="sxs-lookup"><span data-stu-id="2843c-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2843c-108">Notes</span><span class="sxs-lookup"><span data-stu-id="2843c-108">Remarks</span></span>  
 <span data-ttu-id="2843c-109">Le `ObjectedAllocated` méthode n’est pas appelée pour les allocations de la pile ou la mémoire non managée.</span><span class="sxs-lookup"><span data-stu-id="2843c-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="2843c-110">Le `classId` paramètre peut faire référence à une classe dans le code managé qui n’a pas encore été chargé.</span><span class="sxs-lookup"><span data-stu-id="2843c-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="2843c-111">Le profileur reçoit un rappel de chargement de classe pour cette classe immédiatement après le `ObjectAllocated` rappel.</span><span class="sxs-lookup"><span data-stu-id="2843c-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2843c-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2843c-112">Requirements</span></span>  
 <span data-ttu-id="2843c-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2843c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2843c-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2843c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2843c-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2843c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2843c-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2843c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2843c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2843c-117">See Also</span></span>  
 [<span data-ttu-id="2843c-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="2843c-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="2843c-119">ClassLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="2843c-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)  
 [<span data-ttu-id="2843c-120">ClassLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="2843c-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
