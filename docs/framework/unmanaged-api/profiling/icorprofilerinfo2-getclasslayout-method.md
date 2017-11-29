---
title: "ICorProfilerInfo2::GetClassLayout, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 988e9daf54d9b4edd623e2488b68dff007e4495b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="a64ba-102">ICorProfilerInfo2::GetClassLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="a64ba-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="a64ba-103">Obtient des informations sur la disposition, dans la mémoire, des champs définis par la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a64ba-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="a64ba-104">Autrement dit, cette méthode obtient les offsets des champs de la classe.</span><span class="sxs-lookup"><span data-stu-id="a64ba-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a64ba-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a64ba-105">Syntax</span></span>  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a64ba-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a64ba-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="a64ba-107">[in] ID de la classe pour laquelle les informations sont récupérées.</span><span class="sxs-lookup"><span data-stu-id="a64ba-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="a64ba-108">[dans, out] Un tableau de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, qui contiennent chacune les jetons et les offsets des champs de la classe.</span><span class="sxs-lookup"><span data-stu-id="a64ba-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="a64ba-109">[in] Taille du tableau `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="a64ba-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="a64ba-110">[out] Pointeur vers le nombre total d'éléments disponibles.</span><span class="sxs-lookup"><span data-stu-id="a64ba-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="a64ba-111">Si `cFieldOffset` est égal à 0, cette valeur indique le nombre d'éléments requis.</span><span class="sxs-lookup"><span data-stu-id="a64ba-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="a64ba-112">[out] Pointeur vers un emplacement qui contient la taille, en octets, de la classe.</span><span class="sxs-lookup"><span data-stu-id="a64ba-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a64ba-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="a64ba-113">Remarks</span></span>  
 <span data-ttu-id="a64ba-114">La méthode `GetClassLayout` retourne uniquement les champs définis par la classe elle-même.</span><span class="sxs-lookup"><span data-stu-id="a64ba-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="a64ba-115">Si la classe parente de la classe a également défini des champs, le profileur doit appeler `GetClassLayout` sur la classe parente pour obtenir ces champs.</span><span class="sxs-lookup"><span data-stu-id="a64ba-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="a64ba-116">Si vous utilisez `GetClassLayout` avec des classes string, la méthode échoue avec le code d'erreur E_INVALIDARG.</span><span class="sxs-lookup"><span data-stu-id="a64ba-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="a64ba-117">Utilisez [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) pour obtenir des informations sur la disposition d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="a64ba-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="a64ba-118">La méthode `GetClassLayout` échoue également quand elle est appelée avec une classe array.</span><span class="sxs-lookup"><span data-stu-id="a64ba-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="a64ba-119">Suite au retour de `GetClassLayout`, vous devez vérifier que la mémoire tampon `rFieldOffset` est suffisamment grande pour contenir toutes les structures `COR_FIELD_OFFSET` disponibles.</span><span class="sxs-lookup"><span data-stu-id="a64ba-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="a64ba-120">Pour ce faire, comparez la valeur vers laquelle pointe `pcFieldOffset` au résultat de la division de la taille de `rFieldOffset` par la taille d'une structure `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="a64ba-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="a64ba-121">Si la taille de `rFieldOffset` n'est pas suffisante, allouez une mémoire tampon `rFieldOffset` plus grande, mettez à jour `cFieldOffset` pour refléter la nouvelle taille et rappelez `GetClassLayout`.</span><span class="sxs-lookup"><span data-stu-id="a64ba-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="a64ba-122">Vous pouvez également commencer par appeler `GetClassLayout` avec une mémoire tampon `rFieldOffset` de longueur nulle pour obtenir la taille correcte de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="a64ba-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="a64ba-123">Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcFieldOffset` et rappeler `GetClassLayout`.</span><span class="sxs-lookup"><span data-stu-id="a64ba-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a64ba-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a64ba-124">Requirements</span></span>  
 <span data-ttu-id="a64ba-125">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a64ba-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a64ba-126">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a64ba-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a64ba-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a64ba-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a64ba-128">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a64ba-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a64ba-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a64ba-129">See Also</span></span>  
 [<span data-ttu-id="a64ba-130">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="a64ba-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="a64ba-131">ICorProfilerInfo2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="a64ba-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="a64ba-132">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="a64ba-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="a64ba-133">Profilage</span><span class="sxs-lookup"><span data-stu-id="a64ba-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
