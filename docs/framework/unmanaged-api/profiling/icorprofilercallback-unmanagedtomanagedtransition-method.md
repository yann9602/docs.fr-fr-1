---
title: "ICorProfilerCallback::UnmanagedToManagedTransition, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.UnmanagedToManagedTransition
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 45a2ceb53263e317c5c72695d6bc1e93f8f70bbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="a1595-102">ICorProfilerCallback::UnmanagedToManagedTransition, méthode</span><span class="sxs-lookup"><span data-stu-id="a1595-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="a1595-103">Notifie le profileur qu’une transition du code non managé au code managé s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a1595-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1595-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1595-104">Syntax</span></span>  
  
```  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1595-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1595-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a1595-106">[in] L’ID de la fonction est appelée.</span><span class="sxs-lookup"><span data-stu-id="a1595-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="a1595-107">[in] Une valeur de la [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) énumération qui indique si la transition s’est produite en raison d’un appel au code managé à partir de code non managé, ou en raison d’un retour d’une fonction non managée est appelée par un objet managé.</span><span class="sxs-lookup"><span data-stu-id="a1595-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1595-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="a1595-108">Remarks</span></span>  
 <span data-ttu-id="a1595-109">Si la valeur de `reason` est COR_PRF_TRANSITION_RETURN et `functionId` n’est ne pas null, la fonction ID est celle de la fonction non managée et n’a jamais été compilé à l’aide du compilateur juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="a1595-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="a1595-110">Fonctions non managées ont des informations de base associées, telles qu’un nom et des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a1595-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="a1595-111">Si la valeur de `reason` est COR_PRF_TRANSITION_CALL, il est possible que la fonction appelée (autrement dit, la fonction managée) n’a pas encore été compilé par JIT.</span><span class="sxs-lookup"><span data-stu-id="a1595-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1595-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a1595-112">Requirements</span></span>  
 <span data-ttu-id="a1595-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1595-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1595-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1595-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1595-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1595-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1595-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1595-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1595-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1595-117">See Also</span></span>  
 [<span data-ttu-id="a1595-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a1595-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a1595-119">ManagedToUnmanagedTransition (méthode)</span><span class="sxs-lookup"><span data-stu-id="a1595-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)  
 [<span data-ttu-id="a1595-120">Utilisation d’un PInvoke explicite en C++ (attribut DllImport)</span><span class="sxs-lookup"><span data-stu-id="a1595-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)  
 [<span data-ttu-id="a1595-121">Utilisation de l’interopérabilité C++ (PInvoke implicite)</span><span class="sxs-lookup"><span data-stu-id="a1595-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
