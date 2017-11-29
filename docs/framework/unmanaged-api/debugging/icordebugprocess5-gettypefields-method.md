---
title: "ICorDebugProcess5::GetTypeFields, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeFields
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7a64e754a77c7d730d921f8a8c1547dd18b66d77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields, méthode
Fournit des informations sur les champs qui appartiennent à un type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `id`  
 [in] L’identificateur du type dont les informations de champ sont récupérées.  
  
 `celt`  
 [in] Le nombre de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objets dont les informations de champ doit être récupéré.  
  
 `fields`  
 [out] Un tableau de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) des objets qui fournissent des informations sur les champs qui appartiennent au type.  
  
 `pceltNeeded`  
 [out] Un pointeur vers le nombre de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objets inclus dans `fields`.  
  
## <a name="remarks"></a>Remarques  
 Le `celt` paramètre qui spécifie le nombre de champs dont la méthode utilise pour renseigner les informations de champ `fields`, doit correspondre à la valeur de la `COR_TYPE_LAYOUT::numFields` champ.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Icordebugprocess5, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
