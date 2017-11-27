---
title: "ICorProfilerInfo4::InitializeCurrentThread, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4::InitializeCurrentThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc19ae86c266c74097bd649aa96f532528df3d7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="9a187-102">ICorProfilerInfo4::InitializeCurrentThread, méthode</span><span class="sxs-lookup"><span data-stu-id="9a187-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="9a187-103">Initialise le thread actuel avant profiler ultérieur qu'appels d’API sur le même thread, afin que le blocage peut être évité.</span><span class="sxs-lookup"><span data-stu-id="9a187-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a187-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a187-104">Syntax</span></span>  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9a187-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="9a187-105">Remarks</span></span>  
 <span data-ttu-id="9a187-106">Nous vous recommandons d’appeler `InitializeCurrentThread` sur n’importe quel thread qui appelle un profileur API lorsqu’il y a suspendu des threads.</span><span class="sxs-lookup"><span data-stu-id="9a187-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="9a187-107">Cette méthode est généralement utilisée par les profileurs d’échantillonnage qui créent leurs propres threads pour appeler le [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) méthode pour effectuer la pile présente alors que le thread cible est suspendu.</span><span class="sxs-lookup"><span data-stu-id="9a187-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="9a187-108">En appelant `InitializeCurrentThread` une fois lorsque le profileur crée d’abord le thread d’échantillonnage, les profileurs peuvent s’assurer que l’initialisation tardive par thread que le CLR, sinon, exécuterait pendant le premier appel à `DoStackSnapshot` peut désormais se produire en toute sécurité lorsque aucun autre thread n’est suspendu.</span><span class="sxs-lookup"><span data-stu-id="9a187-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a187-109">`InitializeCurrentThread`exécute l’initialisation à l’avance pour terminer les tâches qui prennent des verrous et peuvent se bloquer.</span><span class="sxs-lookup"><span data-stu-id="9a187-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="9a187-110">Appelez `InitializeCurrentThread` uniquement lorsque aucun thread interrompu.</span><span class="sxs-lookup"><span data-stu-id="9a187-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a187-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9a187-111">Requirements</span></span>  
 <span data-ttu-id="9a187-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a187-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a187-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a187-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a187-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a187-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a187-115">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a187-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a187-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a187-116">See Also</span></span>  
 [<span data-ttu-id="9a187-117">Icorprofilerinfo4, Interface</span><span class="sxs-lookup"><span data-stu-id="9a187-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="9a187-118">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="9a187-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="9a187-119">Profilage</span><span class="sxs-lookup"><span data-stu-id="9a187-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
