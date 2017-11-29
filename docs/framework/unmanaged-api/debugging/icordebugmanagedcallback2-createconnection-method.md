---
title: "ICorDebugManagedCallback2::CreateConnection, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.CreateConnection
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 716321508c18a415dc8e5c1c3e7e350deaf00a4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="72a57-102">ICorDebugManagedCallback2::CreateConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="72a57-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="72a57-103">Notifie le débogueur qu’une nouvelle connexion a été créée.</span><span class="sxs-lookup"><span data-stu-id="72a57-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72a57-104">Syntax</span></span>  
  
```  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72a57-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="72a57-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="72a57-106">[in] Un pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel la connexion a été créée.</span><span class="sxs-lookup"><span data-stu-id="72a57-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="72a57-107">[in] L’ID de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="72a57-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="72a57-108">[in] Pointeur vers le nom de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="72a57-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72a57-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="72a57-109">Remarks</span></span>  
 <span data-ttu-id="72a57-110">A `CreateConnection` rappel sera déclenché dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="72a57-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
-   <span data-ttu-id="72a57-111">Lorsqu’un débogueur est attaché à un processus qui contient les connexions.</span><span class="sxs-lookup"><span data-stu-id="72a57-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="72a57-112">Dans ce cas, le runtime génère et distribuer un `CreateConnection` événement et un [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) événement pour chaque connexion dans le processus.</span><span class="sxs-lookup"><span data-stu-id="72a57-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
-   <span data-ttu-id="72a57-113">Lorsqu’un hôte appelle [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) dans les [API d’hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="72a57-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72a57-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="72a57-114">Requirements</span></span>  
 <span data-ttu-id="72a57-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72a57-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72a57-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72a57-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72a57-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72a57-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72a57-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72a57-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a57-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72a57-119">See Also</span></span>  
 [<span data-ttu-id="72a57-120">ICorDebugManagedCallback2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="72a57-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="72a57-121">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="72a57-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
