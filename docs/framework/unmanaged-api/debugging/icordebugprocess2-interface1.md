---
title: ICorDebugProcess2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2
helpviewer_keywords: ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80f6c35ba2ef2ec74293d0f025ddf20254f504a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2-interface1"></a>ICorDebugProcess2 Interface1
Extension logique de l’interface ICorDebugProcess, qui représente un processus en cours d’exécution du code managé.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|Supprime un point d’arrêt à l’offset spécifié qui a été défini par un appel précédent à `ICorDebugProcess2::SetUnmanagedBreakpoint`.|  
|[GetDesiredNGENCompilerFlags, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|Obtient les indicateurs qui doivent être définis pour le common language runtime (CLR) pour charger l’image dans le processus référencé par ce `ICorDebugProcess2`.|  
|[GetReferenceValueFromGCHandle, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|Obtient un pointeur de référence à l’objet managé spécifié qui a un garbage collection à gérer.|  
|[GetThreadForTaskID, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|Obtient le thread sur lequel s’exécute la tâche avec l’identificateur spécifié.|  
|[GetVersion, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|Obtient la version du CLR sur laquelle le processus en cours de débogage s’exécute.|  
|[SetDesiredNGENCompilerFlags, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|Définit les indicateurs qui sont requis pour le compilateur juste-à-temps (JIT) charger une image dans le processus en cours de débogage.|  
|[SetUnmanagedBreakpoint, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|Définit un point d’arrêt non managé à l’offset d’image native spécifié.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
