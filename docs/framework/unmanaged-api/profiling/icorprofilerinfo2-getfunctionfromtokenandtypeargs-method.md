---
title: "ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b225b87eab6e65055618c8b6659459637e8a01be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="da69b-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs, méthode</span><span class="sxs-lookup"><span data-stu-id="da69b-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="da69b-103">Obtient le `FunctionID` d’une fonction à l’aide du jeton de métadonnées spécifié contenant la classe, et `ClassID` valeurs des arguments de type.</span><span class="sxs-lookup"><span data-stu-id="da69b-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da69b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da69b-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da69b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="da69b-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="da69b-106">[in] L’ID du module dans lequel la fonction réside.</span><span class="sxs-lookup"><span data-stu-id="da69b-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="da69b-107">[in] Un `mdMethodDef` jeton de métadonnées qui fait référence à la fonction.</span><span class="sxs-lookup"><span data-stu-id="da69b-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="da69b-108">[in] L’ID de classe de conteneur de la fonction.</span><span class="sxs-lookup"><span data-stu-id="da69b-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="da69b-109">[in] Le nombre de paramètres de type pour la fonction donnée.</span><span class="sxs-lookup"><span data-stu-id="da69b-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="da69b-110">Cette valeur doit être zéro pour les fonctions non génériques.</span><span class="sxs-lookup"><span data-stu-id="da69b-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="da69b-111">[in] Un tableau de `ClassID` valeurs, chacune d’elles est un argument de la fonction.</span><span class="sxs-lookup"><span data-stu-id="da69b-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="da69b-112">La valeur de `typeArgs` peut être NULL si `cTypeArgs` est défini à zéro.</span><span class="sxs-lookup"><span data-stu-id="da69b-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="da69b-113">[out] Un pointeur vers le `FunctionID` de la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="da69b-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da69b-114">Notes</span><span class="sxs-lookup"><span data-stu-id="da69b-114">Remarks</span></span>  
 <span data-ttu-id="da69b-115">Appel de la `GetFunctionFromTokenAndTypeArgs` méthode avec un `mdMethodRef` métadonnées au lieu d’un `mdMethodDef` jeton de métadonnées peut avoir des résultats imprévisibles.</span><span class="sxs-lookup"><span data-stu-id="da69b-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="da69b-116">Les appelants doivent résoudre le `mdMethodRef` à un `mdMethodDef` lors de son passage.</span><span class="sxs-lookup"><span data-stu-id="da69b-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="da69b-117">Si la fonction n’est pas déjà chargée, l’appel `GetFunctionFromTokenAndTypeArgs` provoquera le chargement, qui est une opération dangereuse dans de nombreux contextes.</span><span class="sxs-lookup"><span data-stu-id="da69b-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="da69b-118">Par exemple, l’appel de cette méthode pendant le chargement de modules ou de types peut entraîner une boucle infinie, que le runtime tente de charger des éléments.</span><span class="sxs-lookup"><span data-stu-id="da69b-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="da69b-119">En règle générale, utilisez des `GetFunctionFromTokenAndTypeArgs` est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="da69b-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="da69b-120">Si les profileurs sont intéressés par les événements pour une fonction particulière, ils doivent stocker le `ModuleID` et `mdMethodDef` de cette fonction et utilisez [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) pour vérifier si une donnée `FunctionID` est celui de la fonction de votre choix.</span><span class="sxs-lookup"><span data-stu-id="da69b-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da69b-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="da69b-121">Requirements</span></span>  
 <span data-ttu-id="da69b-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da69b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da69b-123">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="da69b-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="da69b-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da69b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da69b-125">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da69b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da69b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da69b-126">See Also</span></span>  
 [<span data-ttu-id="da69b-127">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="da69b-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="da69b-128">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="da69b-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
