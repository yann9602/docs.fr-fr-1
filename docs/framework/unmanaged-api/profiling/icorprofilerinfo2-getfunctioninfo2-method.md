---
title: "ICorProfilerInfo2::GetFunctionInfo2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e7a48f109c22ae768e636a7f6b57e4e10ac76012
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="f819d-102">ICorProfilerInfo2::GetFunctionInfo2, méthode</span><span class="sxs-lookup"><span data-stu-id="f819d-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="f819d-103">Obtient la classe parente, le jeton de métadonnées et le `ClassID` de chaque argument de type, le cas échéant, d'une fonction.</span><span class="sxs-lookup"><span data-stu-id="f819d-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f819d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f819d-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f819d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f819d-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="f819d-106">[in] ID de la fonction pour laquelle obtenir la classe parente et d'autres informations.</span><span class="sxs-lookup"><span data-stu-id="f819d-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="f819d-107">[in] Valeur `COR_PRF_FRAME_INFO` qui pointe vers les informations sur un frame de pile.</span><span class="sxs-lookup"><span data-stu-id="f819d-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="f819d-108">[out] Pointeur vers la classe parente de la fonction.</span><span class="sxs-lookup"><span data-stu-id="f819d-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="f819d-109">[out] Pointeur vers le module dans lequel la classe parente de la fonction est définie.</span><span class="sxs-lookup"><span data-stu-id="f819d-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="f819d-110">[out] Pointeur vers le jeton de métadonnées de la fonction.</span><span class="sxs-lookup"><span data-stu-id="f819d-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="f819d-111">[in] Taille du tableau `typeArgs`.</span><span class="sxs-lookup"><span data-stu-id="f819d-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="f819d-112">[out] Pointeur vers le nombre total de valeurs `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="f819d-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="f819d-113">[out] Tableau de valeurs `ClassID` qui représentent chacune l'ID d'un argument de type de la fonction.</span><span class="sxs-lookup"><span data-stu-id="f819d-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="f819d-114">Suite au retour de la méthode, `typeArgs` contient une partie ou la totalité des valeurs `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="f819d-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f819d-115">Notes</span><span class="sxs-lookup"><span data-stu-id="f819d-115">Remarks</span></span>  
 <span data-ttu-id="f819d-116">Le code du profileur peut appeler [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) pour obtenir un [métadonnées](../../../../docs/framework/unmanaged-api/metadata/index.md) interface pour un module donné.</span><span class="sxs-lookup"><span data-stu-id="f819d-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="f819d-117">Le jeton de métadonnées qui est retourné à l'emplacement référencé par `pToken` peut alors servir à accéder aux métadonnées pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="f819d-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="f819d-118">L'ID de classe et les arguments de type retournés via les paramètres `pClassId` et `typeArgs` dépendent de la valeur qui est passée dans le paramètre `frameInfo`, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f819d-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="f819d-119">Valeur du paramètre `frameInfo`.</span><span class="sxs-lookup"><span data-stu-id="f819d-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="f819d-120">Résultat</span><span class="sxs-lookup"><span data-stu-id="f819d-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="f819d-121">Valeur `COR_PRF_FRAME_INFO` obtenue d'un rappel `FunctionEnter2`</span><span class="sxs-lookup"><span data-stu-id="f819d-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="f819d-122">La valeur `ClassID`, retournée dans l'emplacement référencé par `pClassId`, et tous les arguments de type, retournés dans le tableau `typeArgs`, seront exacts.</span><span class="sxs-lookup"><span data-stu-id="f819d-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="f819d-123">`COR_PRF_FRAME_INFO` obtenu à partir d'une source autre qu'un rappel `FunctionEnter2`</span><span class="sxs-lookup"><span data-stu-id="f819d-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="f819d-124">La valeur `ClassID` et les arguments de type exacts ne peuvent pas être déterminés.</span><span class="sxs-lookup"><span data-stu-id="f819d-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="f819d-125">Autrement dit, la valeur `ClassID` peut être null et certains arguments de type peuvent être retournés comme <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="f819d-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="f819d-126">Zéro</span><span class="sxs-lookup"><span data-stu-id="f819d-126">Zero</span></span>|<span data-ttu-id="f819d-127">La valeur `ClassID` et les arguments de type exacts ne peuvent pas être déterminés.</span><span class="sxs-lookup"><span data-stu-id="f819d-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="f819d-128">Autrement dit, la valeur `ClassID` peut être null et certains arguments de type peuvent être retournés comme <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="f819d-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="f819d-129">Suite au retour de `GetFunctionInfo2`, vous devez vérifier que la mémoire tampon `typeArgs` est suffisamment grande pour contenir toutes les valeurs `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="f819d-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="f819d-130">Pour ce faire, comparez la valeur vers laquelle `pcTypeArgs` pointe à celle du paramètre `cTypeArgs`.</span><span class="sxs-lookup"><span data-stu-id="f819d-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="f819d-131">Si `pcTypeArgs` pointe vers une valeur supérieure à `cTypeArgs` divisée par la taille d'une valeur `ClassID`, allouez une mémoire tampon `pcTypeArgs` plus grande, mettez à jour `cTypeArgs` pour refléter la nouvelle taille et rappelez `GetFunctionInfo2`.</span><span class="sxs-lookup"><span data-stu-id="f819d-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="f819d-132">Vous pouvez également commencer par appeler `GetFunctionInfo2` avec une mémoire tampon `pcTypeArgs` de longueur nulle pour obtenir la taille correcte de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="f819d-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="f819d-133">Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcTypeArgs` divisée par la taille d'une valeur `ClassID` et rappeler `GetFunctionInfo2`.</span><span class="sxs-lookup"><span data-stu-id="f819d-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f819d-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f819d-134">Requirements</span></span>  
 <span data-ttu-id="f819d-135">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f819d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f819d-136">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f819d-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f819d-137">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f819d-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f819d-138">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f819d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f819d-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f819d-139">See Also</span></span>  
 [<span data-ttu-id="f819d-140">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="f819d-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="f819d-141">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="f819d-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="f819d-142">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="f819d-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="f819d-143">Profilage</span><span class="sxs-lookup"><span data-stu-id="f819d-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
