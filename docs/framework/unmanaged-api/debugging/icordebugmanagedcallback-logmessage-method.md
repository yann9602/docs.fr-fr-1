---
title: "ICorDebugManagedCallback::LogMessage, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LogMessage
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d62204e8fb2e1fabae4183bbcf7b4d42b832d2b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="2c0f2-102">ICorDebugManagedCallback::LogMessage, méthode</span><span class="sxs-lookup"><span data-stu-id="2c0f2-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="2c0f2-103">Notifie le débogueur qu’un thread du common language runtime (CLR) géré a appelé une méthode la <xref:System.Diagnostics.EventLog> classe journaliser un événement.</span><span class="sxs-lookup"><span data-stu-id="2c0f2-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c0f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c0f2-104">Syntax</span></span>  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c0f2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2c0f2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="2c0f2-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread managé qui a consigné l’événement.</span><span class="sxs-lookup"><span data-stu-id="2c0f2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="2c0f2-107">[in] Pointeur vers un objet ICorDebugThread qui représente le thread managé.</span><span class="sxs-lookup"><span data-stu-id="2c0f2-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="2c0f2-108">[in] Une valeur de la [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) énumération qui indique le niveau de gravité du message descriptif qui a été écrite dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="2c0f2-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="2c0f2-109">[in] Pointeur vers le nom du commutateur de suivi.</span><span class="sxs-lookup"><span data-stu-id="2c0f2-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="2c0f2-110">[in] Pointeur vers le message qui a été écrite dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="2c0f2-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c0f2-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2c0f2-111">Requirements</span></span>  
 <span data-ttu-id="2c0f2-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c0f2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c0f2-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c0f2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c0f2-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c0f2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c0f2-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c0f2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0f2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c0f2-116">See Also</span></span>  
 [<span data-ttu-id="2c0f2-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="2c0f2-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
