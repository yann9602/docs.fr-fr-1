---
title: ICorProfilerCallback5, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback5
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback5
helpviewer_keywords: ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1a862707dc64efbf3a9b1604a0e6a4ff1be81b43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="bb601-102">ICorProfilerCallback5, interface</span><span class="sxs-lookup"><span data-stu-id="bb601-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="bb601-103">Complète les informations pour identifier un profileur de la fermeture complète d’objets actifs, lorsqu’il est utilisé avec l’option le [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) ou [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)méthode avec la [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) et [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) méthodes.</span><span class="sxs-lookup"><span data-stu-id="bb601-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="bb601-104">`ICorProfilerCallback5` doit être implémentée par un profileur de mémoire managée pour s'abonner aux notifications relatives aux handles dépendants.</span><span class="sxs-lookup"><span data-stu-id="bb601-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb601-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="bb601-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bb601-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bb601-106">Methods</span></span>  
  
|<span data-ttu-id="bb601-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="bb601-107">Method</span></span>|<span data-ttu-id="bb601-108">Description</span><span class="sxs-lookup"><span data-stu-id="bb601-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bb601-109">ConditionalWeakTableElementReferences (méthode)</span><span class="sxs-lookup"><span data-stu-id="bb601-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="bb601-110">Identifie la fermeture transitive des objets référencés par ces racines via les références des champs des membres directs et via les dépendances de `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="bb601-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb601-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bb601-111">Requirements</span></span>  
 <span data-ttu-id="bb601-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb601-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb601-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb601-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb601-114">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb601-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb601-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb601-115">See Also</span></span>  
 [<span data-ttu-id="bb601-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="bb601-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="bb601-117">ICorProfilerCallback2, Interface</span><span class="sxs-lookup"><span data-stu-id="bb601-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
