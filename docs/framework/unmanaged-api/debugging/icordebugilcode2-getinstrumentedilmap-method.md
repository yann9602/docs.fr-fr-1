---
title: "ICorDebugILCode2::GetInstrumentedILMap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILCode2.GetInstrumentedILMap
api_location: mscordbi.dll
api_type: COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9b740f378b4fd15fe6bf4a9832348869878e2a4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="6cee6-102">ICorDebugILCode2::GetInstrumentedILMap, méthode</span><span class="sxs-lookup"><span data-stu-id="6cee6-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="6cee6-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="6cee6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6cee6-104">Retourne un mappage des décalages du langage intermédiaire instrumenté par le profileur avec les décalages du langage intermédiaire de la méthode d'origine pour cette instance.</span><span class="sxs-lookup"><span data-stu-id="6cee6-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cee6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cee6-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cee6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6cee6-106">Parameters</span></span>  
 <span data-ttu-id="6cee6-107">cMap</span><span class="sxs-lookup"><span data-stu-id="6cee6-107">cMap</span></span>  
 <span data-ttu-id="6cee6-108">[en entrée] La capacité de stockage du tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="6cee6-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="6cee6-109">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="6cee6-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="6cee6-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="6cee6-110">pcMap</span></span>  
 <span data-ttu-id="6cee6-111">[out] Le nombre de valeurs COR_IL_MAP écrites dans le tableau de mappage.</span><span class="sxs-lookup"><span data-stu-id="6cee6-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="6cee6-112">map</span><span class="sxs-lookup"><span data-stu-id="6cee6-112">map</span></span>  
 <span data-ttu-id="6cee6-113">[out] Un tableau de valeurs COR_IL_MAP qui fournissent des informations sur les mappages de langage intermédiaire instrumenté par le profileur pour le langage intermédiaire de la méthode d’origine.</span><span class="sxs-lookup"><span data-stu-id="6cee6-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cee6-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="6cee6-114">Remarks</span></span>  
 <span data-ttu-id="6cee6-115">Si le profileur définit le mappage en appelant le [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) (méthode), le débogueur peut appeler cette méthode pour récupérer le mappage et utiliser le mappage en interne lors du calcul de langage intermédiaire des décalages pour la pile les traces et les durées de vie des variables.</span><span class="sxs-lookup"><span data-stu-id="6cee6-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="6cee6-116">Si `cMap` est égal à 0 et `pcMap` est non -**null**, `pcMap` est défini sur le nombre de valeurs COR_IL_MAP disponibles.</span><span class="sxs-lookup"><span data-stu-id="6cee6-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="6cee6-117">Si `cMap` est différent de zéro, il représente la capacité de stockage du tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="6cee6-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="6cee6-118">Lorsque la méthode retourne, `map` contenant un maximum de `cMap` éléments, et `pcMap` est défini sur le nombre de valeurs COR_IL_MAP réellement écrits dans le `map` tableau.</span><span class="sxs-lookup"><span data-stu-id="6cee6-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="6cee6-119">Si le langage intermédiaire n'a pas été instrumenté ou si le mappage n'a pas été fourni par le profileur, cette méthode retourne `S_OK` et définit `pcMap` à 0.</span><span class="sxs-lookup"><span data-stu-id="6cee6-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cee6-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6cee6-120">Requirements</span></span>  
 <span data-ttu-id="6cee6-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cee6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cee6-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cee6-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cee6-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cee6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cee6-124">**Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cee6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cee6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cee6-125">See Also</span></span>  
 [<span data-ttu-id="6cee6-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="6cee6-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)  
 [<span data-ttu-id="6cee6-127">Icordebugilcode2, Interface</span><span class="sxs-lookup"><span data-stu-id="6cee6-127">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [<span data-ttu-id="6cee6-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6cee6-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
