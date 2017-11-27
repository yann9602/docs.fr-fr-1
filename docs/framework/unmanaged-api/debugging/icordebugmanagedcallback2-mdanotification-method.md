---
title: "ICorDebugManagedCallback2::MDANotification, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.MDANotification
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aeddab575f6667dbd27ab3474ae9c6e00dd05750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="db1e4-102">ICorDebugManagedCallback2::MDANotification, méthode</span><span class="sxs-lookup"><span data-stu-id="db1e4-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="db1e4-103">Fournit une notification indiquant que l’exécution du code a rencontré un assistant débogage managé (MDA) dans l’application en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="db1e4-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db1e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db1e4-104">Syntax</span></span>  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db1e4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="db1e4-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="db1e4-106">[in] Pointeur vers un ICorDebugController (interface) qui expose le processus ou le domaine d’application dans lequel l’Assistant Débogage MANAGÉ s’est produite.</span><span class="sxs-lookup"><span data-stu-id="db1e4-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="db1e4-107">Un débogueur n’a pas doit faire d’hypothèses concernant si le contrôleur est un processus ou un domaine d’application, bien qu’il puisse toujours interroger l’interface pour effectuer une détermination.</span><span class="sxs-lookup"><span data-stu-id="db1e4-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="db1e4-108">[in] Pointeur vers une interface ICorDebugThread qui expose le thread managé sur lequel l’événement de débogage s’est produite.</span><span class="sxs-lookup"><span data-stu-id="db1e4-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="db1e4-109">Si l’Assistant Débogage MANAGÉ s’est produite sur une fonction non managée de thread, la valeur de `pThread` sera null.</span><span class="sxs-lookup"><span data-stu-id="db1e4-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="db1e4-110">Vous devez obtenir l’ID de thread de système d’exploitation (OS) à partir de l’objet MDA lui-même.</span><span class="sxs-lookup"><span data-stu-id="db1e4-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="db1e4-111">[in] Un pointeur vers un [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface qui expose les informations MDA.</span><span class="sxs-lookup"><span data-stu-id="db1e4-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db1e4-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="db1e4-112">Remarks</span></span>  
 <span data-ttu-id="db1e4-113">Un MDA est un avertissement heuristique et ne nécessite aucune action du débogueur explicite, à l’exception d’appel [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) pour reprendre l’exécution de l’application est en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="db1e4-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="db1e4-114">Le common language runtime (CLR) peut déterminer quels MDA sont déclenchés et les données qui sont dans n’importe quel MDA donné à tout moment.</span><span class="sxs-lookup"><span data-stu-id="db1e4-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="db1e4-115">Par conséquent, les débogueurs ne doivent pas générer de fonctionnalités nécessitant des modèles MDA spécifiques.</span><span class="sxs-lookup"><span data-stu-id="db1e4-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="db1e4-116">Assistants Débogage managé peut être en file d’attente et déclenchés juste après que l’Assistant Débogage MANAGÉ est rencontré.</span><span class="sxs-lookup"><span data-stu-id="db1e4-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="db1e4-117">Cela peut se produire si le runtime doit attendre jusqu'à ce qu’il atteigne un point sans risque pour déclencher le MDA, au lieu de déclencher lorsqu’elle rencontre.</span><span class="sxs-lookup"><span data-stu-id="db1e4-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="db1e4-118">Cela signifie également que le runtime peut déclencher un nombre d’Assistants Débogage managé dans un seul jeu de rappels en file d’attente (similaires à une opération d’événement « liaison »).</span><span class="sxs-lookup"><span data-stu-id="db1e4-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="db1e4-119">Un débogueur doit libérer la référence à un `ICorDebugMDA` instance immédiatement après le retour à partir de la `MDANotification` rappel, pour permettre au CLR de recycler la mémoire consommée par un Assistant Débogage MANAGÉ.</span><span class="sxs-lookup"><span data-stu-id="db1e4-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="db1e4-120">Libérer l’instance peut améliorer les performances si déclenchent des nombreux MDA.</span><span class="sxs-lookup"><span data-stu-id="db1e4-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db1e4-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="db1e4-121">Requirements</span></span>  
 <span data-ttu-id="db1e4-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db1e4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db1e4-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db1e4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db1e4-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db1e4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db1e4-125">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db1e4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db1e4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db1e4-126">See Also</span></span>  
 [<span data-ttu-id="db1e4-127">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="db1e4-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="db1e4-128">ICorDebugManagedCallback2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="db1e4-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="db1e4-129">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="db1e4-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
