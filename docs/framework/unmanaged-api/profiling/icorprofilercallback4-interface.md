---
title: ICorProfilerCallback4, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4
helpviewer_keywords: ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 64a26f5dfb0ad9f06bb1b9eb31dcae36f4623c4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="01a55-102">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="01a55-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="01a55-103">Fournit des méthodes de rappel que le common language runtime (CLR) utilise pour communiquer des informations au profileur.</span><span class="sxs-lookup"><span data-stu-id="01a55-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01a55-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="01a55-104">Methods</span></span>  
  
|<span data-ttu-id="01a55-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="01a55-105">Method</span></span>|<span data-ttu-id="01a55-106">Description</span><span class="sxs-lookup"><span data-stu-id="01a55-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01a55-107">GetReJITParameters (méthode)</span><span class="sxs-lookup"><span data-stu-id="01a55-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="01a55-108">Permet au profileur de code définir les indicateurs de génération de code de remplacement pour un nouveau corps de méthode recompilée.</span><span class="sxs-lookup"><span data-stu-id="01a55-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="01a55-109">MovedReferences2 (méthode)</span><span class="sxs-lookup"><span data-stu-id="01a55-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="01a55-110">Signale la nouvelle disposition d’objets dans le tas suite à un garbage collection de compactage.</span><span class="sxs-lookup"><span data-stu-id="01a55-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="01a55-111">ReJITCompilationFinished (méthode)</span><span class="sxs-lookup"><span data-stu-id="01a55-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="01a55-112">Notifie le profileur que le compilateur (JIT) juste-à-temps a terminé la recompilation d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="01a55-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="01a55-113">ReJITCompilationStarted (méthode)</span><span class="sxs-lookup"><span data-stu-id="01a55-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="01a55-114">Notifie le profileur que le compilateur (JIT) juste-à-temps a démarré recompiler une fonction.</span><span class="sxs-lookup"><span data-stu-id="01a55-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="01a55-115">ReJITError (méthode)</span><span class="sxs-lookup"><span data-stu-id="01a55-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="01a55-116">Signale une erreur s’est produite lors du traitement d’une demande de recompilation.</span><span class="sxs-lookup"><span data-stu-id="01a55-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="01a55-117">SurvivingReferences2 (méthode)</span><span class="sxs-lookup"><span data-stu-id="01a55-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="01a55-118">Signale la disposition d’objets dans le tas suite à un garbage collection de non-compactage.</span><span class="sxs-lookup"><span data-stu-id="01a55-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01a55-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="01a55-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01a55-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="01a55-120">Requirements</span></span>  
 <span data-ttu-id="01a55-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01a55-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01a55-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01a55-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01a55-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01a55-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01a55-124">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01a55-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a55-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01a55-125">See Also</span></span>  
 [<span data-ttu-id="01a55-126">ICorProfilerCallback2, Interface</span><span class="sxs-lookup"><span data-stu-id="01a55-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="01a55-127">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="01a55-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="01a55-128">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="01a55-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
