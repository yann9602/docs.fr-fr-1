---
title: "ICorDebugVariableHome::GetOffset (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetOffset
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09f80a362d4b44d13c39218b9d7a0db11ef49f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetoffset-method"></a>ICorDebugVariableHome::GetOffset (méthode)
Obtient le décalage à partir du Registre de base d’une variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pOffset`  
 [out] Le décalage à partir du Registre de base.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne les valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La variable est dans un emplacement de mémoire relative au Registre.|  
|`E_FAIL`|La variable n’est pas dans un emplacement de mémoire relative au Registre.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugVariableHome, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
