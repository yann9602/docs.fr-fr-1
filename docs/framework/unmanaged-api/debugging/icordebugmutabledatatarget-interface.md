---
title: ICorDebugMutableDataTarget, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef1c0b7a56f6bd1f7e87650b72dfe8b1411ef7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="1a0ee-102">ICorDebugMutableDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="1a0ee-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="1a0ee-103">Étend la [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface pour prendre en charge des cibles de données mutables.</span><span class="sxs-lookup"><span data-stu-id="1a0ee-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a0ee-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1a0ee-104">Methods</span></span>  
  
|<span data-ttu-id="1a0ee-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1a0ee-105">Method</span></span>|<span data-ttu-id="1a0ee-106">Description</span><span class="sxs-lookup"><span data-stu-id="1a0ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a0ee-107">ContinueStatusChanged (méthode)</span><span class="sxs-lookup"><span data-stu-id="1a0ee-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="1a0ee-108">Modifie l'état de continuation de l'événement de débogage en suspens sur le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="1a0ee-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="1a0ee-109">SetThreadContext (méthode)</span><span class="sxs-lookup"><span data-stu-id="1a0ee-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="1a0ee-110">Définit le contexte (valeurs de registre) d'un thread.</span><span class="sxs-lookup"><span data-stu-id="1a0ee-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="1a0ee-111">WriteVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="1a0ee-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="1a0ee-112">Écrit la mémoire dans l'espace d'adressage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="1a0ee-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a0ee-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="1a0ee-113">Remarks</span></span>  
 <span data-ttu-id="1a0ee-114">Cette extension pour le [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface peut être implémentée par les outils de débogage qui souhaitent modifier le processus cible (par exemple, pour effectuer un débogage INVASIF en direct).</span><span class="sxs-lookup"><span data-stu-id="1a0ee-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="1a0ee-115">Toutes ces méthodes sont facultatives dans le sens où aucune fonctionnalité de débogage principale basée sur l'inspection n'est perdue en cas de non-implémentation de cette interface ou en cas d'échec des appels à ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="1a0ee-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="1a0ee-116">Tout `HRESULT` d'échec issu de ces méthodes se propage sous la forme d'un `HRESULT` de l'appel de méthode ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="1a0ee-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="1a0ee-117">Notez qu'un seul appel de méthode ICorDebug peut entraîner plusieurs mutations et qu'il n'existe aucun mécanisme garantissant l'application en mode transactionnel (tout ou rien) des mutations connexes.</span><span class="sxs-lookup"><span data-stu-id="1a0ee-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="1a0ee-118">Cela signifie que si une mutation échoue après la réussite d'autres mutations (pour le même appel ICorDebug), le processus cible peut se retrouver dans un état incohérent pouvant nuire à la fiabilité du débogage.</span><span class="sxs-lookup"><span data-stu-id="1a0ee-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a0ee-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1a0ee-119">Requirements</span></span>  
 <span data-ttu-id="1a0ee-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a0ee-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a0ee-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a0ee-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a0ee-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a0ee-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a0ee-123">**Versions du .NET framework :**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a0ee-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a0ee-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a0ee-124">See Also</span></span>  
 [<span data-ttu-id="1a0ee-125">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1a0ee-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1a0ee-126">Débogage</span><span class="sxs-lookup"><span data-stu-id="1a0ee-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)