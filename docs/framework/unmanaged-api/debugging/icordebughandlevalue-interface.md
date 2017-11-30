---
title: ICorDebugHandleValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHandleValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHandleValue
helpviewer_keywords: ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b56c23caaaed2bc63c724769db1198fd088f7f1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebughandlevalue-interface1"></a>ICorDebugHandleValue Interface1
Une sous-classe de ICorDebugReferenceValue qui représente une valeur de référence dans laquelle le débogueur a créé un handle pour le garbage collection.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Dispose (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Libère le handle référencé par ce `ICorDebugHandleValue` objet sans libérer explicitement le pointeur d’interface.|  
|[GetHandleType (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Obtient une valeur CorDebugHandleType qui décrit le type de handle référencé par cet `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Remarques  
 Un `ICorDebugReferenceValue` objet est invalidé par un arrêt dans l’exécution du code débogué. Un `ICorDebugHandleValue` conserve sa référence via des arrêts et reprises, jusqu'à ce qu’elle est libérée explicitement.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
