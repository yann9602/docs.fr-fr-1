---
title: "ICorDebugProcess5::EnumerateHandles, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHandles
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9bf9f1a4d565e0af4f3ee34a2805116407027d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles, méthode
Obtient un énumérateur pour les handles d’objet dans un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `types`  
 [in] Une combinaison d’opérations de [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valeurs qui spécifie le type de handles à inclure dans la collection.  
  
 `ppENum`  
 [out] Un pointeur vers l’adresse d’un [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) qui est un énumérateur pour les objets pour le garbage collector.  
  
## <a name="remarks"></a>Notes  
 `EnumerateHandles`est une fonction d’assistance qui prend en charge l’inspection de la table de handles. Il est similaire à la [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) (méthode), à ceci près qu’au lieu de remplir une [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection avec tous les objets par le garbage collector, il inclut uniquement les objets qui ont des descripteurs de la table de handles.  
  
 Le `types` paramètre spécifie les types de handle à inclure dans la collection. `types`peut être une des trois membres suivants de la [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) énumération :  
  
-   `CorHandleStrongOnly`(descripteurs pour les références fortes uniquement).  
  
-   `CorHandleWeakOnly`(gère uniquement les références faibles).  
  
-   `CorHandleAll`(tous les handles).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
