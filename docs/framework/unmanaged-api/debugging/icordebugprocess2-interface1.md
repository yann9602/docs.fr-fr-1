---
title: ICorDebugProcess2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2
helpviewer_keywords: ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80f6c35ba2ef2ec74293d0f025ddf20254f504a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2-interface1"></a><span data-ttu-id="095f9-102">ICorDebugProcess2 Interface1</span><span class="sxs-lookup"><span data-stu-id="095f9-102">ICorDebugProcess2 Interface1</span></span>
<span data-ttu-id="095f9-103">Extension logique de l’interface ICorDebugProcess, qui représente un processus en cours d’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="095f9-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="095f9-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="095f9-104">Methods</span></span>  
  
|<span data-ttu-id="095f9-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="095f9-105">Method</span></span>|<span data-ttu-id="095f9-106">Description</span><span class="sxs-lookup"><span data-stu-id="095f9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="095f9-107">ClearUnmanagedBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="095f9-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="095f9-108">Supprime un point d’arrêt à l’offset spécifié qui a été défini par un appel précédent à `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="095f9-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="095f9-109">GetDesiredNGENCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="095f9-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="095f9-110">Obtient les indicateurs qui doivent être définis pour le common language runtime (CLR) pour charger l’image dans le processus référencé par ce `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="095f9-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="095f9-111">GetReferenceValueFromGCHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="095f9-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="095f9-112">Obtient un pointeur de référence à l’objet managé spécifié qui a un garbage collection à gérer.</span><span class="sxs-lookup"><span data-stu-id="095f9-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="095f9-113">GetThreadForTaskID, méthode</span><span class="sxs-lookup"><span data-stu-id="095f9-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="095f9-114">Obtient le thread sur lequel s’exécute la tâche avec l’identificateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="095f9-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="095f9-115">GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="095f9-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="095f9-116">Obtient la version du CLR sur laquelle le processus en cours de débogage s’exécute.</span><span class="sxs-lookup"><span data-stu-id="095f9-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="095f9-117">SetDesiredNGENCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="095f9-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="095f9-118">Définit les indicateurs qui sont requis pour le compilateur juste-à-temps (JIT) charger une image dans le processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="095f9-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="095f9-119">SetUnmanagedBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="095f9-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="095f9-120">Définit un point d’arrêt non managé à l’offset d’image native spécifié.</span><span class="sxs-lookup"><span data-stu-id="095f9-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="095f9-121">Notes</span><span class="sxs-lookup"><span data-stu-id="095f9-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="095f9-122">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="095f9-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="095f9-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="095f9-123">Requirements</span></span>  
 <span data-ttu-id="095f9-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="095f9-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="095f9-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="095f9-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="095f9-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="095f9-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="095f9-127">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="095f9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="095f9-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="095f9-128">See Also</span></span>  
 [<span data-ttu-id="095f9-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="095f9-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
