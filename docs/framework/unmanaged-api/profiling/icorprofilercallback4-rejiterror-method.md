---
title: "ICorProfilerCallback4::ReJITError, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITError
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c8b1f3c5b206b2e6a108e784a206d597b69fd662
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="d8630-102">ICorProfilerCallback4::ReJITError, méthode</span><span class="sxs-lookup"><span data-stu-id="d8630-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="d8630-103">Notifie le profileur que le compilateur (JIT) juste-à-temps a rencontré une erreur dans le processus de recompilation.</span><span class="sxs-lookup"><span data-stu-id="d8630-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8630-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8630-104">Syntax</span></span>  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8630-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8630-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="d8630-106">[in] Le `ModuleID` dans lequel la recompilation ayant échoué a été tenté.</span><span class="sxs-lookup"><span data-stu-id="d8630-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="d8630-107">[in] Le `MethodDef` de la méthode sur lequel la tentative de recompilation ayant échoué a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="d8630-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="d8630-108">[in] L’instance de la fonction qui est recompilée ou marquée pour la recompilation.</span><span class="sxs-lookup"><span data-stu-id="d8630-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="d8630-109">Cette valeur peut être `NULL` si la défaillance s’est produite sur une base par méthode, au lieu d’une base par instanciation (par exemple, si le profileur a spécifié un jeton de métadonnées non valide pour la méthode d’être recompilé).</span><span class="sxs-lookup"><span data-stu-id="d8630-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="d8630-110">[in] HRESULT qui indique la nature de l’échec.</span><span class="sxs-lookup"><span data-stu-id="d8630-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="d8630-111">Consultez la section HRESULT d’état pour obtenir la liste de valeurs.</span><span class="sxs-lookup"><span data-stu-id="d8630-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8630-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d8630-112">Return Value</span></span>  
 <span data-ttu-id="d8630-113">Les valeurs retournées depuis ce rappel sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="d8630-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="d8630-114">HRESULT d'état</span><span class="sxs-lookup"><span data-stu-id="d8630-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="d8630-115">HRESULT du tableau d'états</span><span class="sxs-lookup"><span data-stu-id="d8630-115">Status array HRESULT</span></span>|<span data-ttu-id="d8630-116">Description</span><span class="sxs-lookup"><span data-stu-id="d8630-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="d8630-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d8630-117">E_INVALIDARG</span></span>|<span data-ttu-id="d8630-118">Le `moduleID` ou `methodDef` jeton est `NULL`.</span><span class="sxs-lookup"><span data-stu-id="d8630-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="d8630-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="d8630-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="d8630-120">Le module n'est pas encore totalement chargé ou il est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="d8630-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="d8630-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="d8630-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="d8630-122">Le module spécifié a été généré dynamiquement (par exemple, en `Reflection.Emit`) et n’est donc pas prise en charge par cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d8630-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="d8630-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="d8630-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="d8630-124">La méthode est instanciée dans un assembly pouvant être collecté et n’est donc pas en mesure d’être recompilé.</span><span class="sxs-lookup"><span data-stu-id="d8630-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="d8630-125">Notez que les types et fonctions définies dans un contexte de réflexion non (par exemple, `List<MyCollectibleStruct>`) peut être instancié dans un assembly pouvant être collecté.</span><span class="sxs-lookup"><span data-stu-id="d8630-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="d8630-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d8630-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d8630-127">Le CLR a manqué de mémoire lors de la tentative de marquer la méthode spécifiée pour la recompilation JIT.</span><span class="sxs-lookup"><span data-stu-id="d8630-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="d8630-128">Autre</span><span class="sxs-lookup"><span data-stu-id="d8630-128">Other</span></span>|<span data-ttu-id="d8630-129">Le système d'exploitation a retourné un échec en dehors du contrôle du CLR.</span><span class="sxs-lookup"><span data-stu-id="d8630-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="d8630-130">Par exemple, si un appel système pour modifier la protection d’accès d’une page de mémoire échoue, l’erreur de système d’exploitation s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d8630-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8630-131">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d8630-131">Requirements</span></span>  
 <span data-ttu-id="d8630-132">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8630-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8630-133">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8630-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8630-134">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8630-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8630-135">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8630-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8630-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8630-136">See Also</span></span>  
 [<span data-ttu-id="d8630-137">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d8630-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d8630-138">ICorProfilerCallback4 (Interface)</span><span class="sxs-lookup"><span data-stu-id="d8630-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
