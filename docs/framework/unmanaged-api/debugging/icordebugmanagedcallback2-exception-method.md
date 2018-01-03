---
title: "ICorDebugManagedCallback2::Exception, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79a8fa4709aeb04164bd1c2da07607435b76fff5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception, méthode
Notifie le débogueur qu’une recherche pour un gestionnaire d’exceptions a démarré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pAppDomain`  
 [in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread sur lequel l’exception a été levée.  
  
 `pThread`  
 [in] Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel l’exception a été levée.  
  
 `pFrame`  
 [in] Un pointeur vers un objet ICorDebugFrame qui représente un frame, comme déterminé par la `dwEventType` paramètre. Pour plus d’informations, consultez le tableau dans la section Notes.  
  
 `nOffset`  
 [in] Entier qui spécifie un offset, comme déterminé par la `dwEventType` paramètre. Pour plus d’informations, consultez le tableau dans la section Notes.  
  
 `dwEventType`  
 [in] Valeur de l’énumération CorDebugExceptionCallbackType qui spécifie le type de ce rappel d’exception.  
  
 `dwFlags`  
 [in] Une valeur de la [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) énumération qui spécifie des informations supplémentaires sur l’exception  
  
## <a name="remarks"></a>Notes  
 Le `Exception` rappel est appelé à différents points pendant la phase de recherche du processus de gestion des exceptions. Autrement dit, elle peut être appelée plusieurs fois pendant le déroulement d’une exception.  
  
 L’exception en cours de traitement peut être récupérée à partir de l’objet ICorDebugThread référencé par le `pThread` paramètre.  
  
 L’image particulière et le décalage sont déterminées par la `dwEventType` paramètre comme suit :  
  
|Valeur de `dwEventType`|Valeur de `pFrame`|Valeur de `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Le frame qui a levé l’exception.|Le pointeur d’instruction dans le frame.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Le frame de code utilisateur plus proche du point de l’exception levée.|Le pointeur d’instruction dans le frame.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Le frame qui contient le gestionnaire catch.|L’offset Microsoft intermediate language (MSIL), du début du gestionnaire catch.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Non défini.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugManagedCallback2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
