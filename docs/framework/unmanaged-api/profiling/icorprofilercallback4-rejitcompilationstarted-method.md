---
title: "ICorProfilerCallback4::ReJITCompilationStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ddcacf72d21ec076fe74a1c069311ef3f73a20c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted, méthode
Notifie le profileur que le compilateur (JIT) juste-à-temps a démarré recompiler une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReJITCompilationStarted(    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `functionId`  
 [in] L’ID de la fonction que le compilateur JIT a commencé à recompiler.  
  
 `rejitId`  
 [in] L’ID de la recompilation de la nouvelle version de la fonction.  
  
 `fIsSafeToBlock`  
 [in] `true` pour indiquer que le blocage peut entraîner l’exécution pour attendre que le thread appelant à retourner à partir de ce rappel ; `false` pour indiquer que le blocage n’affecte pas le fonctionnement de l’exécution. La valeur `true` ne nuise pas au runtime, mais peut affecter les résultats de profilage.  
  
## <a name="remarks"></a>Remarques  
 Il est possible de recevoir plusieurs paires de `ReJITCompilationStarted` et [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) appels de méthode pour chaque fonction en raison du mode le runtime gère les constructeurs de classe. Par exemple, le runtime commence à recompiler la méthode A, mais le constructeur de classe pour la classe B doit être exécutée. Par conséquent, le runtime recompile le constructeur de classe B et l’exécute. Alors que le constructeur s’exécute, il effectue un appel à la méthode A, ce qui provoque la méthode A de nouveau être recompilée. Dans ce scénario, la première recompilation de la méthode A est interrompue. Toutefois, les deux tente de recompiler la méthode A sont signalé avec des événements de recompilation JIT.  
  
 Les profileurs doivent prendre en charge la séquence des rappels de recompilation JIT dans les cas où deux threads effectuent simultanément des rappels. Par exemple, le thread A appelle `ReJITCompilationStarted`; Toutefois, avant que le thread A appelle [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), le thread B appelle [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) avec l’ID de fonction à partir de la `ReJITCompilationStarted` rappel pour le thread A. Il peut apparaître que l’ID de fonction n'est pas encore valide, car un appel à [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) n’a pas encore été reçu par le profileur. Toutefois, dans ce cas, l’ID de fonction est valide.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4 (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [JITCompilationFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [ReJITCompilationFinished (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
