---
title: "CorGCReferenceType, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorGCReferenceType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorGCReferenceType
helpviewer_keywords: CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45ca1e9c6123a4b22a1645d151e49a0dd65addbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType, énumération
Identifie la source d'un objet pour lequel l'espace occupé en mémoire peut être récupéré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a>Membres  
  
|Nom de membre|Description|  
|-----------------|-----------------|  
|`CorHandleStrong`|Handle à une référence forte tiré de la table de handles d'objets.|  
|`CorHandleStrongPinning`|Handle vers une référence forte épinglée à partir de la table de handles d’objet.|  
|`CorHandleWeakShort`|Handle vers une référence faible à partir de la table de handles d’objet.|  
|`CorHandleWeakRefCount`|Handle vers un objet contenant des références faible à partir de la table de handles d’objet.|  
|`CorHandleStrongRefCount`|Handle vers un objet contenant des références à partir de la table de handles d’objet.|  
|`CorHandleStrongDependent`|Handle vers un objet dépendant de la table de handles d’objet.|  
|`CorHandleStrongAsyncPinned`|Objet épinglé asynchrone tiré de la table de handles d'objets.|  
|`CorHandleStrongSizedByref`|Handle fort qui conserve une taille approximative de la fermeture collective de tous les objets et racines d’objets au moment du Garbage Collection.|  
|`CorReferenceStack`|Une référence à partir de la pile managée.|  
|`CorReferenceFinalizer`|Une référence à partir de la file d’attente du finaliseur.|  
|CorHandleStrongOnly|Retourner uniquement les références solides à partir de la table de handles. Cette valeur est utilisée par le [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) méthode uniquement.|  
|`CorHandleWeakOnly`|Retourner uniquement les références faibles à partir de la table de handles. Cette valeur est utilisée par le [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) méthode uniquement.|  
|`CorHandleAll`|Retourne toutes les références à partir de la table de handles. Cette valeur est utilisée par le [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) méthode uniquement.|  
  
## <a name="remarks"></a>Remarques  
 Le `CorGCReferenceType` énumération est utilisée comme suit :  
  
-   En tant que la valeur de la `type` champ le [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, il indique la source d’une référence ou un handle.  
  
-   Comme le `types` l’argument de la [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) méthode, il spécifie les types de handles à inclure dans l’énumération.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
