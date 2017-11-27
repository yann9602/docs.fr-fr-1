---
title: "COR_PRF_SUSPEND_REASON, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SUSPEND_REASON
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SUSPEND_REASON
helpviewer_keywords: COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aef9688d3da047645d53f6fcf113153393780c8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfsuspendreason-enumeration"></a>COR_PRF_SUSPEND_REASON, énumération
Indique la raison pour laquelle le runtime est suspendu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|L’exécution est interrompu pour une raison non spécifiée.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Le runtime est suspendu pour traiter une demande de garbage collection.<br /><br /> Les rappels de collection associés au garbage ont lieu entre les [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) et [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) rappels.|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|L’exécution est suspendu afin qu’un `AppDomain` peut être arrêté.<br /><br /> Quand l’exécution est suspendu, le runtime détermine quels threads se trouvent dans le `AppDomain` qui est en cours d’arrêter et de les définir à abandonner lorsqu’ils reprennent. Il n’y aucun `AppDomain`-rappels spécifiques pendant cette interruption.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|Le runtime est suspendu pour que la suspension de code peut se produire.<br /><br /> Suspension de code s’ensuit uniquement lorsque le compilateur (JIT) juste-à-temps est actif avec la suspension de code activée. Code de rappels de suspension se produisent entre la `ICorProfilerCallback::RuntimeSuspendFinished` et `ICorProfilerCallback::RuntimeResumeStarted` rappels. **Remarque :** le JIT CLR ne suspend pas les fonctions dans le .NET Framework version 2.0, cette valeur n’est pas utilisé dans la version 2.0.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|Le runtime est suspendu pour s’arrêter. Il doit suspendre tous les threads pour terminer l’opération.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|Le runtime est suspendu dans le processus de débogage.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|Le runtime est suspendu pour préparer un garbage collection.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|Le runtime est suspendu pour la recompilation JIT.|  
  
## <a name="remarks"></a>Remarques  
 Tous les threads d’exécution qui se trouvent dans le code non managé sont autorisés à continuer à s’exécuter jusqu'à ce qu’ils essaient d’entrer à nouveau l’exécution, à partir de laquelle ils seront également suspendus jusqu'à ce que le runtime reprend. Cela s’applique également aux nouveaux threads qui entrent dans le runtime. Tous les threads dans le runtime sont immédiatement suspendus s’ils sont dans du code interruptible, ou suspendus lorsqu’ils atteignent du code interruptible.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
