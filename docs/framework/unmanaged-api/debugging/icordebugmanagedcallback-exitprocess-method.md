---
title: "ICorDebugManagedCallback::ExitProcess, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ExitProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ff80462c722a84ef68ac8c6703ded3e7138a1939
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="7f81d-102">ICorDebugManagedCallback::ExitProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="7f81d-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="7f81d-103">Notifie le débogueur qu’un processus s’est arrêté.</span><span class="sxs-lookup"><span data-stu-id="7f81d-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f81d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f81d-104">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f81d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7f81d-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="7f81d-106">[in] Pointeur vers un objet ICorDebugProcess qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="7f81d-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f81d-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="7f81d-107">Remarks</span></span>  
 <span data-ttu-id="7f81d-108">Vous ne pouvez pas continuer à partir d’un `ExitProcess` événement.</span><span class="sxs-lookup"><span data-stu-id="7f81d-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="7f81d-109">Cet événement peut être activé en mode asynchrone et d’autres événements alors que le processus semble arrêté.</span><span class="sxs-lookup"><span data-stu-id="7f81d-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="7f81d-110">Cela peut se produire si le processus se termine lorsque l’état arrêté, généralement en raison d’une force externe.</span><span class="sxs-lookup"><span data-stu-id="7f81d-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="7f81d-111">Si le common language runtime (CLR) distribue déjà un rappel managé, cet événement sera retardé en attendant une fois que le rappel a retourné.</span><span class="sxs-lookup"><span data-stu-id="7f81d-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="7f81d-112">Le `ExitProcess` événement est le seul événement de sortie/déchargement qui est appelé lors de l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="7f81d-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f81d-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7f81d-113">Requirements</span></span>  
 <span data-ttu-id="7f81d-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f81d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f81d-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f81d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f81d-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f81d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f81d-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f81d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f81d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f81d-118">See Also</span></span>  
 [<span data-ttu-id="7f81d-119">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="7f81d-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
