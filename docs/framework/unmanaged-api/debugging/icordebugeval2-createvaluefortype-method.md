---
title: "ICorDebugEval2::CreateValueForType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.CreateValueForType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 18e7eb5fc30c27fd2c4865dc61e2f75dc9e96068
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType, méthode
Obtient un pointeur vers un nouvel ICorDebugValue du type spécifié, avec une valeur initiale de zéro ou null.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pType`  
 [in] Pointeur vers un objet ICorDebugType qui représente le type.  
  
 `ppValue`  
 [out] Pointeur vers l’adresse d’un `ICorDebugValue` objet qui représente la valeur.  
  
## <a name="remarks"></a>Notes  
 `CreateValueForType`généralise [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) en vous permettant de spécifier un type d’objet arbitraire, y compris les types construits comme `List<int>`. Il est le seul objectif de cette méthode pour générer une valeur qui peut être passée à une évaluation de fonction.  
  
 Le type doit être une classe ou un type valeur. Vous ne pouvez pas utiliser cette méthode pour créer des valeurs de chaîne ou des valeurs de tableau.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
