---
title: "ICorDebugManagedCallback::DebuggerError, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.DebuggerError
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc92bc6a1718d9d3505443e5b13786d1a359481f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="6bd43-102">ICorDebugManagedCallback::DebuggerError, méthode</span><span class="sxs-lookup"><span data-stu-id="6bd43-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="6bd43-103">Notifie le débogueur qu’une erreur s’est produite lors de la tentative gérer un événement dans le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6bd43-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bd43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bd43-104">Syntax</span></span>  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6bd43-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6bd43-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="6bd43-106">[in] Pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel l’événement s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6bd43-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="6bd43-107">[in] La valeur HRESULT qui a été retournée par le Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="6bd43-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="6bd43-108">[in] Entier qui spécifie l’erreur CLR.</span><span class="sxs-lookup"><span data-stu-id="6bd43-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bd43-109">Notes</span><span class="sxs-lookup"><span data-stu-id="6bd43-109">Remarks</span></span>  
 <span data-ttu-id="6bd43-110">Le processus peut être placé en mode de transfert direct, selon la nature de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="6bd43-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="6bd43-111">Le `DebugError` rappel indique que les services de débogage ont été désactivés en raison d’une erreur, par conséquent, les débogueurs doivent le message d’erreur disponible à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6bd43-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="6bd43-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) sera sécurisé à l’appel, mais toutes les autres méthodes, y compris [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), ne doit pas être appelée.</span><span class="sxs-lookup"><span data-stu-id="6bd43-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="6bd43-113">Le débogueur doit utiliser des fonctionnalités du système d’exploitation pour terminer les processus.</span><span class="sxs-lookup"><span data-stu-id="6bd43-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bd43-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6bd43-114">Requirements</span></span>  
 <span data-ttu-id="6bd43-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bd43-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bd43-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bd43-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bd43-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bd43-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bd43-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bd43-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd43-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bd43-119">See Also</span></span>  
 [<span data-ttu-id="6bd43-120">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="6bd43-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
