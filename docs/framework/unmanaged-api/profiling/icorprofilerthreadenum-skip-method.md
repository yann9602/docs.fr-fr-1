---
title: "ICorProfilerThreadEnum::Skip, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.Skip
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c1840722a250dd627a5214700dca95c48aa2e8d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="66e7b-102">ICorProfilerThreadEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="66e7b-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="66e7b-103">Fait avancer le curseur de l'énumérateur depuis sa position actuelle de manière à ignorer le nombre spécifié d'éléments.</span><span class="sxs-lookup"><span data-stu-id="66e7b-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66e7b-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66e7b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="66e7b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="66e7b-106">[in] Le nombre d’éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="66e7b-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66e7b-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="66e7b-107">Return Value</span></span>  
 <span data-ttu-id="66e7b-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="66e7b-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="66e7b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66e7b-109">HRESULT</span></span>|<span data-ttu-id="66e7b-110">Description</span><span class="sxs-lookup"><span data-stu-id="66e7b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="66e7b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="66e7b-111">S_OK</span></span>|<span data-ttu-id="66e7b-112">`celt`éléments ont été ignorés.</span><span class="sxs-lookup"><span data-stu-id="66e7b-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="66e7b-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="66e7b-113">S_FALSE</span></span>|<span data-ttu-id="66e7b-114">Moins de `celt` éléments ont été ignorés, ce qui signifie qu’il n’y a plus d’éléments.</span><span class="sxs-lookup"><span data-stu-id="66e7b-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66e7b-115">Notes</span><span class="sxs-lookup"><span data-stu-id="66e7b-115">Remarks</span></span>  
 <span data-ttu-id="66e7b-116">La nouvelle position du curseur de cet énumérateur est (position actuelle) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="66e7b-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e7b-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="66e7b-117">Requirements</span></span>  
 <span data-ttu-id="66e7b-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66e7b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66e7b-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66e7b-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66e7b-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66e7b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66e7b-121">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66e7b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e7b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66e7b-122">See Also</span></span>  
 [<span data-ttu-id="66e7b-123">ICorProfilerThreadEnum, interface</span><span class="sxs-lookup"><span data-stu-id="66e7b-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="66e7b-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="66e7b-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
