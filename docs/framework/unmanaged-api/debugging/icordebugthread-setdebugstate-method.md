---
title: "ICorDebugThread::SetDebugState, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.SetDebugState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 01f84c7126a4017a8d3b199f94eb497fae8e1a49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState, méthode
Définit les indicateurs qui décrivent l’état de débogage de ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `state`  
 [in] Combinaison de bits des valeurs d’énumération CorDebugThreadState qui spécifient l’état de débogage de ce thread.  
  
## <a name="remarks"></a>Remarques  
 `SetDebugState`définit l’état de débogage actuel du thread. (Le « état de débogage actuel » représente l’état de débogage si le processus de se poursuivre, pas l’état actuel réel.) La valeur normale est THREAD_RUNNING. Seul le débogueur peut affecter l’état de débogage d’un thread. États de débogage dernière à travers continue, donc si vous souhaitez conserver un thread THREAD_SUSPENDed sur plusieurs continue, vous pouvez définir une seule fois et au préoccupez pas. Suspendre les threads et la reprise du processus peuvent entraîner des blocages, bien qu’il soit généralement peu probable. Ceci est une qualité intrinsèque des threads et processus et de par sa conception. Un débogueur peut arrêter de façon asynchrone et reprendre les threads pour arrêter l’interblocage. Si l’état utilisateur du thread inclut USER_UNSAFE_POINT, le thread peut bloquer un garbage collection (GC). Cela signifie que le thread suspendu risque davantage de provoquer un interblocage. Cela peut affecter pas les événements sont déjà en file d’attente de débogage. Par conséquent, un débogueur doit vider la file d’attente de la totalité de l’événement (en appelant [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) avant de suspendre ou reprendre des threads. Sinon, il peut obtenir des événements sur un thread qu’elle estime qu’il a déjà suspendu.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
