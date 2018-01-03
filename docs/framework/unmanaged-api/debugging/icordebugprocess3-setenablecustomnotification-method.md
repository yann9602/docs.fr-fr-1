---
title: "ICorDebugProcess3::SetEnableCustomNotification, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess3.SetEnableCustomNotification Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ccd1f4b6be56202d5efea1d2e38dce554835218
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification, méthode
Active ou désactive les notifications de débogueur personnalisées du type spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pClass`  
 [in] Type qui spécifie les notifications de débogueur personnalisées.  
  
 `fEnable`  
 [in] `true` pour activer les notifications de débogueur personnalisées ; `false` pour désactiver les notifications. La valeur par défaut est `false`.  
  
## <a name="remarks"></a>Notes  
 Lorsque `fEnable` a la valeur `true`, les appels à la <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> déclencheur de la méthode un [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) rappel. Les notifications sont désactivées par défaut. Par conséquent, le débogueur doit spécifier tous les types de notification qu’il connaît et souhaite gérer. Étant donné que la [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) classe est délimitée par le domaine d’application, le débogueur doit appeler `SetEnableCustomNotification` pour chaque domaine d’application dans le processus s’il souhaite recevoir la notification de l’ensemble du processus.  
  
 En commençant par le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], la seule notification prise en charge est une notification de dépendance inter-threads.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugProcess3, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
