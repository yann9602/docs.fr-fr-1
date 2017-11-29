---
title: ICorDebugProcess Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess
helpviewer_keywords: ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee526a79d89a9e4e3483daa07a512b6b7f920e70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess-interface1"></a><span data-ttu-id="fb265-102">ICorDebugProcess Interface1</span><span class="sxs-lookup"><span data-stu-id="fb265-102">ICorDebugProcess Interface1</span></span>
<span data-ttu-id="fb265-103">Représente un processus qui exécute le code managé.</span><span class="sxs-lookup"><span data-stu-id="fb265-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="fb265-104">Cette interface est une sous-classe de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="fb265-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb265-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="fb265-105">Methods</span></span>  
  
|<span data-ttu-id="fb265-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="fb265-106">Method</span></span>|<span data-ttu-id="fb265-107">Description</span><span class="sxs-lookup"><span data-stu-id="fb265-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb265-108">ClearCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="fb265-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="fb265-109">Efface l’exception non managée actuelle sur le thread donné.</span><span class="sxs-lookup"><span data-stu-id="fb265-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="fb265-110">EnableLogMessages (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="fb265-111">Active ou désactive l’envoi de messages de journal au débogueur.</span><span class="sxs-lookup"><span data-stu-id="fb265-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="fb265-112">EnumerateAppDomains (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="fb265-113">Énumère tous les domaines d’application dans le processus.</span><span class="sxs-lookup"><span data-stu-id="fb265-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="fb265-114">EnumerateObjects (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="fb265-115">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="fb265-115">Not implemented.</span></span>|  
|[<span data-ttu-id="fb265-116">GetHandle (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="fb265-117">Obtient un handle vers le processus.</span><span class="sxs-lookup"><span data-stu-id="fb265-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="fb265-118">GetHelperThreadID (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="fb265-119">Obtient l’ID de thread de système d’exploitation (OS) pour le thread d’assistance interne du débogueur.</span><span class="sxs-lookup"><span data-stu-id="fb265-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="fb265-120">GetID (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="fb265-121">Obtient l’ID de système d’exploitation (OS) du processus.</span><span class="sxs-lookup"><span data-stu-id="fb265-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="fb265-122">GetObject (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="fb265-123">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="fb265-123">Not implemented.</span></span>|  
|[<span data-ttu-id="fb265-124">GetThread (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="fb265-125">Obtient l’instance ICorDebugThread qui a le thread du système d’exploitation spécifié ID.</span><span class="sxs-lookup"><span data-stu-id="fb265-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="fb265-126">GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="fb265-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="fb265-127">Obtient le contexte pour le thread donné.</span><span class="sxs-lookup"><span data-stu-id="fb265-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="fb265-128">IsOSSuspended (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="fb265-129">Détermine si le thread a été interrompu à la suite du débogueur qui arrête le processus.</span><span class="sxs-lookup"><span data-stu-id="fb265-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="fb265-130">IsTransitionStub (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="fb265-131">Détermine si une adresse est à l’intérieur d’un stub qui provoquera une transition vers du code managé.</span><span class="sxs-lookup"><span data-stu-id="fb265-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="fb265-132">ModifyLogSwitch (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="fb265-133">Définit le niveau de gravité du commutateur de journal spécifié.</span><span class="sxs-lookup"><span data-stu-id="fb265-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="fb265-134">ReadMemory (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="fb265-135">Lit la mémoire du processus.</span><span class="sxs-lookup"><span data-stu-id="fb265-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="fb265-136">SetThreadContext (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="fb265-137">Définit le contexte pour le thread donné.</span><span class="sxs-lookup"><span data-stu-id="fb265-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="fb265-138">ThreadForFiberCookie (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="fb265-139">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="fb265-139">Deprecated.</span></span>|  
|[<span data-ttu-id="fb265-140">WriteMemory (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb265-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="fb265-141">Écrit des données dans une zone de mémoire dans le processus.</span><span class="sxs-lookup"><span data-stu-id="fb265-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb265-142">Remarques</span><span class="sxs-lookup"><span data-stu-id="fb265-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb265-143">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="fb265-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb265-144">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fb265-144">Requirements</span></span>  
 <span data-ttu-id="fb265-145">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb265-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb265-146">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb265-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb265-147">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb265-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb265-148">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb265-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb265-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb265-149">See Also</span></span>  
 [<span data-ttu-id="fb265-150">ICorDebug (Interface)</span><span class="sxs-lookup"><span data-stu-id="fb265-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="fb265-151">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="fb265-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
