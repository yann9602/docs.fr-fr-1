---
title: "ICorDebugProcess5::EnumerateHeapRegions, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHeapRegions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1365ed5fd8cf308716b16d78e79a26584bd966c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions, méthode
Obtient un énumérateur pour les plages de mémoire du tas managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppRegions`  
 [out] Un pointeur vers l’adresse d’un [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objet d’interface qui est un énumérateur pour les plages de mémoire dans lequel les objets résident dans le tas managé.  
  
## <a name="remarks"></a>Remarques  
 Avant d’appeler le `ICorDebugProcess5::EnumerateHeapRegions` (méthode), vous devez appeler la [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) (méthode) et examinez la valeur de la `areGCStructuresValid` champ retourné [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) objet pour vous assurer que le tas de garbage collection dans son état actuel est énumérable. En outre, le `ICorDebugProcess5::EnumerateHeapRegions` retourne de la méthode `E_FAIL` si vous attachez trop tôt dans la durée de vie du processus, les régions sont créées avant la mémoire.  
  
 Cette méthode est garantie pour énumérer toutes les régions de mémoire qui peuvent contenir des objets gérés, mais il ne garantit pas que les objets gérés qui résident dans ces régions. Le [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objet de collection peut-être inclure des régions de mémoire vide ou réservés.  
  
 Le [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objet d’interface est un énumérateur standard dérivé de l’interface ICorDebugEnum qui vous permet d’énumérer les [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objets. Chaque [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objet fournit des informations sur la plage de mémoire d’un segment particulier, ainsi que la génération des objets dans ce segment.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Icordebugprocess5, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
