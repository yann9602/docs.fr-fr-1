---
title: "LoggingLevelEnum, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoggingLevelEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: LoggingLevelEnum
helpviewer_keywords: LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f6041f429c057cea9607df34ec5691be84e2d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum, énumération
Indique le niveau de gravité d'un message de description qui est écrit dans le journal des événements quand un thread managé consigne un événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`LTraceLevel0`|Le message est un niveau de trace 0.|  
|`LTraceLevel1`|Le message est un niveau de trace 1.|  
|`LTraceLevel2`|Le message est un niveau de trace 2.|  
|`LTraceLevel3`|Le message est un niveau de trace 3.|  
|`LTraceLevel4`|Le message est un niveau de trace 4.|  
|`LStatusLevel0`|Le message est un niveau d’état 0.|  
|`LStatusLevel1`|Le message est un niveau de statut 1.|  
|`LStatusLevel2`|Le message est un niveau de statut 2.|  
|`LStatusLevel3`|Le message est un niveau de statut 3.|  
|`LStatusLevel4`|Le message est un niveau de statut 4.|  
|`LWarningLevel`|Le message est un niveau d’avertissement.|  
|`LErrorLevel`|Le message est un niveau d’erreur.|  
|`LPanicLevel`|Le message est un niveau de panique.|  
  
## <a name="remarks"></a>Remarques  
 Le common language runtime (CLR) appelle la [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) méthode pour informer le débogueur qu’un thread managé a enregistré un événement. Le CLR passe une valeur de la `LoggingLevelEnum` énumération pour indiquer le niveau de gravité du message que le thread managé a écrit dans le journal des événements.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.EventLog>  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
