---
title: "CorDebugCodeInvokeKind, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugCodeInvokeKind
api_location: mscordbi.dll
api_type: COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10b45938cfe63fa98fdb06bc20c66cc0f25c41a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugcodeinvokekind-enumeration"></a>CorDebugCodeInvokeKind, énumération
Indique de quelle manière une fonction exportée appelle du code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|Si du code managé est appelé par cette méthode, il devra ensuite être localisé par des événements ou des points d'arrêt explicites.<br /><br /> – ou –<br /><br /> Une partie du code managé appelé par cette méthode risque d'être oubliée, car il n'existe pas de moyen simple d'arrêter son exécution.<br /><br /> – ou –<br /><br /> La méthode risque de ne jamais appeler le code managé.|  
|`CODE_INVOKE_KIND_RETURN`|Cette méthode appelle le code managé via une instruction de retour. Le pas à pas sortant doit normalement se produire dans le code managé suivant.|  
|`CODE_INVOKE_KIND_TAILCALL`|Cette méthode appelle le code managé via un appel tail. Le pas à pas détaillé et le pas à pas principal sur des instructions d'appel doivent normalement se produire dans le code managé.|  
  
## <a name="remarks"></a>Notes  
 Cette énumération est utilisée par le [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) méthode pour fournir des informations sur l’exécution pas à pas du code managé.  
  
> [!NOTE]
>  Cette énumération est destinée à une utilisation dans des scénarios de débogage .NET Native uniquement.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
