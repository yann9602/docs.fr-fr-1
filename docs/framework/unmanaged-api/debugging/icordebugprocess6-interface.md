---
title: ICorDebugProcess6, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9928018b7d4065fbf24b4c39f7ef2d121e66d7ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6-interface"></a>ICorDebugProcess6, interface
Étend logiquement l’interface ICorDebugProcess pour activer des fonctionnalités telles que le décodage des événements de débogage managés qui sont codés dans les événements de débogage d’exception native et fractionnement de module virtuel.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[DecodeEvent, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|Décode les événements de débogage managés qui ont été encapsulés dans la charge utile des événements de débogage d'exception native conçus à cet effet.|  
|[EnableVirtualModuleSplitting, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|Active ou désactive le fractionnement de module virtuel.|  
|[GetCode, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|Obtient des informations sur le code managé à une adresse de code particulière.|  
|[GetExportStepInfo, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|Fournit des informations sur les fonctions exportées du runtime pour faciliter l'exécution pas à pas du code managé.|  
|[MarkDebuggerAttached, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|Change l'état interne du programme débogué pour que la méthode <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> de la bibliothèque de classes du .NET Framework retourne `true`.|  
|[ProcessStateChanged, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|Notifie [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) le processus est en cours d’exécution.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  L'interface est uniquement disponible avec .NET Native. Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
