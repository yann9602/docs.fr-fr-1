---
title: FunctionEnter3, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter3
helpviewer_keywords: FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 08ab1b6adc3d4038a57a187519e96c7a07f1e6ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter3-function"></a><span data-ttu-id="ef6c5-102">FunctionEnter3, fonction</span><span class="sxs-lookup"><span data-stu-id="ef6c5-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="ef6c5-103">Notifie le profileur que le contrôle est passé à une fonction.</span><span class="sxs-lookup"><span data-stu-id="ef6c5-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef6c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef6c5-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef6c5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ef6c5-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="ef6c5-106">[in] Identificateur de la fonction à laquelle le contrôle est passé.</span><span class="sxs-lookup"><span data-stu-id="ef6c5-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef6c5-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="ef6c5-107">Remarks</span></span>  
 <span data-ttu-id="ef6c5-108">Le `FunctionEnter3` fonction de rappel notifie le profileur que les fonctions sont appelées, mais sont l’inspection des arguments non prise en charge.</span><span class="sxs-lookup"><span data-stu-id="ef6c5-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="ef6c5-109">Utilisez le [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) pour enregistrer votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="ef6c5-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="ef6c5-110">Le `FunctionEnter3` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="ef6c5-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="ef6c5-111">L’implémentation doit utiliser le `__declspec(naked)` attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="ef6c5-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="ef6c5-112">Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="ef6c5-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="ef6c5-113">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="ef6c5-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="ef6c5-114">À la sortie, vous devez restaurer la pile par extraire tous les paramètres qui ont été envoyées par son appelant.</span><span class="sxs-lookup"><span data-stu-id="ef6c5-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef6c5-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ef6c5-115">Requirements</span></span>  
 <span data-ttu-id="ef6c5-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef6c5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef6c5-117">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ef6c5-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ef6c5-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef6c5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef6c5-119">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef6c5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef6c5-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef6c5-120">See Also</span></span>  
 [<span data-ttu-id="ef6c5-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="ef6c5-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="ef6c5-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="ef6c5-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="ef6c5-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ef6c5-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="ef6c5-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ef6c5-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="ef6c5-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ef6c5-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="ef6c5-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="ef6c5-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="ef6c5-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ef6c5-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="ef6c5-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="ef6c5-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="ef6c5-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="ef6c5-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="ef6c5-130">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="ef6c5-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
