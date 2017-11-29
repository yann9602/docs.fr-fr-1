---
title: FunctionEnter3WithInfo, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3WithInfo
api_location: mscorwks.cll
api_type: COM
f1_keywords: FunctionEnter3WithInfo
helpviewer_keywords: FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 37cdf823cc910dd1cebcb587d2616406a842fef2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="4e5bb-102">FunctionEnter3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="4e5bb-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="4e5bb-103">Notifie le profileur que le contrôle est passé à une fonction et fournit un handle qui peut être passé à la [ICorProfilerInfo3::GetFunctionEnter3Info, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) pour récupérer les arguments de fonction et de frame de pile.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e5bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e5bb-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e5bb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4e5bb-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="4e5bb-106">[in] Identificateur de la fonction à laquelle le contrôle est passé.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-106">[in] The identifier of the function to which control is passed.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="4e5bb-107">[in] Handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="4e5bb-108">Ce handle est uniquement valide pendant le rappel auquel il est passé.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e5bb-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="4e5bb-109">Remarks</span></span>  
 <span data-ttu-id="4e5bb-110">Le `FunctionEnter3WithInfo` méthode de rappel notifie le profileur que les fonctions sont appelées et permet au profileur d’utiliser le [ICorProfilerInfo3::GetFunctionEnter3Info, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) pour inspecter des valeurs d’argument.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="4e5bb-111">Pour accéder aux informations de l’argument, la `COR_PRF_ENABLE_FUNCTION_ARGS` indicateur doit être défini.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="4e5bb-112">Le profileur peut utiliser le [ICorProfilerInfo::SetEventMask, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser le [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="4e5bb-113">Le `FunctionEnter3WithInfo` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="4e5bb-114">L’implémentation doit utiliser le `__declspec(naked)` attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="4e5bb-115">Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="4e5bb-116">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="4e5bb-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="4e5bb-117">À la sortie, vous devez restaurer la pile par extraire tous les paramètres qui ont été envoyées par son appelant.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="4e5bb-118">L’implémentation de `FunctionEnter3WithInfo` ne doivent pas bloquer, car il sera retarder le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="4e5bb-119">L’implémentation ne doit pas tenter de garbage collection, car la pile est peut-être pas dans un état de nom convivial de la collection garbage.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="4e5bb-120">Si un garbage collection est tenté, le runtime bloque jusqu'à ce que `FunctionEnter3WithInfo` retourne.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="4e5bb-121">Le `FunctionEnter3WithInfo` fonction ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée en aucune façon.</span><span class="sxs-lookup"><span data-stu-id="4e5bb-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e5bb-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4e5bb-122">Requirements</span></span>  
 <span data-ttu-id="4e5bb-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e5bb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e5bb-124">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="4e5bb-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4e5bb-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e5bb-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e5bb-126">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e5bb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e5bb-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e5bb-127">See Also</span></span>  
 [<span data-ttu-id="4e5bb-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="4e5bb-128">GetFunctionEnter3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)  
 [<span data-ttu-id="4e5bb-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="4e5bb-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="4e5bb-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="4e5bb-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="4e5bb-131">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="4e5bb-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
