---
title: "ICorProfilerThreadEnum::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.Next
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3295f3dc9af50fb62a2008f59819a51a6032a48b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="27833-102">ICorProfilerThreadEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="27833-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="27833-103">Obtient le nombre spécifié de threads contigus dans une collection séquentielle de threads, à commencer par la position actuelle de l’énumérateur dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="27833-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27833-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27833-104">Syntax</span></span>  
  
```  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27833-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="27833-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="27833-106">[in] Nombre de threads à récupérer.</span><span class="sxs-lookup"><span data-stu-id="27833-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="27833-107">[out] Tableau de valeurs `ThreadID` qui représentent chacune un thread récupéré.</span><span class="sxs-lookup"><span data-stu-id="27833-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="27833-108">[out] Pointeur vers le nombre de threads réellement retournés dans le tableau `ids`.</span><span class="sxs-lookup"><span data-stu-id="27833-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27833-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="27833-109">Return Value</span></span>  
 <span data-ttu-id="27833-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="27833-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="27833-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27833-111">HRESULT</span></span>|<span data-ttu-id="27833-112">Description</span><span class="sxs-lookup"><span data-stu-id="27833-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="27833-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="27833-113">S_OK</span></span>|<span data-ttu-id="27833-114">`celt` éléments ont été retournés.</span><span class="sxs-lookup"><span data-stu-id="27833-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="27833-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="27833-115">S_FALSE</span></span>|<span data-ttu-id="27833-116">Moins de `celt` éléments ont été retournés, ce qui indique que l'énumération est terminée.</span><span class="sxs-lookup"><span data-stu-id="27833-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27833-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="27833-117">Requirements</span></span>  
 <span data-ttu-id="27833-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27833-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27833-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27833-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27833-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27833-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27833-121">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27833-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27833-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27833-122">See Also</span></span>  
 [<span data-ttu-id="27833-123">ICorProfilerThreadEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="27833-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="27833-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="27833-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
