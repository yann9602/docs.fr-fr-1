---
title: FunctionEnter2 (fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter2
helpviewer_keywords: FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0aa1d98021dcbfc38721d7f30ad305065dced605
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter2-function"></a><span data-ttu-id="a8d03-102">FunctionEnter2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="a8d03-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="a8d03-103">Notifie le profileur que le contrôle est passé à une fonction et fournit des informations sur la pile des arguments de fonction et de frame.</span><span class="sxs-lookup"><span data-stu-id="a8d03-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="a8d03-104">Cette fonction remplace la [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="a8d03-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8d03-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8d03-105">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8d03-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a8d03-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="a8d03-107">[in] Identificateur de la fonction à laquelle le contrôle est passé.</span><span class="sxs-lookup"><span data-stu-id="a8d03-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="a8d03-108">[in] Identificateur de fonction remappé, avec le profileur spécifié précédemment à l’aide de la [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="a8d03-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="a8d03-109">[in] A `COR_PRF_FRAME_INFO` valeur qui pointe vers des informations sur le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="a8d03-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="a8d03-110">Le profileur doit le traiter en tant que handle opaque qui peut être passé au moteur d’exécution dans le [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="a8d03-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="a8d03-111">[in] Un pointeur vers un [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure qui spécifie les emplacements en mémoire des arguments de la fonction.</span><span class="sxs-lookup"><span data-stu-id="a8d03-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="a8d03-112">Pour accéder aux informations d’argument, la `COR_PRF_ENABLE_FUNCTION_ARGS` indicateur doit être défini.</span><span class="sxs-lookup"><span data-stu-id="a8d03-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="a8d03-113">Le profileur peut utiliser le [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement.</span><span class="sxs-lookup"><span data-stu-id="a8d03-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8d03-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="a8d03-114">Remarks</span></span>  
 <span data-ttu-id="a8d03-115">Les valeurs de la `func` et `argumentInfo` paramètres ne sont pas valides après le `FunctionEnter2` fonction retourne, car les valeurs peuvent changer ou être détruites.</span><span class="sxs-lookup"><span data-stu-id="a8d03-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="a8d03-116">Le `FunctionEnter2` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="a8d03-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="a8d03-117">L’implémentation doit utiliser le `__declspec`(`naked`) attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="a8d03-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="a8d03-118">Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="a8d03-118">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="a8d03-119">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="a8d03-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="a8d03-120">À la sortie, vous devez restaurer la pile par extraire tous les paramètres qui ont été envoyées par son appelant.</span><span class="sxs-lookup"><span data-stu-id="a8d03-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a8d03-121">L’implémentation de `FunctionEnter2` ne doivent pas bloquer, car il sera retarder le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a8d03-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="a8d03-122">L’implémentation ne doit pas tenter une opération garbage collection, car la pile est peut-être pas dans un état de nom convivial de la collection garbage.</span><span class="sxs-lookup"><span data-stu-id="a8d03-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a8d03-123">Si un garbage collection est tenté, le runtime bloque jusqu'à ce que `FunctionEnter2` retourne.</span><span class="sxs-lookup"><span data-stu-id="a8d03-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="a8d03-124">En outre, le `FunctionEnter2` (fonction) ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="a8d03-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8d03-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a8d03-125">Requirements</span></span>  
 <span data-ttu-id="a8d03-126">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8d03-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8d03-127">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a8d03-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a8d03-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8d03-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8d03-129">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8d03-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d03-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8d03-130">See Also</span></span>  
 [<span data-ttu-id="a8d03-131">FunctionLeave2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="a8d03-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="a8d03-132">FunctionTailcall2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="a8d03-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="a8d03-133">SetEnterLeaveFunctionHooks2 (méthode)</span><span class="sxs-lookup"><span data-stu-id="a8d03-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="a8d03-134">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="a8d03-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
