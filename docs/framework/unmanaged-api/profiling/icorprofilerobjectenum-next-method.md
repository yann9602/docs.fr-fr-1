---
title: "ICorProfilerObjectEnum::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.Next
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::Next
helpviewer_keywords:
- Next method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Next method [.NET Framework profiling]
ms.assetid: b420433c-5ebe-4986-bba1-97902e6db819
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfeec7c3ee2038b77549e53b10534d817b667687
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="67b8e-102">ICorProfilerObjectEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="67b8e-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="67b8e-103">Obtient le nombre spécifié d’objets contigus dans une collection séquentielle d’objets, en commençant à la position actuelle de l’énumérateur dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="67b8e-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67b8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67b8e-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67b8e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="67b8e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="67b8e-106">[in] Nombre d'objets à récupérer.</span><span class="sxs-lookup"><span data-stu-id="67b8e-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="67b8e-107">[out] Un tableau de `ObjectID` valeurs, chacune représentant un objet récupéré.</span><span class="sxs-lookup"><span data-stu-id="67b8e-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="67b8e-108">[out] Pointeur vers le nombre d'éléments réellement retournés dans le tableau `objects`.</span><span class="sxs-lookup"><span data-stu-id="67b8e-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67b8e-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="67b8e-109">Requirements</span></span>  
 <span data-ttu-id="67b8e-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67b8e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67b8e-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67b8e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67b8e-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67b8e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67b8e-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67b8e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b8e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67b8e-114">See Also</span></span>  
 [<span data-ttu-id="67b8e-115">ICorProfilerObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="67b8e-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
