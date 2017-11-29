---
title: "ICorDebugType::GetClass, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: be9999cd0dd8db5439dd41e51429841666597b16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass, méthode
Obtient un pointeur d’interface ICorDebugClass qui représente le type générique non instancié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppClass`  
 [out] Un pointeur vers l’adresse d’un `ICorDebugClass` interface qui représente le type générique non instancié.  
  
## <a name="remarks"></a>Remarques  
 `GetClass`peut être appelée uniquement sous certaines conditions. Appelez [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) avant d’appeler `GetClass`. Si `ICorDebugType::GetType` retourne une valeur CorElementType ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, `GetClass` peut être appelée pour obtenir le type non instancié pour un type générique.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
