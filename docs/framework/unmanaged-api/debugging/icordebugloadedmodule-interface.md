---
title: ICorDebugLoadedModule (interface)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cc7a36deb7c81ccf67427b833dead7127619b39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodule-interface"></a>ICorDebugLoadedModule (interface)
Fournit des informations sur un module chargé.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBaseAddress, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|Obtient l'adresse de base du module chargé.|  
|[GetName, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|Obtient le nom du module chargé.|  
|[GetSize, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|Obtient la taille en octets du module chargé.|  
  
## <a name="remarks"></a>Notes  
 L'interface `ICorDebugLoadedModule` est implémentée par un débogueur et est utilisée par les interfaces de débogage du CLR pour obtenir des informations sur le module chargé à partir du débogueur.  
  
> [!NOTE]
>  Cette interface est uniquement disponible avec .NET Native. Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
