---
title: "ICorDebugManagedCallback::LogSwitch, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LogSwitch
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9480b3123abceb6a108e2e00c7304829188cd162
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="9f0a9-102">ICorDebugManagedCallback::LogSwitch, méthode</span><span class="sxs-lookup"><span data-stu-id="9f0a9-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="9f0a9-103">Notifie le débogueur qu’un thread du common language runtime (CLR) géré a appelé une méthode la <xref:System.Diagnostics.Switch> classe pour créer, modifier ou supprimer un commutateur de débogage/suivi.</span><span class="sxs-lookup"><span data-stu-id="9f0a9-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f0a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f0a9-104">Syntax</span></span>  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f0a9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9f0a9-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="9f0a9-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread managé qui a créé, modifié ou supprimé un commutateur de débogage/suivi.</span><span class="sxs-lookup"><span data-stu-id="9f0a9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="9f0a9-107">[in] Pointeur vers un objet ICorDebugThread qui représente le thread managé.</span><span class="sxs-lookup"><span data-stu-id="9f0a9-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="9f0a9-108">[in] Une valeur qui indique le niveau de gravité du message descriptif qui a été écrite dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="9f0a9-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="9f0a9-109">[in] Une valeur de la [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) énumération qui indique l’opération effectuée sur le commutateur de débogage/suivi.</span><span class="sxs-lookup"><span data-stu-id="9f0a9-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="9f0a9-110">[in] Pointeur vers le nom du commutateur de débogage/suivi.</span><span class="sxs-lookup"><span data-stu-id="9f0a9-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="9f0a9-111">[in] Pointeur vers le nom du parent du commutateur de débogage/suivi.</span><span class="sxs-lookup"><span data-stu-id="9f0a9-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f0a9-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9f0a9-112">Requirements</span></span>  
 <span data-ttu-id="9f0a9-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f0a9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f0a9-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f0a9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f0a9-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f0a9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f0a9-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f0a9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f0a9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f0a9-117">See Also</span></span>  
 [<span data-ttu-id="9f0a9-118">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="9f0a9-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
