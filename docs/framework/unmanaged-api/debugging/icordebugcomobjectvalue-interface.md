---
title: Interface ICorDebugComObjectValue
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugComObjectValue
helpviewer_keywords: ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9adeec14e102ef575f24566980477a285f87ba40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvalue-interface"></a>Interface ICorDebugComObjectValue
Fournit des méthodes pour récupérer les informations associées à un wrapper RCW (RCW).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCachedInterfacePointers, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Obtient les pointeurs d’interface brut mis en cache sur le wrapper RCW en cours.|  
|[GetCachedInterfaceTypes, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Fournit un énumérateur pour les types d’interfaces que l’objet actuel a été à la casse ou utilisé en tant que.|  
  
## <a name="remarks"></a>Notes  
 Pour vérifier si une instance d’une interface « ICorDebugValue » représente un wrapper RCW, appelle un débogueur `QueryInterface` sur « ICorDebugValue » avec `IID_ICorDebugComObjectValue`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
