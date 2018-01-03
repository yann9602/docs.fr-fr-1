---
title: "ICorDebugProcess5::EnumerateHeap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHeap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fabe3d70b493427f3845b5752946b00097c1e78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumerateheap-method"></a>ICorDebugProcess5::EnumerateHeap, méthode
Obtient un énumérateur pour les objets sur le tas managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppObject`  
 [out] Un pointeur vers l’adresse d’un [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objet d’interface qui est un énumérateur pour les objets qui résident sur le tas managé.  
  
## <a name="remarks"></a>Notes  
 Avant d’appeler le `ICorDebugProcess5::EnumerateHeap` (méthode), vous devez appeler la [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) (méthode) et examinez la valeur de la `areGCStructuresValid` champ retourné [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) objet pour vous assurer que le tas de garbage collection dans son état actuel est énumérable. En outre, le `ICorDebugProcess5::EnumerateHeap` retourne `E_FAIL` si vous attachez trop tôt dans la durée de vie du processus, avant de mémoire pour le tas managé est alloué.  
  
 Le [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objet d’interface est un énumérateur standard dérivé de l’interface ICorDebugEnum qui vous permet d’énumérer les [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objets. Cette méthode remplit la [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objet de collection [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances qui fournissent des informations sur tous les objets. La collection peut également inclure [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances qui fournissent des informations sur les objets qui ne sont pas enracinés par un de l’objet mais n’ont pas encore été collectés par le garbage collector.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugProcess5, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
