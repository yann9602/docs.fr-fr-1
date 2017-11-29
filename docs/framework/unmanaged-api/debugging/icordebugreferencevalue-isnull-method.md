---
title: "ICorDebugReferenceValue::IsNull, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue.IsNull
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8a7892900149380c979f0bee1a4229407af8c9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugreferencevalueisnull-method"></a>ICorDebugReferenceValue::IsNull, méthode
Obtient une valeur qui indique si cette ICorDebugReferenceValue est une valeur null, auquel cas le `ICorDebugReferenceValue` ne pointe pas vers un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbNull`  
 [out] Un pointeur vers une valeur booléenne qui est `true` si ce `ICorDebugReferenceValue` objet est null ; sinon, `pbNull` est `false`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
