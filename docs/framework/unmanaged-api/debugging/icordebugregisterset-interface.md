---
title: ICorDebugRegisterSet, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet
helpviewer_keywords: ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 714f3d7839ce1d8b65405b6cb3c91d43f1db6642
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet, interface
Représente le jeu de registres disponibles sur l’ordinateur qui exécute actuellement le code.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetRegisters, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) qui est spécifié par le masque de bits.|  
|[GetRegistersAvailable, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|Obtient un masque de bits indiquant les registres dans ce `ICorDebugRegisterSet` sont actuellement disponibles.|  
|[GetThreadContext, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|Obtient le contexte du thread actuel.|  
|[SetRegisters, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|Non implémenté pour le .NET Framework version 2.0.|  
|[SetThreadContext, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|Non implémenté pour le .NET Framework 2.0.|  
  
## <a name="remarks"></a>Notes  
 Le `ICorDebugRegisterSet` interface prend en charge les registres 32 bits uniquement. Utilisez le [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface sur les plateformes IA-64 qui requièrent des registres supplémentaires.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugRegisterSet2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
