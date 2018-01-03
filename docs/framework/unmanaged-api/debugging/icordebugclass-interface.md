---
title: ICorDebugClass Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass
helpviewer_keywords: ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3998cf76430612759f69df07fb4f5afebd7a25ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclass-interface1"></a>ICorDebugClass Interface1
Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur). Si le type est générique, `ICorDebugClass` représente le type générique non instancié.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetModule, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Obtient le module qui définit cette classe.|  
|[GetStaticFieldValue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|Obtient la valeur du champ statique spécifié.|  
|[GetToken, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|Obtient le `TypeDef` jeton de métadonnées pour cette classe.|  
  
## <a name="remarks"></a>Notes  
 Le `ICorDebugClass` interface représente un type générique non instancié. L’interface ICorDebugType représente un type générique instancié. Par exemple, `Hashtable<K, V>` serait représenté par `ICorDebugClass`, alors que `Hashtable<Int32, String>` serait représenté par `ICorDebugType`.  
  
 Les types non génériques sont représentés par les deux `ICorDebugClass` et `ICorDebugType`. Cette dernière interface a été introduite dans le .NET Framework version 2.0 pour gérer l’instanciation de type.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
