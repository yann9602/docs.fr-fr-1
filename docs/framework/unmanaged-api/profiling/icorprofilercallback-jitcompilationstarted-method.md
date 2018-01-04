---
title: "ICorProfilerCallback::JITCompilationStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a25f452ccb121ef7ebcae05048eb7116b4ac48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted, méthode
Notifie le profileur que le compilateur (JIT) juste-à-temps a démarré à compiler une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `functionId`  
 [in] L’ID de la fonction pour laquelle la compilation démarre.  
  
 `fIsSafeToBlock`  
 [in] Une valeur qui indique au profileur si un blocage affectera le fonctionnement de l’exécution. La valeur est `true` si blocage peut provoquer l’exécution pour attendre que le thread appelant à retourner à partir de ce rappel ; sinon, `false`.  
  
 Bien que la valeur de `true` ne nuise pas au runtime, elle peut fausser les résultats de profilage.  
  
## <a name="remarks"></a>Notes  
 Il est possible de recevoir plusieurs paires de `JITCompilationStarted` et [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) appelle pour chaque fonction en raison du mode le runtime gère les constructeurs de classe. Par exemple, le runtime commence la compilation JIT de la méthode A, mais le constructeur de classe pour la classe B doit être exécutée. Par conséquent, le runtime JIT-compile le constructeur de classe B et l’exécute. Lorsque le constructeur s’exécute, il effectue un appel à la méthode A, ce qui provoque la méthode A compilé juste-à nouveau. Dans ce scénario, la première compilation JIT de la méthode A est interrompue. Toutefois, les deux tentatives de compilation JIT de la méthode A sont signalés par les événements de compilation JIT. Si le profileur doit remplacer le code de Microsoft intermediate language (MSIL) pour la méthode A en appelant le [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) (méthode), il doit le faire pour les deux `JITCompilationStarted` événements, mais il peut utiliser le même bloc MSIL pour les deux.  
  
 Les profileurs doivent prendre en charge de la séquence de rappels JIT dans les cas où deux threads effectuent simultanément des rappels. Par exemple, le thread A appelle `JITCompilationStarted`. Toutefois, avant le thread A appelle `JITCompilationFinished`, le thread B appelle [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) avec l’ID de la fonction à partir du thread de `JITCompilationStarted` rappel. Il peut apparaître que l’ID de fonction n'est pas encore valide, car un appel à `JITCompilationFinished` n’a pas encore été reçu par le profileur. Toutefois, dans un cas comme celui-ci, l’ID de fonction est valide.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [JITCompilationFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
