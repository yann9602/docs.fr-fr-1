---
title: "ICorProfilerInfo4::RequestRevert, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.RequestRevert
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f0bf926bc6ba458745231bc17ce20dbe5cdbd1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="d64d6-102">ICorProfilerInfo4::RequestRevert, méthode</span><span class="sxs-lookup"><span data-stu-id="d64d6-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="d64d6-103">Rétablit les versions d'origine de toutes les instances des fonctions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d64d6-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d64d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d64d6-104">Syntax</span></span>  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d64d6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d64d6-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="d64d6-106">[in] Nombre de fonctions à rétablir.</span><span class="sxs-lookup"><span data-stu-id="d64d6-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="d64d6-107">[in] Spécifie la partie `moduleId` des paires (`module`, `methodDef`) qui identifient les fonctions à rétablir.</span><span class="sxs-lookup"><span data-stu-id="d64d6-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="d64d6-108">[in] Spécifie la partie `methodId` des paires (`module`, `methodDef`) qui identifient les fonctions à rétablir.</span><span class="sxs-lookup"><span data-stu-id="d64d6-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="d64d6-109">[out] Tableau de HRESULT répertoriés dans la section « HRESULT d'état » plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="d64d6-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="d64d6-110">Chaque HRESULT indique la réussite ou l'échec de la tentative de rétablissement de chaque fonction spécifiée dans les tableaux parallèles `moduleIds` et `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="d64d6-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d64d6-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d64d6-111">Return Value</span></span>  
 <span data-ttu-id="d64d6-112">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d64d6-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d64d6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d64d6-113">HRESULT</span></span>|<span data-ttu-id="d64d6-114">Description</span><span class="sxs-lookup"><span data-stu-id="d64d6-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d64d6-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d64d6-115">S_OK</span></span>|<span data-ttu-id="d64d6-116">Une tentative de rétablissement de toutes les demandes a été effectuée ; toutefois, le tableau d'états retourné doit être examiné pour déterminer les fonctions qui ont été correctement rétablies.</span><span class="sxs-lookup"><span data-stu-id="d64d6-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="d64d6-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="d64d6-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="d64d6-118">Le profileur doit implémenter la [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface pour cet appel pour être pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d64d6-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="d64d6-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="d64d6-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="d64d6-120">La recompilation juste-à-temps n'a pas été activée.</span><span class="sxs-lookup"><span data-stu-id="d64d6-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="d64d6-121">Vous devez activer la recompilation JIT pendant l’initialisation à l’aide de la [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pour définir le `COR_PRF_ENABLE_REJIT` indicateur.</span><span class="sxs-lookup"><span data-stu-id="d64d6-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="d64d6-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d64d6-122">E_INVALIDARG</span></span>|<span data-ttu-id="d64d6-123">`cFunctions` est égal à 0, ou `moduleIds` ou `methodIds` a la valeur `NULL`.</span><span class="sxs-lookup"><span data-stu-id="d64d6-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="d64d6-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d64d6-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d64d6-125">Le CLR n'a pas pu terminer la demande, car la mémoire est insuffisante.</span><span class="sxs-lookup"><span data-stu-id="d64d6-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="d64d6-126">HRESULT d'état</span><span class="sxs-lookup"><span data-stu-id="d64d6-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="d64d6-127">HRESULT du tableau d'états</span><span class="sxs-lookup"><span data-stu-id="d64d6-127">Status array HRESULT</span></span>|<span data-ttu-id="d64d6-128">Description</span><span class="sxs-lookup"><span data-stu-id="d64d6-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="d64d6-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="d64d6-129">S_OK</span></span>|<span data-ttu-id="d64d6-130">La fonction correspondante a été rétablie.</span><span class="sxs-lookup"><span data-stu-id="d64d6-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="d64d6-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d64d6-131">E_INVALIDARG</span></span>|<span data-ttu-id="d64d6-132">Le paramètre `moduleID` ou `methodDef` est `NULL`.</span><span class="sxs-lookup"><span data-stu-id="d64d6-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="d64d6-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="d64d6-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="d64d6-134">Le module n'est pas encore totalement chargé ou il est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="d64d6-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="d64d6-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="d64d6-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="d64d6-136">Le module spécifié a été généré dynamiquement (par exemple, par `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="d64d6-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="d64d6-137">Par conséquent, il n'est pas pris en charge par cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d64d6-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="d64d6-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="d64d6-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="d64d6-139">Le CLR ne peut pas rétablir la fonction spécifiée, car une demande de recompilation active correspondante est introuvable.</span><span class="sxs-lookup"><span data-stu-id="d64d6-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="d64d6-140">La recompilation n'a jamais demandée ou la fonction a déjà été rétablie.</span><span class="sxs-lookup"><span data-stu-id="d64d6-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="d64d6-141">Autre</span><span class="sxs-lookup"><span data-stu-id="d64d6-141">Other</span></span>|<span data-ttu-id="d64d6-142">Le système d'exploitation a retourné un échec en dehors du contrôle du CLR.</span><span class="sxs-lookup"><span data-stu-id="d64d6-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="d64d6-143">Par exemple, en cas d'échec d'un appel système visant à modifier la protection d'accès d'une page de mémoire, l'erreur du système d'exploitation s'affiche.</span><span class="sxs-lookup"><span data-stu-id="d64d6-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d64d6-144">Notes</span><span class="sxs-lookup"><span data-stu-id="d64d6-144">Remarks</span></span>  
 <span data-ttu-id="d64d6-145">Lors du prochain appel des instances de la fonction rétablie, les versions d'origine des fonctions seront exécutées.</span><span class="sxs-lookup"><span data-stu-id="d64d6-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="d64d6-146">Si une fonction est déjà en cours d'exécution, il termine l'exécution de la version en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="d64d6-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d64d6-147">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d64d6-147">Requirements</span></span>  
 <span data-ttu-id="d64d6-148">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d64d6-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d64d6-149">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d64d6-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d64d6-150">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d64d6-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d64d6-151">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d64d6-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d64d6-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d64d6-152">See Also</span></span>  
 [<span data-ttu-id="d64d6-153">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="d64d6-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="d64d6-154">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="d64d6-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d64d6-155">Profilage</span><span class="sxs-lookup"><span data-stu-id="d64d6-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
