---
title: "ICorDebugValue::GetAddress, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetAddress
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7018dcb41f46d5407549f5c3d3029716781014e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluegetaddress-method"></a>ICorDebugValue::GetAddress, méthode
Obtient l’adresse de cet objet « ICorDebugValue », qui est en cours de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pAddress`  
 [out] Pointeur vers un `CORDB_ADDRESS` objet qui spécifie l’adresse de cet objet de valeur.  
  
## <a name="remarks"></a>Remarques  
 Si la valeur n’est pas disponible, 0 (zéro) est retournée. Cela peut se produire si la valeur est au moins en partie dans les registres ou stockées dans un handle de garbage collector (`GCHandle`).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 
