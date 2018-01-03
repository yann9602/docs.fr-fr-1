---
title: "ICorDebugType::GetType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c07f9974d0178a1a7502a97d54d7103ee795425f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType, méthode
Obtient une valeur CorElementType qui décrit le type natif du common language runtime (CLR) <xref:System.Type> représenté par cet ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ty`  
 [out] Un pointeur vers une valeur de la `CorElementType` énumération qui indique le CLR <xref:System.Type> par ce `ICorDebugType` représente.  
  
## <a name="remarks"></a>Notes  
 Si la valeur de `ty` est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, la [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) méthode peut être appelée pour obtenir le type non instancié pour un type générique ; sinon, n’appelez pas `ICorDebugType::GetClass`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
