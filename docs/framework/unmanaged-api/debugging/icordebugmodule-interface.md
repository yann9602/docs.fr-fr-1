---
title: ICorDebugModule Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule
helpviewer_keywords: ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ced01c9c01a32468f371a8e172c878337fb79757
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmodule-interface1"></a>ICorDebugModule Interface1
Représente un module common language runtime (CLR), qui est un fichier exécutable ou une bibliothèque de liens dynamiques (DLL).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateBreakpoint, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|Non implémenté.|  
|[EnableClassLoadCallbacks (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|Détermine si le [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) sont appelés pour ce module.|  
|[EnableJITDebugging (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|Détermine si le compilateur (JIT) juste-à-temps conserve les informations de débogage pour les méthodes de ce module.|  
|[GetAssembly (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|Obtient l’assembly contenant de ce module.|  
|[GetBaseAddress, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|Obtient l’adresse de base du module.|  
|[GetClassFromToken (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|Obtient la ICorDebugClass à partir des métadonnées.|  
|[GetEditAndContinueSnapshot (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|Obsolète.|  
|[GetFunctionFromRVA (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|Non implémenté.|  
|[GetFunctionFromToken, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|Obtient la fonction qui est spécifiée par le jeton de métadonnées.|  
|[GetGlobalVariableValue (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|Obtient un objet de valeur pour la variable globale spécifiée.|  
|[GetMetaDataInterface (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|Obtient un pointeur d’interface de métadonnées qui peut être utilisé pour examiner les métadonnées pour le module.|  
|[GetName (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|Obtient le nom de fichier du module.|  
|[GetProcess (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|Obtient le processus contenant de ce module.|  
|[GetSize (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|Obtient la taille du module en octets.|  
|[GetToken, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|Obtient le jeton de l’entrée de table pour ce module.|  
|[IsDynamic (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|Indique si le module est dynamique.|  
|[IsInMemory (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|Indique si ce module existe uniquement en mémoire.|  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebug (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
