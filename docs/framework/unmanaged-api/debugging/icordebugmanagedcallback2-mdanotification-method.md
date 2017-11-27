---
title: "ICorDebugManagedCallback2::MDANotification, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.MDANotification
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aeddab575f6667dbd27ab3474ae9c6e00dd05750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification, méthode
Fournit une notification indiquant que l’exécution du code a rencontré un assistant débogage managé (MDA) dans l’application en cours de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pController`  
 [in] Pointeur vers un ICorDebugController (interface) qui expose le processus ou le domaine d’application dans lequel l’Assistant Débogage MANAGÉ s’est produite.  
  
 Un débogueur n’a pas doit faire d’hypothèses concernant si le contrôleur est un processus ou un domaine d’application, bien qu’il puisse toujours interroger l’interface pour effectuer une détermination.  
  
 `pThread`  
 [in] Pointeur vers une interface ICorDebugThread qui expose le thread managé sur lequel l’événement de débogage s’est produite.  
  
 Si l’Assistant Débogage MANAGÉ s’est produite sur une fonction non managée de thread, la valeur de `pThread` sera null.  
  
 Vous devez obtenir l’ID de thread de système d’exploitation (OS) à partir de l’objet MDA lui-même.  
  
 `pMDA`  
 [in] Un pointeur vers un [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface qui expose les informations MDA.  
  
## <a name="remarks"></a>Remarques  
 Un MDA est un avertissement heuristique et ne nécessite aucune action du débogueur explicite, à l’exception d’appel [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) pour reprendre l’exécution de l’application est en cours de débogage.  
  
 Le common language runtime (CLR) peut déterminer quels MDA sont déclenchés et les données qui sont dans n’importe quel MDA donné à tout moment. Par conséquent, les débogueurs ne doivent pas générer de fonctionnalités nécessitant des modèles MDA spécifiques.  
  
 Assistants Débogage managé peut être en file d’attente et déclenchés juste après que l’Assistant Débogage MANAGÉ est rencontré. Cela peut se produire si le runtime doit attendre jusqu'à ce qu’il atteigne un point sans risque pour déclencher le MDA, au lieu de déclencher lorsqu’elle rencontre. Cela signifie également que le runtime peut déclencher un nombre d’Assistants Débogage managé dans un seul jeu de rappels en file d’attente (similaires à une opération d’événement « liaison »).  
  
 Un débogueur doit libérer la référence à un `ICorDebugMDA` instance immédiatement après le retour à partir de la `MDANotification` rappel, pour permettre au CLR de recycler la mémoire consommée par un Assistant Débogage MANAGÉ. Libérer l’instance peut améliorer les performances si déclenchent des nombreux MDA.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [ICorDebugManagedCallback2 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
