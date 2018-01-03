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
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError, méthode
Notifie le débogueur qu’une erreur s’est produite lors de la tentative gérer un événement dans le common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pProcess`  
 [in] Pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel l’événement s’est produite.  
  
 `errorHR`  
 [in] La valeur HRESULT qui a été retournée par le Gestionnaire d’événements.  
  
 `errorCode`  
 [in] Entier qui spécifie l’erreur CLR.  
  
## <a name="remarks"></a>Notes  
 Le processus peut être placé en mode de transfert direct, selon la nature de l’erreur.  
  
 Le `DebugError` rappel indique que les services de débogage ont été désactivés en raison d’une erreur, par conséquent, les débogueurs doivent le message d’erreur disponible à l’utilisateur. [ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) sera sécurisé à l’appel, mais toutes les autres méthodes, y compris [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), ne doit pas être appelée. Le débogueur doit utiliser des fonctionnalités du système d’exploitation pour terminer les processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugManagedCallback, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
