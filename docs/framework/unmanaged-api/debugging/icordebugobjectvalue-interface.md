---
title: ICorDebugObjectValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue
helpviewer_keywords: ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6dfde9f212936b1a0d0f5a6e76eafd4a2e62356c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvalue-interface1"></a>ICorDebugObjectValue Interface1
Une sous-classe de « ICorDebugValue » qui représente une valeur qui contient un objet.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetClass, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|Obtient un pointeur d’interface pour le common language runtime (CLR) <xref:System.Type> de l’objet que cette `ICorDebugObjectValue` références.|  
|[GetContext, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|Non implémenté.|  
|[GetFieldValue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|Obtient un pointeur d’interface vers un [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) qui représente la valeur du champ spécifié de la classe spécifiée.|  
|[GetManagedCopy, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|Obsolète. N’appelez pas cette méthode.|  
|[GetVirtualMethod, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|Non implémenté.|  
|[IsValueClass, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|Obtient une valeur qui indique si l’objet référencé par ce `ICorDebugObjectValue` est un type valeur.|  
|[SetFromManagedCopy, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|Obsolète. N’appelez pas cette méthode.|  
  
## <a name="remarks"></a>Notes  
 Un `ICorDebugObjectValue` reste valide jusqu'à ce que le processus en cours de débogage se poursuit.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 
