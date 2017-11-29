---
title: ICorProfilerCallback, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback
helpviewer_keywords: ICorProfilerCallback interface [.NET Framework profiling]
ms.assetid: 4bae06f7-94d7-4ba8-b250-648b2da78674
topic_type: apiref
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3370dade937d67aa40be263faf3a433d142d932c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback, interface
Fournit des méthodes qui sont utilisées par le common language runtime (CLR) pour avertir un profileur de code lorsque les événements auxquels le profileur est abonné se produisent.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[AppDomainCreationFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Notifie le profileur qu’un domaine d’application a été créé.|  
|[AppDomainCreationStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Notifie le profileur qu’un domaine d’application est créé.|  
|[AppDomainShutdownFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Informe le profileur qu’un domaine d’application a été déchargé à partir d’un processus.|  
|[AppDomainShutdownStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Notifie le profileur qu’un domaine d’application est en cours de déchargement d’un processus.|  
|[AssemblyLoadFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Notifie le profileur qu’un assembly a été chargé.|  
|[AssemblyLoadStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Notifie le profileur qu’un assembly est chargé.|  
|[AssemblyUnloadFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Informe le profileur qu’un assembly a été déchargé.|  
|[AssemblyUnloadStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Notifie le profileur qu’un assembly est déchargé.|  
|[ClassLoadFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Notifie le profileur qu’une classe a été chargé.|  
|[ClassLoadStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Notifie le profileur qu’une classe est chargée.|  
|[ClassUnloadFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Notifie le profileur qu’une classe a été déchargée.|  
|[ClassUnloadStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Notifie le profileur qu’une classe est en cours de déchargement.|  
|[COMClassicVTableCreated (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Notifie le profileur qu’un runtime callable wrapper RCW () pour l’IID et la classe spécifiée a été créé.|  
|[COMClassicVTableDestroyed (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Notifie le profileur qu’un wrapper RCW est détruit.|  
|[ExceptionCatcherEnter (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Notifie le profileur que le contrôle est passé à approprié `catch` bloc.|  
|[ExceptionCatcherLeave (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Notifie le profileur que le contrôle est passé hors approprié `catch` bloc.|  
|[ExceptionCLRCatcherExecute (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|Obsolète dans le .NET Framework version 2.0.|  
|[ExceptionCLRCatcherFound (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|Obsolète dans .NET Framework 2.0.|  
|[ExceptionOSHandlerEnter (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Non implémenté. Un profileur qui a besoin d’informations sur les exceptions non managées doit obtenir ces informations par d’autres moyens.|  
|[ExceptionOSHandlerLeave (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Non implémenté. Un profileur qui a besoin d’informations sur les exceptions non managées doit obtenir ces informations par d’autres moyens.|  
|[ExceptionSearchCatcherFound (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Notifie le profileur que la phase de recherche de la gestion des exceptions a trouvé un gestionnaire pour l’exception qui a été levée.|  
|[ExceptionSearchFilterEnter (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Notifie le profileur qu’un filtre de l’utilisateur est en cours d’exécution.|  
|[ExceptionSearchFilterLeave (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Notifie le profileur qu’un filtre utilisateur vient de se terminer l’exécution.|  
|[ExceptionSearchFunctionEnter (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Notifie le profileur que la phase de recherche de la gestion des exceptions est entrée dans une fonction.|  
|[ExceptionSearchFunctionLeave (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Notifie le profileur que la phase de recherche de la gestion des exceptions a terminé la recherche d’une fonction.|  
|[ExceptionThrown (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Notifie le profileur qu’une exception a été levée.|  
|[ExceptionUnwindFinallyEnter (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Notifie le profileur que la phase de déroulement d’exception gestion entre un `finally` clause contenue dans la fonction spécifiée.|  
|[ExceptionUnwindFinallyLeave (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Informe le profileur que la phase de déroulement d’exception gestion a quitté une `finally` clause.|  
|[ExceptionUnwindFunctionEnter (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Notifie le profileur que la phase de déroulement de la gestion des exceptions est entrée dans une fonction.|  
|[ExceptionUnwindFunctionLeave (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Notifie le profileur que la phase de déroulement de la gestion des exceptions a terminé le déroulement d’une fonction.|  
|[FunctionUnloadStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Notifie le profileur que le runtime a commencé à décharger une fonction.|  
|[Initialize (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Appelée pour initialiser le profileur chaque fois qu’une nouvelle application CLR est démarrée.|  
|[JITCachedFunctionSearchFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Notifie le profileur qu’une recherche est terminée pour une fonction qui a été compilée précédemment à l’aide de NGen.exe.|  
|[JITCachedFunctionSearchStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Notifie le profileur qu’une recherche a démarré pour une fonction qui a été compilée précédemment à l’aide de NGen.exe.|  
|[JITCompilationFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Notifie le profileur que le compilateur JIT a terminé la compilation d’une fonction.|  
|[JITCompilationStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Notifie le profileur que le compilateur (JIT) juste-à-temps a démarré à compiler une fonction.|  
|[JITFunctionPitched, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Notifie le profileur qu’une fonction qui a été compilé par JIT a été supprimée de la mémoire.|  
|[JITInlining (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Notifie le profileur que le compilateur JIT est sur le point d’insertion d’une fonction conformément à une autre fonction.|  
|[ManagedToUnmanagedTransition (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Notifie le profileur qu’une transition du code managé au code non managé s’est produite.|  
|[ModuleAttachedToAssembly (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Notifie le profileur qu’un module est en cours d’attachement à son assembly parent.|  
|[ModuleLoadFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Notifie le profileur qu’un module a été chargé.|  
|[ModuleLoadStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Notifie le profileur qu’un module est chargé.|  
|[ModuleUnloadFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Notifie le profileur qu’un module a été déchargé.|  
|[ModuleUnloadStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Notifie le profileur qu’un module est déchargé.|  
|[MovedReferences, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Notifie le profileur sur les références d’objet qui ont été déplacées pendant le garbage collection.|  
|[ObjectAllocated (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Notifie le profileur de mémoire dans le tas a été allouée pour un objet.|  
|[ObjectReferences (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Notifie le profileur sur les objets dans la mémoire référencée par l’objet spécifié.|  
|[ObjectsAllocatedByClass (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Informe le profileur sur le nombre d’instances de chaque classe spécifiée qui ont été créés depuis le dernier garbage collection.|  
|[RemotingClientInvocationFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Notifie le profileur qu’un appel de la communication à distance s’est exécutée entièrement sur le client.|  
|[RemotingClientInvocationStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Notifie le profileur qu’un appel de la communication à distance a démarré.|  
|[RemotingClientReceivingReply (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Notifie le profileur que la partie côté serveur d’un appel de la communication à distance est terminée et le client reçoit maintenant et s’apprête à traiter la réponse.|  
|[RemotingClientSendingMessage (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Notifie le profileur que le client envoie une demande au serveur.|  
|[RemotingServerInvocationReturned (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Notifie le profileur que le processus a fini d’appeler une méthode en réponse à une demande d’appel de méthode distant.|  
|[RemotingServerInvocationStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Notifie le profileur que le processus appelle une méthode en réponse à une demande d’appel de méthode distant.|  
|[RemotingServerReceivingMessage (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Notifie le profileur que le processus reçoit une demande d’appel ou de l’activation de méthode distante.|  
|[RemotingServerSendingReply (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Notifie le profileur que le processus a fini de traiter une demande d’appel de méthode distant et qu’il est sur le point de transmettre la réponse via un canal.|  
|[RootReferences (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Notifie le profileur avec les informations concernant les références racine après le garbage collection.|  
|[RuntimeResumeFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Notifie le profileur que le runtime a repris tous les threads d’exécution et a retourné un fonctionnement normal.|  
|[RuntimeResumeStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Notifie le profileur que le runtime reprend tous les threads d’exécution.|  
|[RuntimeSuspendAborted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Notifie le profileur que le runtime a abandonné la suspension de l’exécution qui était en cours.|  
|[RuntimeSuspendFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Notifie le profileur que le runtime a terminé la suspension de tous les threads d’exécution.|  
|[RuntimeSuspendStarted (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Notifie le profileur que l’exécution est sur le point d’interrompre tous les threads d’exécution.|  
|[RuntimeThreadResumed (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Notifie le profileur que le thread spécifié a repris après avoir été interrompue.|  
|[RuntimeThreadSuspended, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Notifie le profileur que le thread spécifié a été, ou va être suspendu.|  
|[Shutdown (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Notifie le profileur que l’application est en cours d’arrêt.|  
|[ThreadAssignedToOSThread (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Notifie le profileur qu’un thread managé est implémenté à l’aide d’un thread de système d’exploitation (OS).|  
|[ThreadCreated (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Notifie le profileur qu’un thread a été créé.|  
|[ThreadDestroyed (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Notifie le profileur qu’un thread a été détruit.|  
|[UnmanagedToManagedTransition (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Notifie le profileur qu’une transition du code non managé au code managé s’est produite.|  
  
## <a name="remarks"></a>Remarques  
 Le CLR appelle une méthode dans le `ICorProfilerCallback` (ou [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) interface pour informer le profileur lorsqu’un événement auquel le profileur est abonnée, se produit. Il s’agit de l’interface de rappel principale par le biais duquel le CLR communique avec le profileur de code.  
  
 Un profileur de code doit implémenter les méthodes de la `ICorProfilerCallback` interface. Pour le .NET Framework version 2.0 ou ultérieure, le profileur doit également implémenter le `ICorProfilerCallback2` méthodes. Chaque implémentation de méthode doit retourner un HRESULT qui a la valeur S_OK en cas de réussite ou E_FAIL en cas d’échec. Actuellement, le CLR ignore le HRESULT retourné par chaque rappel à l’exception [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Dans le Registre de Microsoft Windows, un profileur de code doit enregistrer son modèle COM (Component Object) qui implémente le `ICorProfilerCallback` et `ICorProfilerCallback2` interfaces. Un profileur de code s’abonne aux événements pour lesquels il souhaite recevoir une notification en appelant [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Pour ce faire dans l’implémentation du profileur de [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Le profileur peut ensuite recevoir une notification du runtime lorsqu’un événement est sur le point de se produire ou s’est produite dans un processus de runtime en cours d’exécution.  
  
> [!NOTE]
>  Le profileur s’inscrit à un objet COM unique. Si le profileur cible le .NET Framework version 1.0 ou 1.1, que l’objet COM doit implémenter uniquement les méthodes de `ICorProfilerCallback`. S’il cible .NET Framework version 2.0 ou ultérieure, l’objet COM doit également implémenter les méthodes de `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerCallback2, Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [ICorProfilerCallback3 (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerCallback4 (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
