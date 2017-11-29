---
title: "ICorProfilerInfo2::GetCodeInfo2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetCodeInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6c2526c286e4014b32e63ec34f9d212a5f657756
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="eebb6-102">ICorProfilerInfo2::GetCodeInfo2, méthode</span><span class="sxs-lookup"><span data-stu-id="eebb6-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="eebb6-103">Obtient l'étendue de code natif associée au `FunctionID` spécifié.</span><span class="sxs-lookup"><span data-stu-id="eebb6-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eebb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eebb6-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eebb6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eebb6-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="eebb6-106">[in] ID de la fonction à laquelle le code natif est associé.</span><span class="sxs-lookup"><span data-stu-id="eebb6-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="eebb6-107">[in] Taille du tableau `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="eebb6-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="eebb6-108">[out] Un pointeur vers le nombre total de [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures disponibles.</span><span class="sxs-lookup"><span data-stu-id="eebb6-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="eebb6-109">[out] Mémoire tampon fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="eebb6-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="eebb6-110">Suite au retour de la méthode, celle-ci contient un tableau de structures `COR_PRF_CODE_INFO` qui décrivent chacune un bloc de code natif.</span><span class="sxs-lookup"><span data-stu-id="eebb6-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eebb6-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="eebb6-111">Remarks</span></span>  
 <span data-ttu-id="eebb6-112">Les étendues sont triées par ordre croissant des offsets du langage MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="eebb6-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="eebb6-113">Suite au retour de `GetCodeInfo2`, vous devez vérifier que la mémoire tampon `codeInfos` est suffisamment grande pour contenir toutes les structures `COR_PRF_CODE_INFO`.</span><span class="sxs-lookup"><span data-stu-id="eebb6-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="eebb6-114">Pour ce faire, comparez la valeur de `cCodeInfos` à celle du paramètre `cchName`.</span><span class="sxs-lookup"><span data-stu-id="eebb6-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="eebb6-115">Si le résultat de la division de `cCodeInfos` par la taille d'une structure `COR_PRF_CODE_INFO` est inférieur à `pcCodeInfos`, allouez une mémoire tampon `codeInfos` plus grande, mettez à jour `cCodeInfos` pour refléter la nouvelle taille et rappelez `GetCodeInfo2`.</span><span class="sxs-lookup"><span data-stu-id="eebb6-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="eebb6-116">Vous pouvez également commencer par appeler `GetCodeInfo2` avec une mémoire tampon `codeInfos` de longueur nulle pour obtenir la taille correcte de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="eebb6-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="eebb6-117">Vous pouvez ensuite affecter à la taille de la mémoire tampon `codeInfos` la valeur retournée dans `pcCodeInfos`, multipliée par la taille d'une structure `COR_PRF_CODE_INFO`, puis rappeler `GetCodeInfo2`.</span><span class="sxs-lookup"><span data-stu-id="eebb6-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eebb6-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="eebb6-118">Requirements</span></span>  
 <span data-ttu-id="eebb6-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eebb6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eebb6-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eebb6-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eebb6-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eebb6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eebb6-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eebb6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eebb6-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eebb6-123">See Also</span></span>  
 [<span data-ttu-id="eebb6-124">GetCodeInfo3 (méthode)</span><span class="sxs-lookup"><span data-stu-id="eebb6-124">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)  
 [<span data-ttu-id="eebb6-125">ICorProfilerInfo2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="eebb6-125">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="eebb6-126">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="eebb6-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="eebb6-127">Profilage</span><span class="sxs-lookup"><span data-stu-id="eebb6-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
