---
title: ICorDebugController Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController
helpviewer_keywords: ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bde0ef86ff6304c696ad8c68fc81c0a339ed6e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontroller-interface1"></a><span data-ttu-id="1a671-102">ICorDebugController Interface1</span><span class="sxs-lookup"><span data-stu-id="1a671-102">ICorDebugController Interface1</span></span>
<span data-ttu-id="1a671-103">Représente une portée, un <xref:System.Diagnostics.Process> ou un <xref:System.AppDomain>, où le contexte d'exécution du code peut être contrôlé.</span><span class="sxs-lookup"><span data-stu-id="1a671-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a671-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1a671-104">Methods</span></span>  
  
|<span data-ttu-id="1a671-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1a671-105">Method</span></span>|<span data-ttu-id="1a671-106">Description</span><span class="sxs-lookup"><span data-stu-id="1a671-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="1a671-107">Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="1a671-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="1a671-108">Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="1a671-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="1a671-109">Continue, méthode</span><span class="sxs-lookup"><span data-stu-id="1a671-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="1a671-110">Reprend l’exécution de threads managés après un appel à [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="1a671-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="1a671-111">Detach, méthode</span><span class="sxs-lookup"><span data-stu-id="1a671-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="1a671-112">Détache le débogueur du processus ou domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="1a671-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="1a671-113">EnumerateThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="1a671-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="1a671-114">Obtient un énumérateur pour les threads managés actifs dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1a671-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="1a671-115">HasQueuedCallbacks, méthode</span><span class="sxs-lookup"><span data-stu-id="1a671-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="1a671-116">Obtient une valeur qui indique si des rappels managés sont actuellement en file d’attente pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="1a671-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="1a671-117">IsRunning, méthode</span><span class="sxs-lookup"><span data-stu-id="1a671-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="1a671-118">Obtient une valeur qui indique si les threads dans le processus en cours d’exécution librement.</span><span class="sxs-lookup"><span data-stu-id="1a671-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="1a671-119">SetAllThreadsDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="1a671-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="1a671-120">Définit l’état de débogage de tous les threads managés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1a671-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="1a671-121">Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="1a671-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="1a671-122">Effectue un arrêt coopératif sur tous les threads qui exécutent du code managé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1a671-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="1a671-123">Terminate, méthode</span><span class="sxs-lookup"><span data-stu-id="1a671-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="1a671-124">Termine le processus avec le code de sortie spécifié.</span><span class="sxs-lookup"><span data-stu-id="1a671-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a671-125">Notes</span><span class="sxs-lookup"><span data-stu-id="1a671-125">Remarks</span></span>  
 <span data-ttu-id="1a671-126">Si `ICorDebugController` est contrôle un processus, l’étendue inclut tous les threads du processus.</span><span class="sxs-lookup"><span data-stu-id="1a671-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="1a671-127">Si `ICorDebugController` est contrôle un domaine d’application, la portée inclut uniquement les threads de ce domaine d’application particulier.</span><span class="sxs-lookup"><span data-stu-id="1a671-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a671-128">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="1a671-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a671-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1a671-129">Requirements</span></span>  
 <span data-ttu-id="1a671-130">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a671-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a671-131">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a671-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a671-132">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a671-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a671-133">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a671-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a671-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a671-134">See Also</span></span>  
 [<span data-ttu-id="1a671-135">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1a671-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
