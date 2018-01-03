---
title: "ICorDebugManagedCallback2::DestroyConnection, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.DestroyConnection
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9d87f3c57e72c567be582ba2ac78589fa2e3357
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="85ba7-102">ICorDebugManagedCallback2::DestroyConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="85ba7-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="85ba7-103">Notifie le débogueur que la connexion spécifiée a été arrêtée.</span><span class="sxs-lookup"><span data-stu-id="85ba7-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85ba7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85ba7-104">Syntax</span></span>  
  
```  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85ba7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="85ba7-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="85ba7-106">[in] Pointeur vers un objet ICorDebugProcess qui représente le processus contenant la connexion qui a été détruite.</span><span class="sxs-lookup"><span data-stu-id="85ba7-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="85ba7-107">[in] L’ID de la connexion qui a été détruite.</span><span class="sxs-lookup"><span data-stu-id="85ba7-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85ba7-108">Notes</span><span class="sxs-lookup"><span data-stu-id="85ba7-108">Remarks</span></span>  
 <span data-ttu-id="85ba7-109">A `DestroyConnection` rappel sera déclenché lorsqu’un hôte appelle [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) dans les [API d’hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="85ba7-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85ba7-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="85ba7-110">Requirements</span></span>  
 <span data-ttu-id="85ba7-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85ba7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85ba7-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85ba7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85ba7-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85ba7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85ba7-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85ba7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ba7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85ba7-115">See Also</span></span>  
 [<span data-ttu-id="85ba7-116">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="85ba7-116">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="85ba7-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="85ba7-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
