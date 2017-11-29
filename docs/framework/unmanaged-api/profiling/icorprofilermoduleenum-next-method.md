---
title: "ICorProfilerModuleEnum::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Next Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c20b6970c0df30b75bacf76f52c7610bd4a3a5e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="f8077-102">ICorProfilerModuleEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="f8077-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="f8077-103">Obtient le nombre spécifié de modules contigus dans une collection séquentielle de modules, à commencer par la position actuelle de l’énumérateur dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="f8077-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8077-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8077-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8077-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8077-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f8077-106">[in] Nombre de modules à récupérer.</span><span class="sxs-lookup"><span data-stu-id="f8077-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="f8077-107">[out] Tableau de valeurs `ModuleID` qui représentent chacune un module récupéré.</span><span class="sxs-lookup"><span data-stu-id="f8077-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f8077-108">[out] Pointeur vers le nombre d'éléments réellement retournés dans le tableau `ids`.</span><span class="sxs-lookup"><span data-stu-id="f8077-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8077-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f8077-109">Return Value</span></span>  
 <span data-ttu-id="f8077-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f8077-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f8077-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8077-111">HRESULT</span></span>|<span data-ttu-id="f8077-112">Description</span><span class="sxs-lookup"><span data-stu-id="f8077-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8077-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8077-113">S_OK</span></span>|<span data-ttu-id="f8077-114">`celt` éléments ont été retournés.</span><span class="sxs-lookup"><span data-stu-id="f8077-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="f8077-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f8077-115">S_FALSE</span></span>|<span data-ttu-id="f8077-116">Moins de `celt` éléments ont été retournés, ce qui indique que l'énumération est terminée.</span><span class="sxs-lookup"><span data-stu-id="f8077-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8077-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f8077-117">Requirements</span></span>  
 <span data-ttu-id="f8077-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8077-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8077-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8077-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8077-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8077-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8077-121">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8077-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8077-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8077-122">See Also</span></span>  
 [<span data-ttu-id="f8077-123">ICorProfilerModuleEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="f8077-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="f8077-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="f8077-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
