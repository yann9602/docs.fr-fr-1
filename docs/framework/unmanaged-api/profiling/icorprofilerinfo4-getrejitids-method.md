---
title: "ICorProfilerInfo4::GetReJITIDs, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetReJITIDs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc16cd932fc2ce0cf5cb53c227081501e79ed2d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="5e64d-102">ICorProfilerInfo4::GetReJITIDs, méthode</span><span class="sxs-lookup"><span data-stu-id="5e64d-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="5e64d-103">Retourne un tableau d’ID qui identifie toutes les recompilée juste-versions de la fonction spécifiée qui sont toujours allouées.</span><span class="sxs-lookup"><span data-stu-id="5e64d-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="5e64d-104">Cela inclut les versions de recompilée juste-des fonctions qui ont été annulées par la suite, mais pas encore libérées (par exemple, lorsque le domaine d’application qui contient la fonction restaurée est en cours d’utilisation).</span><span class="sxs-lookup"><span data-stu-id="5e64d-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e64d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e64d-105">Syntax</span></span>  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e64d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e64d-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5e64d-107">[in] Le `FunctionID` de l’instance de la fonction pour laquelle énumérer des versions.</span><span class="sxs-lookup"><span data-stu-id="5e64d-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="5e64d-108">[in] Le nombre d’ID recompilé juste-allouée dans le `reJitIds` tableau.</span><span class="sxs-lookup"><span data-stu-id="5e64d-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="5e64d-109">[out] Le nombre réel d’ID de recompilée juste.</span><span class="sxs-lookup"><span data-stu-id="5e64d-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="5e64d-110">[out] Tableau alloué par l’appelant qui contiendra les ID recompilé juste-pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5e64d-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e64d-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="5e64d-111">Remarks</span></span>  
 <span data-ttu-id="5e64d-112">`GetReJITIDs`énumère les ID recompilé juste-actives pour une instance de la fonction donnée.</span><span class="sxs-lookup"><span data-stu-id="5e64d-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="5e64d-113">Il suit le même modèle d’utilisation en tant qu’autre `ICorProfilerInfo` les fonctions qui acceptent des mémoires tampons allouées par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="5e64d-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e64d-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5e64d-114">Requirements</span></span>  
 <span data-ttu-id="5e64d-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e64d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e64d-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5e64d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e64d-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e64d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e64d-118">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e64d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e64d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e64d-119">See Also</span></span>  
 [<span data-ttu-id="5e64d-120">Icorprofilerinfo4, Interface</span><span class="sxs-lookup"><span data-stu-id="5e64d-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="5e64d-121">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="5e64d-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="5e64d-122">Profilage</span><span class="sxs-lookup"><span data-stu-id="5e64d-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
