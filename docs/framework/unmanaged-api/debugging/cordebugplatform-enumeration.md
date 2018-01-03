---
title: "CorDebugPlatform, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugPlatformEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugPlatformEnum
helpviewer_keywords: CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f67ed6ad886c137eddaa42840f3f0edda88bd4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugplatform-enumeration"></a>CorDebugPlatform, énumération
Fournit des valeurs de plateforme cible utilisées par le [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|CORDB_PLATFORM_WINDOWS_X86|La plateforme cible est Windows s'exécutant sur du matériel Intel x86.|  
|CORDB_PLATFORM_WINDOWS_AMD64|La plateforme cible est Windows 64 bits s'exécutant sur du matériel AMD64 ou Intel EM64T.|  
|CORDB_PLATFORM_WINDOWS_IA64|La plateforme cible est Windows 32 bits s'exécutant sur du matériel IA-64.|  
|CORDB_PLATFORM_MAC_PPC|La plateforme cible est le système d’exploitation Macintosh s’exécutant sur du matériel PowerPC.|  
|CORDB_PLATFORM_MAC_X86|La plateforme cible est en cours d’exécution sur du matériel Intel x86 avec le système d’exploitation Macintosh.|  
|CORDB_PLATFORM_WINDOWS_ARM|La plateforme cible est le système d’exploitation Macintosh s’exécutant sur le matériel Windows ARM.|  
|CORDB_PLATFORM_MAC_AMD64|La plateforme cible est en cours d’exécution sur du matériel AMD64 avec le système d’exploitation Macintosh.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 Les membres `CORDB_PLATFORM_WINDOWS_ARM` et `CORDB_PLATFORM_MAC_AMD64` sont disponibles dans .NET Framework 4.5.2 et ultérieur.  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
