---
title: "ICorProfilerCallback4::ReJITError, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITError
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c746d0f7a6be96f95f1a051e22de0ad1bd2d2269
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError, méthode
Notifie le profileur que le compilateur (JIT) juste-à-temps a rencontré une erreur dans le processus de recompilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `moduleID`  
 [in] Le `ModuleID` dans lequel la recompilation ayant échoué a été tenté.  
  
 `methodId`  
 [in] Le `MethodDef` de la méthode sur lequel la tentative de recompilation ayant échoué a été effectuée.  
  
 `functionId`  
 [in] L’instance de la fonction qui est recompilée ou marquée pour la recompilation. Cette valeur peut être `NULL` si la défaillance s’est produite sur une base par méthode, au lieu d’une base par instanciation (par exemple, si le profileur a spécifié un jeton de métadonnées non valide pour la méthode d’être recompilé).  
  
 `hrStatus`  
 [in] HRESULT qui indique la nature de l’échec. Consultez la section HRESULT d’état pour obtenir la liste de valeurs.  
  
## <a name="return-value"></a>Valeur de retour  
 Les valeurs retournées depuis ce rappel sont ignorées.  
  
## <a name="status-hresults"></a>HRESULT d'état  
  
|HRESULT du tableau d'états|Description|  
|--------------------------|-----------------|  
|E_INVALIDARG|Le `moduleID` ou `methodDef` jeton est `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Le module n'est pas encore totalement chargé ou il est en cours de déchargement.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Le module spécifié a été généré dynamiquement (par exemple, en `Reflection.Emit`) et n’est donc pas prise en charge par cette méthode.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|La méthode est instanciée dans un assembly pouvant être collecté et n’est donc pas en mesure d’être recompilé. Notez que les types et fonctions définies dans un contexte de réflexion non (par exemple, `List<MyCollectibleStruct>`) peut être instancié dans un assembly pouvant être collecté.|  
|E_OUTOFMEMORY|Le CLR a manqué de mémoire lors de la tentative de marquer la méthode spécifiée pour la recompilation JIT.|  
|Autre|Le système d'exploitation a retourné un échec en dehors du contrôle du CLR. Par exemple, si un appel système pour modifier la protection d’accès d’une page de mémoire échoue, l’erreur de système d’exploitation s’affiche.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
