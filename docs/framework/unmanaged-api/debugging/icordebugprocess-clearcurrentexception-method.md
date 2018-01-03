---
title: "ICorDebugProcess::ClearCurrentException, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ClearCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 905ade7e5c44861b4ad6e7eb57fe7d3e3e9e3002
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessclearcurrentexception-method"></a>ICorDebugProcess::ClearCurrentException, méthode
Efface l’exception non managée actuelle sur le thread donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `threadID`  
 [in] L’ID du thread sur lequel l’exception non managée actuelle sera effacée.  
  
## <a name="remarks"></a>Notes  
 Appelez cette méthode avant d’appeler [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) lorsqu’un thread a signalé une exception non managée qui doit être ignorée par le programme débogué. Efface l’en attente de bande (IB) et les événements hors-bande (OOB) sur le thread donné. Tous les points d’arrêt OOB et exceptions de la seule étape sont automatiquement effacées.  
  
 Utilisez [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) pour intercepter actuel gérés exception sur un thread.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
