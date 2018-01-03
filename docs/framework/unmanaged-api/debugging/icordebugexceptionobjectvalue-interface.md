---
title: ICorDebugExceptionObjectValue, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue
helpviewer_keywords: ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6ee743a5e3e28b5d8b864f325239725ca6c0042
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptionobjectvalue-interface"></a>ICorDebugExceptionObjectValue, interface
Étend l’interface « ICorDebugObjectValue » pour fournir des informations à partir d’un objet d’exception managée.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumerateExceptionCallStack, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|Obtient un énumérateur pour la pile des appels incorporée dans un objet d’exception.|  
  
## <a name="remarks"></a>Notes  
 L’appel à `QueryInterface` réussira pour des objets managés qui dérivent de <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
