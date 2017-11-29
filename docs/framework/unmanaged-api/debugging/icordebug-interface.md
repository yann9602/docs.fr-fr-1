---
title: ICorDebug, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug
helpviewer_keywords: ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62a29133252277cbf614a1916af6fa4c6905a920
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebug-interface"></a>ICorDebug, interface
Fournit des méthodes qui permettent aux développeurs de déboguer des applications dans l’environnement du common language runtime (CLR).  
  
> [!NOTE]
>  Débogage en mode mixte (code managé et natif) n’est pas pris en charge sur Windows 95, Windows 98 ou Windows Millennium Edition ou sur les plateformes non-x86 (par exemple, IA64 et AMD64).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CanLaunchOrAttach (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|Détermine si le lancement d’un nouveau processus ou l’attachement au processus donné est possible dans le contexte de la configuration actuelle de l’ordinateur et d’exécution.|  
|[CreateProcess (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|Lance un processus et son thread principal sous le contrôle du débogueur.|  
|[DebugActiveProcess (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|Attache le débogueur à un processus existant.|  
|[EnumerateProcesses (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|Obtient un énumérateur pour les processus en cours de débogage.|  
|[GetProcess (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|Retourne l’objet « ICorDebugProcess » avec l’ID de processus donné.|  
|[Initialize (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|Initialise le `ICorDebug` objet.|  
|[SetManagedHandler (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|Spécifie l’objet de gestionnaire d’événements pour les événements managés.|  
|[SetUnmanagedHandler (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|Spécifie l’objet de gestionnaire d’événements pour les événements non gérés.|  
|[Terminate (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|Met fin à la `ICorDebug` objet.|  
  
## <a name="remarks"></a>Remarques  
 `ICorDebug`représente une boucle de traitement d’événements pour un processus du débogueur. Le débogueur doit attendre le [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) rappel de tous les processus en cours de débogage avant de libérer cette interface.  
  
 Le `ICorDebug` objet est l’objet initial pour contrôler tout débogage managé supplémentaire. Dans les versions 1.0 et 1.1 du .NET Framework, cet objet a été un `CoClass` objet créé à partir de COM. Dans le .NET Framework version 2.0, cet objet n’est plus un `CoClass` objet. Il doit être créé par le [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) fonction, qui est plus en charge des versions. Cette nouvelle fonction de création permet aux clients d’obtenir une implémentation spécifique de `ICorDebug`, qui émule également une version spécifique de l’API de débogage.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
