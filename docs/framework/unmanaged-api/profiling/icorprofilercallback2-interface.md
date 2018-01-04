---
title: ICorProfilerCallback2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2
helpviewer_keywords: ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7927d3b4d41731c9b69154fa8895a8f698f53e31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2, interface
Fournit des méthodes qui sont utilisées par le common language runtime (CLR) pour avertir un profileur de code lorsque les événements auxquels le profileur est abonné se produisent. Le `ICorProfilerCallback2` interface est une extension de la [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface. Autrement dit, il fournit des nouveaux rappels introduites dans .NET Framework version 2.0.  
  
> [!NOTE]
>  Chaque implémentation de méthode doit retourner un HRESULT avec la valeur S_OK de réussite ou E_FAIL en cas d’échec. Actuellement, le CLR ignore le HRESULT retourné par chaque rappel à l’exception [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[FinalizeableObjectQueued, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Notifie le profileur de code à un objet avec un finaliseur a été mis en attente pour le thread finaliseur pour l’exécution de son `Finalize` (méthode).|  
|[GarbageCollectionFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Informe le profileur qu’une garbage collection est terminé et que tous les rappels de garbage collection ont été publiés.|  
|[GarbageCollectionStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Notifie le profileur de code qu’un garbage collection a démarré.|  
|[HandleCreated, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Notifie le profileur de code qu’un handle de garbage collection a été créé.|  
|[HandleDestroyed, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Notifie le profileur de code qu’un handle de garbage collection a été détruit.|  
|[RootReferences2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Notifie le profileur concernant les références racine après qu’un garbage collection s’est produite. Cette méthode est une extension de la [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) (méthode).|  
|[SurvivingReferences, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Notifie le profileur à propos des références d’objet qui ont survécu à un garbage collection.|  
|[ThreadNameChanged, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Notifie le profileur de code que le nom d’un thread a changé.|  
  
## <a name="remarks"></a>Notes  
 Le CLR appelle une méthode dans le `ICorProfilerCallback` (ou `ICorProfilerCallback2`) interface pour informer le profileur lorsqu’un événement auquel le profileur était abonné se produit. Il s’agit de l’interface de rappel principale par le biais duquel le CLR communique avec le profileur de code.  
  
 Un profileur de code doit implémenter les méthodes de la `ICorProfilerCallback` interface. Pour le .NET Framework 2.0 et les versions ultérieures, le profileur doit également implémenter le `ICorProfilerCallback2` méthodes. Chaque implémentation de méthode doit retourner un HRESULT avec la valeur S_OK de réussite ou E_FAIL en cas d’échec. Actuellement, le CLR ignore le HRESULT retourné par chaque rappel à l’exception [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Un profileur de code doit inscrire dans le Registre de Microsoft Windows, son objet COM qui implémente le `ICorProfilerCallback` et `ICorProfilerCallback2` interfaces. Un profileur de code s’abonne aux événements pour lesquels il souhaite recevoir une notification en appelant [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Pour ce faire dans l’implémentation du profileur de [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Le profileur peut ensuite recevoir une notification du runtime lorsqu’un événement est sur le point de se produire ou s’est produite dans un processus de runtime en cours d’exécution.  
  
> [!NOTE]
>  Le profileur s’inscrit à un objet COM unique. Si le profileur cible .NET Framework version 1.0 ou 1.1, cet objet COM doit uniquement implémenter les méthodes de `ICorProfilerCallback`. S’il cible .NET Framework version 2.0 et versions ultérieures, l’objet COM doit implémenter également les méthodes de `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback3, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerCallback4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
