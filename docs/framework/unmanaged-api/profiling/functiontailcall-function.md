---
title: FunctionTailcall (fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall
helpviewer_keywords: FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8bc0d72ad9c11cb36803cc606b460181b44033f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="functiontailcall-function"></a><span data-ttu-id="15f6e-102">FunctionTailcall (fonction)</span><span class="sxs-lookup"><span data-stu-id="15f6e-102">FunctionTailcall Function</span></span>
<span data-ttu-id="15f6e-103">Notifie le profileur que la fonction en cours d’exécution est sur le point d’exécuter un appel tail à une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="15f6e-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15f6e-104">Le `FunctionTailcall` fonction est déconseillée dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="15f6e-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="15f6e-105">Il continue de fonctionner, mais entraîne une baisse des performances.</span><span class="sxs-lookup"><span data-stu-id="15f6e-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="15f6e-106">Utilisez le [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) de fonction à la place.</span><span class="sxs-lookup"><span data-stu-id="15f6e-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15f6e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15f6e-107">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15f6e-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="15f6e-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="15f6e-109">[in] Identificateur de la fonction en cours d’exécution qui doit faire un appel tail.</span><span class="sxs-lookup"><span data-stu-id="15f6e-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15f6e-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="15f6e-110">Remarks</span></span>  
 <span data-ttu-id="15f6e-111">La fonction de la cible de l’appel tail utilisera le frame de pile actuel et retourne directement à l’appelant de la fonction qui fait l’appel tail.</span><span class="sxs-lookup"><span data-stu-id="15f6e-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="15f6e-112">Cela signifie qu’un [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) rappel ne sera pas émis pour une fonction qui est la cible d’un appel tail.</span><span class="sxs-lookup"><span data-stu-id="15f6e-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="15f6e-113">Le `FunctionTailcall` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="15f6e-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="15f6e-114">L’implémentation doit utiliser le `__declspec`(`naked`) attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="15f6e-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="15f6e-115">Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="15f6e-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="15f6e-116">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="15f6e-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="15f6e-117">À la sortie, vous devez restaurer la pile par extraire tous les paramètres qui ont été envoyées par son appelant.</span><span class="sxs-lookup"><span data-stu-id="15f6e-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="15f6e-118">L’implémentation de `FunctionTailcall` ne doivent pas bloquer, car il sera retarder le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="15f6e-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="15f6e-119">L’implémentation ne doit pas tenter une opération garbage collection, car la pile est peut-être pas dans un état de nom convivial de la collection garbage.</span><span class="sxs-lookup"><span data-stu-id="15f6e-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="15f6e-120">Si un garbage collection est tenté, le runtime bloque jusqu'à ce que `FunctionTailcall` retourne.</span><span class="sxs-lookup"><span data-stu-id="15f6e-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="15f6e-121">En outre, le `FunctionTailcall` (fonction) ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="15f6e-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15f6e-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="15f6e-122">Requirements</span></span>  
 <span data-ttu-id="15f6e-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15f6e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15f6e-124">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="15f6e-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="15f6e-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15f6e-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15f6e-126">**Versions du .NET framework :** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="15f6e-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f6e-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15f6e-127">See Also</span></span>  
 [<span data-ttu-id="15f6e-128">FunctionEnter2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="15f6e-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="15f6e-129">FunctionLeave2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="15f6e-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="15f6e-130">SetEnterLeaveFunctionHooks2 (méthode)</span><span class="sxs-lookup"><span data-stu-id="15f6e-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="15f6e-131">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="15f6e-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
