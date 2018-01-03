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
ms.workload: dotnet
ms.openlocfilehash: beb4dc25d634f64d8740005abf83e51ec1e3e731
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>ICorDebugManagedCallback::LogSwitch, méthode
Notifie le débogueur qu’un thread du common language runtime (CLR) géré a appelé une méthode la <xref:System.Diagnostics.Switch> classe pour créer, modifier ou supprimer un commutateur de débogage/suivi.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `PAppDomain`  
 [in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread managé qui a créé, modifié ou supprimé un commutateur de débogage/suivi.  
  
 `pThread`  
 [in] Pointeur vers un objet ICorDebugThread qui représente le thread managé.  
  
 `lLevel`  
 [in] Une valeur qui indique le niveau de gravité du message descriptif qui a été écrite dans le journal des événements.  
  
 `ulReason`  
 [in] Une valeur de la [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) énumération qui indique l’opération effectuée sur le commutateur de débogage/suivi.  
  
 `pLogSwitchName`  
 [in] Pointeur vers le nom du commutateur de débogage/suivi.  
  
 `pParentName`  
 [in] Pointeur vers le nom du parent du commutateur de débogage/suivi.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugManagedCallback, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
