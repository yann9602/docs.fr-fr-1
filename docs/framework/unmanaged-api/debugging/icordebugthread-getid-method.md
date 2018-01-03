---
title: "ICorDebugThread::GetID, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cab889761c204204e7eda46fde0df42f31b89fbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetid-method"></a>ICorDebugThread::GetID, méthode
Obtient l’identificateur de système d’exploitation actuel de la partie active du ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwThreadId`  
 [out] L’identificateur du thread.  
  
## <a name="remarks"></a>Notes  
 L’identificateur de système d’exploitation susceptible d’être modifié pendant l’exécution d’un processus et peut être une valeur différente pour les différentes parties du thread.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
