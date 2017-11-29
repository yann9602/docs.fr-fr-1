---
title: "ICorDebugThread::GetActiveChain, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetActiveChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3f104933bc70682a531c0853cfc6eabcd357831
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetactivechain-method"></a>ICorDebugThread::GetActiveChain, méthode
Obtient un pointeur d’interface vers la chaîne de pile active (la plus récente) sur cet objet ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppChain`  
 [out] Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne de pile.  
  
## <a name="remarks"></a>Remarques  
 Le `ppChain` paramètre est null si aucune chaîne de pile n’est actuellement actif.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
