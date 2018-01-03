---
title: "ICorDebugType::GetBase, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetBase
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c28c88988155cf5e00897858d4306e4cb2ea78a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetbase-method"></a>ICorDebugType::GetBase, méthode
Obtient un pointeur d’interface vers ICorDebugType qui représente le type de base, s’il en existe, du type représenté par ce `ICorDebugType`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pBase`  
 [out] Un pointeur vers l’adresse d’un `ICorDebugType` objet qui représente le type de base.  
  
## <a name="remarks"></a>Notes  
 Recherche le type de base pour un type est utile pour implémenter des fonctionnalités communes du débogueur, telles que l’impression de tous les champs d’un objet ou ses classes parent.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
