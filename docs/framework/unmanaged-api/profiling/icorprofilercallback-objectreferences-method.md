---
title: "ICorProfilerCallback::ObjectReferences, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5cdebc1984f86d3801759f8f987df8fb89d82e3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences, méthode
Notifie le profileur sur les objets en mémoire qui sont référencés par l’objet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `objectId`  
 [in] L’ID de l’objet qui fait référence à des objets.  
  
 `classId`  
 [in] L’ID de l’objet spécifié est une instance de la classe.  
  
 `cObjectRefs`  
 [in] Le nombre d’objets référencés par l’objet spécifié (autrement dit, le nombre d’éléments dans le `objectRefIds` tableau).  
  
 `objectRefIds`  
 [in] Un tableau d’ID d’objets qui sont référencés par `objectId`.  
  
## <a name="remarks"></a>Remarques  
 Le `ObjectReferences` méthode est appelée pour chaque objet reste dans le tas après l’exécution d’un garbage collection. Si le profileur retourne une erreur à partir de ce rappel, les services de profilage cessent d’appeler ce rappel jusqu’au garbage collection suivant.  
  
 Le `ObjectReferences` rappel peut être utilisé conjointement avec la [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) rappel pour créer un graphique de référence d’objet complet pour le runtime. Le common language runtime (CLR) garantit que chaque référence d’objet est signalé qu’une seule fois par le `ObjectReferences` (méthode).  
  
 Les ID d’objet retourné par `ObjectReferences` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être occupé à déplacer des objets. Par conséquent, les profileurs ne doivent pas essayer d’inspecter les objets pendant un `ObjectReferences` appeler. Lorsque [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) est appelée, le garbage collection est terminé et l’inspection peut être effectuée en toute sécurité.  
  
 Une valeur null `ClassId` indique que `objectId` a un type qui est déchargement.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
