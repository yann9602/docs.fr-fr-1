---
title: ICorDebugProcess5, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5
helpviewer_keywords: ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0f0a46e18121a222ee62fec207dde938d1e967b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5, interface
Étend l’interface ICorDebugProcess pour prendre en charge l’accès au tas managé, pour fournir des informations sur le garbage collection d’objets gérés, et pour déterminer si un débogueur charge des images à partir du cache d’images natives locales application.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnableNGenPolicy (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|Définit une valeur qui détermine comment une application charge les images natives lors de son exécution sous un débogueur managé.|  
|[EnumerateGCReferences (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|Obtient un énumérateur pour tous les objets qui doivent être par le garbage collector dans un processus.|  
|[EnumerateHandles (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|Obtient un énumérateur pour les handles d’objet dans un processus.|  
|[EnumerateHeap (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|Obtient un énumérateur pour les objets sur le tas managé.|  
|[EnumerateHeapRegions (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|Obtient un énumérateur pour les régions du tas managé.|  
|[GetArrayLayout (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|Obtient des informations sur la disposition d’un tableau dans la mémoire.|  
|[GetGCHeapInformation (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|Obtient un pointeur vers un [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) structure qui contient des informations sur les objets qui doivent être par le garbage collector sur le tas managé.|  
|[GetObject (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|Obtient un pointeur vers un objet sur le tas managé.|  
|[GetTypeFields (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|Obtient un pointeur vers un tableau qui contient les informations pour un type en fonction de son identificateur de type.|  
|[GetTypeForTypeID (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|Obtient un objet de type qui fournit des informations sur un objet basé sur les identificateurs de son type.|  
|[GetTypeID (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|Obtient l’identificateur de type pour l’objet à une adresse spécifiée.|  
|[GetTypeLayout (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|Obtient des informations sur la disposition d’un objet dans la mémoire en fonction de son identificateur de type.|  
  
## <a name="remarks"></a>Remarques  
 Cette interface étend logiquement l’ICorDebugProcess, ICorDebugProcess2, et [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l’appel à distance, à partir d’un autre ordinateur ou à partir d’un autre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
