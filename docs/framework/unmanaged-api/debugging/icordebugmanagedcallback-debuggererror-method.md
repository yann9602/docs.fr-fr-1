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
ms.openlocfilehash: c4eb16762d2a0db01c3cc921712a89995e0c87c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
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
  
## <a name="remarks"></a>Remarques  
 Le processus peut être placé en mode de transfert direct, selon la nature de l’erreur.  
  
 Le `DebugError` rappel indique que les services de débogage ont été désactivés en raison d’une erreur, par conséquent, les débogueurs doivent le message d’erreur disponible à l’utilisateur. [ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) sera sécurisé à l’appel, mais toutes les autres méthodes, y compris [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), ne doit pas être appelée. Le débogueur doit utiliser des fonctionnalités du système d’exploitation pour terminer les processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugManagedCallback (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
