---
title: "ICorDebugThread2::GetConnectionID, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetConnectionID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28fa949de768191061bd747034a5c951a03b8596
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2getconnectionid-method"></a>ICorDebugThread2::GetConnectionID, méthode
Obtient l’identificateur de connexion pour cet objet ICorDebugThread2.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwConnectionId`  
 [out] Un `CONNID` qui représente l’identificateur de connexion.  
  
## <a name="remarks"></a>Notes  
 Le `GetConnectionID` retourne la valeur zéro dans le `pdwConnectionId` paramètre, si ce thread n’est pas partie d’une connexion.  
  
 Si ce thread est connecté à une instance de Microsoft SQL Server 2005 Analysis Services (SSAS), le `CONNID` est mappé à un identificateur de processus serveur (SPID).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
