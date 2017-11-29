---
title: "ICorDebugUnmanagedCallback::DebugEvent, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback.DebugEvent
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 008ae1bd1a5774604bf2c0f196352dcf07da6ee7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="251d2-102">ICorDebugUnmanagedCallback::DebugEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="251d2-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="251d2-103">Notifie le débogueur qu’un événement natif a été déclenché.</span><span class="sxs-lookup"><span data-stu-id="251d2-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="251d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="251d2-104">Syntax</span></span>  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="251d2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="251d2-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="251d2-106">[in] Pointeur vers l’événement natif.</span><span class="sxs-lookup"><span data-stu-id="251d2-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="251d2-107">[in] `true`, si l’interaction avec l’état de processus managé est impossible après un événement non managé, jusqu'à ce que le débogueur appelle [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="251d2-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="251d2-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="251d2-108">Remarks</span></span>  
 <span data-ttu-id="251d2-109">Si le thread en cours de débogage est un thread Win32, n’utilisez pas de tous les membres de Win32 interface de débogage.</span><span class="sxs-lookup"><span data-stu-id="251d2-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="251d2-110">Vous pouvez appeler `ICorDebugController::Continue` uniquement sur un thread Win32 et uniquement lorsque vous continuez après un événement hors-bande.</span><span class="sxs-lookup"><span data-stu-id="251d2-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="251d2-111">Le `DebugEvent` rappel ne suit pas les règles standard pour les rappels.</span><span class="sxs-lookup"><span data-stu-id="251d2-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="251d2-112">Lorsque vous appelez `DebugEvent`, le processus est dans le texte brut, état arrêté du débogage de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="251d2-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="251d2-113">Le processus ne seront pas synchronisé.</span><span class="sxs-lookup"><span data-stu-id="251d2-113">The process will not be synchronized.</span></span> <span data-ttu-id="251d2-114">Il insère automatiquement l’état synchronisé lorsque cela est nécessaire pour répondre aux demandes d’informations sur le code managé, ce qui peut provoquer d’autres imbriqués `DebugEvent` rappels.</span><span class="sxs-lookup"><span data-stu-id="251d2-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="251d2-115">Appelez [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) sur le processus pour ignorer un événement d’exception avant de poursuivre le processus.</span><span class="sxs-lookup"><span data-stu-id="251d2-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="251d2-116">Appel de cette méthode envoie DBG_CONTINUE au lieu de DBG_EXCEPTION_NOT_HANDLED sur la demande de continuer et efface automatiquement les points d’arrêt hors-bande et les exceptions de la seule étape.</span><span class="sxs-lookup"><span data-stu-id="251d2-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="251d2-117">Événements de out-of-band peuvent provenir à tout moment, même lorsque l’application en cours de débogage s’affiche arrêtée et lorsqu’un événement dans la bande en attente existe déjà.</span><span class="sxs-lookup"><span data-stu-id="251d2-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="251d2-118">Dans le .NET Framework version 2.0, le débogueur doit continuer immédiatement après un événement de point d’arrêt hors-bande.</span><span class="sxs-lookup"><span data-stu-id="251d2-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="251d2-119">Le débogueur doit être à l’aide de la [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) et [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) méthodes pour ajouter et supprimer des points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="251d2-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="251d2-120">Ces méthodes ignoreront automatiquement des points d’arrêt hors-bande.</span><span class="sxs-lookup"><span data-stu-id="251d2-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="251d2-121">Par conséquent, les points d’arrêt uniquement out-of-band distribuer doivent être des points d’arrêt bruts qui sont déjà dans le flux d’instructions, tel qu’un appel à Win32 `DebugBreak` (fonction).</span><span class="sxs-lookup"><span data-stu-id="251d2-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="251d2-122">N’essayez pas d’utiliser `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), ou tout autre membre de la [API de débogage](../../../../docs/framework/unmanaged-api/debugging/index.md).</span><span class="sxs-lookup"><span data-stu-id="251d2-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="251d2-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="251d2-123">Requirements</span></span>  
 <span data-ttu-id="251d2-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="251d2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="251d2-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="251d2-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="251d2-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="251d2-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="251d2-127">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="251d2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="251d2-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="251d2-128">See Also</span></span>  
 [<span data-ttu-id="251d2-129">ICorDebugUnmanagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="251d2-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
