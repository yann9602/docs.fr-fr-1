---
title: "ICorDebugObjectValue::GetFieldValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.GetFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fcf53610cf96ef1ab62b4768521e8a2fb7ee6c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue, méthode
Obtient la valeur du champ spécifié de la classe spécifiée pour la valeur de cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pClass`  
 [in] Pointeur vers un objet « ICorDebugClass » qui représente la classe pour laquelle obtenir la valeur du champ.  
  
 `fieldDef`  
 [in] Un `mdFieldDef` jeton qui référence les métadonnées décrivant le champ.  
  
 `ppValue`  
 [out] Pointeur vers un objet « ICorDebugValue » qui représente la valeur du champ spécifié.  
  
## <a name="remarks"></a>Notes  
 La classe spécifiée dans le `pClass` paramètre doit être dans la hiérarchie de classe de la valeur d’objet, et le champ doit être un champ de cette classe.  
  
 Le `GetFieldValue` méthode continuera à aboutir pour les objets génériques et les classes génériques. Par exemple, si MonDictionnaire\<V > hérite de dictionnaire\<de chaîne, V >, et la valeur de l’objet est de type MonDictionnaire\<int32 >, en passant le `ICorDebugClass` objet dictionnaire\<K, V > sera récupérer un champ de dictionnaire\<string, int32 >.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
    
 
