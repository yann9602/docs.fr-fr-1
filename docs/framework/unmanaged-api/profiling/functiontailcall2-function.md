---
title: FunctionTailcall2 (fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall2
helpviewer_keywords: FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9d6ccb08bc09bea2ec9e9a49333c92da8cb5695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="d9c55-102">FunctionTailcall2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="d9c55-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="d9c55-103">Notifie le profileur que la fonction en cours d’exécution est sur le point d’exécuter un appel tail à une autre fonction et fournit des informations sur le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="d9c55-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9c55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9c55-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9c55-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d9c55-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="d9c55-106">[in] Identificateur de la fonction en cours d’exécution qui doit faire un appel tail.</span><span class="sxs-lookup"><span data-stu-id="d9c55-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `clientData`  
 <span data-ttu-id="d9c55-107">[in] Identificateur de fonction remappé, avec le profileur spécifié précédemment via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), de la fonction en cours d’exécution qui doit faire un appel tail.</span><span class="sxs-lookup"><span data-stu-id="d9c55-107">[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>  
  
 `func`  
 <span data-ttu-id="d9c55-108">[in] A `COR_PRF_FRAME_INFO` valeur qui pointe vers des informations sur le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="d9c55-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="d9c55-109">Le profileur doit le traiter en tant que handle opaque qui peut être passé au moteur d’exécution dans le [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="d9c55-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9c55-110">Notes</span><span class="sxs-lookup"><span data-stu-id="d9c55-110">Remarks</span></span>  
 <span data-ttu-id="d9c55-111">La fonction de la cible de l’appel tail utilisera le frame de pile actuel et retourne directement à l’appelant de la fonction qui fait l’appel tail.</span><span class="sxs-lookup"><span data-stu-id="d9c55-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="d9c55-112">Cela signifie qu’un [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) rappel ne sera pas émis pour une fonction qui est la cible d’un appel tail.</span><span class="sxs-lookup"><span data-stu-id="d9c55-112">This means that a [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="d9c55-113">La valeur de la `func` paramètre n’est pas valide après la `FunctionTailcall2` fonction retourne, car la valeur peut changer ou être détruite.</span><span class="sxs-lookup"><span data-stu-id="d9c55-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="d9c55-114">Le `FunctionTailcall2` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="d9c55-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="d9c55-115">L’implémentation doit utiliser le `__declspec`(`naked`) attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="d9c55-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="d9c55-116">Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="d9c55-116">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="d9c55-117">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="d9c55-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="d9c55-118">À la sortie, vous devez restaurer la pile par extraire tous les paramètres qui ont été envoyées par son appelant.</span><span class="sxs-lookup"><span data-stu-id="d9c55-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="d9c55-119">L’implémentation de `FunctionTailcall2` ne doivent pas bloquer, car il sera retarder le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="d9c55-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="d9c55-120">L’implémentation ne doit pas tenter une opération garbage collection, car la pile est peut-être pas dans un état de nom convivial de la collection garbage.</span><span class="sxs-lookup"><span data-stu-id="d9c55-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="d9c55-121">Si un garbage collection est tenté, le runtime bloque jusqu'à ce que `FunctionTailcall2` retourne.</span><span class="sxs-lookup"><span data-stu-id="d9c55-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="d9c55-122">En outre, le `FunctionTailcall2` (fonction) ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="d9c55-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9c55-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d9c55-123">Requirements</span></span>  
 <span data-ttu-id="d9c55-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9c55-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9c55-125">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="d9c55-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d9c55-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9c55-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9c55-127">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9c55-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c55-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9c55-128">See Also</span></span>  
 [<span data-ttu-id="d9c55-129">FunctionEnter2, fonction</span><span class="sxs-lookup"><span data-stu-id="d9c55-129">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="d9c55-130">FunctionLeave2, fonction</span><span class="sxs-lookup"><span data-stu-id="d9c55-130">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="d9c55-131">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="d9c55-131">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="d9c55-132">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="d9c55-132">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
