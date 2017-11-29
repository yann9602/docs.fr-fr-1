---
title: "ICorProfilerCallback::JITCachedFunctionSearchStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09fcdc67dc730b59b76a2da9f6ccea04800e20c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted, méthode
Notifie le profileur qu’une recherche a démarré pour une fonction qui a été compilée précédemment à l’aide du Générateur d’images natives (NGen.exe).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `functionId`  
 [in] L’ID de la fonction pour laquelle la recherche est effectuée.  
  
 `pbUseCachedFunction`  
 [out] `true` si le moteur d’exécution doit utiliser la version mise en cache d’une fonction (si disponible) ; sinon `false`. Si la valeur est `false`, le moteur d’exécution JIT-compile la fonction au lieu d’utiliser une version qui n’est pas compilé par JIT.  
  
## <a name="remarks"></a>Remarques  
 Dans le .NET Framework version 2.0, le `JITCachedFunctionSearchStarted` et [ICorProfilerCallback::JITCachedFunctionSearchFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) rappels ne sont pas effectués pour toutes les fonctions dans les images NGen normales. Seules les images NGen optimisées pour un profil généreront des rappels pour toutes les fonctions dans l’image. Toutefois, en raison de la charge supplémentaire, un profileur doit demander les images NGen optimisées sur le profileur uniquement si elle a l’intention d’utiliser ces rappels pour forcer une fonction compilée juste-à-temps (JIT). Sinon, le profileur doit utiliser une stratégie minimale pour la collecte des informations sur la fonction.  
  
 Les profileurs doivent prendre en charge les cas où plusieurs threads d’une application profilée appellent simultanément la même méthode. Par exemple, le thread A appelle `JITCachedFunctionSearchStarted` et le profileur répond en affectant *pbUseCachedFunction*sur FALSE pour forcer la compilation JIT. Thread, puis appelle [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) et [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).  
  
 Maintenant, le thread B appelle `JITCachedFunctionSearchStarted` pour la même fonction. Bien que le profileur a déclaré son intention de la fonction de la compilation JIT, le profileur reçoit le deuxième rappel, car le thread B envoie le rappel avant que le profileur n’a répondu à l’appel du thread de A à `JITCachedFunctionSearchStarted`. L’ordre dans lequel les threads effectuent des appels dépend de la façon dont les threads sont planifiés.  
  
 Lorsque le profileur reçoit des rappels en double, il doit définir la valeur référencée par `pbUseCachedFunction` à la même valeur pour tous les rappels en double. Autrement dit, lorsque `JITCachedFunctionSearchStarted` est appelée plusieurs fois avec le même `functionId` valeur, le profileur doit répondre de la même chaque fois.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
