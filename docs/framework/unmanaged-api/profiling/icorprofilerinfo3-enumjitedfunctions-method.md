---
title: "ICorProfilerInfo3::EnumJITedFunctions, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.EnumJITedFunctions Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2c367ae29cc0daa406356a245f3dc16a671d3c54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="23863-102">ICorProfilerInfo3::EnumJITedFunctions, méthode</span><span class="sxs-lookup"><span data-stu-id="23863-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="23863-103">Retourne un énumérateur pour toutes les fonctions qui ont été précédemment compilé par JIT.</span><span class="sxs-lookup"><span data-stu-id="23863-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23863-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23863-104">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23863-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="23863-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="23863-106">[out] Un pointeur vers le [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) énumérateur.</span><span class="sxs-lookup"><span data-stu-id="23863-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23863-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="23863-107">Remarks</span></span>  
 <span data-ttu-id="23863-108">Cette méthode peut se chevaucher avec `JITCompilation` rappels tels que les [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="23863-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="23863-109">L’énumérateur retourné par cette méthode n’inclut pas les fonctions qui sont chargées à partir d’images natives générées avec Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="23863-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23863-110">L’énumération retournée inclut uniquement « 0 » pour la valeur de la `COR_PRF_FUNCTION::reJitId` champ.</span><span class="sxs-lookup"><span data-stu-id="23863-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="23863-111">Si vous avez besoin valide `COR_PRF_FUNCTION::reJitId` valeurs, utilisez la [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="23863-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23863-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="23863-112">Requirements</span></span>  
 <span data-ttu-id="23863-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23863-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23863-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="23863-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="23863-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23863-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23863-116">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23863-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23863-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23863-117">See Also</span></span>  
 [<span data-ttu-id="23863-118">ICorProfilerInfo3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="23863-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="23863-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="23863-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="23863-120">Profilage</span><span class="sxs-lookup"><span data-stu-id="23863-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
