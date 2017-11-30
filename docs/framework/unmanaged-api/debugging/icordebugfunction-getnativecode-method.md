---
title: "ICorDebugFunction::GetNativeCode, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetNativeCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2fccfaeb346d59f5cf565f47a9a64e732706adad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode, méthode
Obtient le code natif pour la fonction qui est représentée par cette instance ICorDebugFunction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppCode`  
 [out] Pointeur vers l’instance ICorDebugCode qui représente le code natif pour cette fonction, ou null, si cette fonction est le code Microsoft intermediate language (MSIL) qui n’a pas été compilé juste-à-temps (JIT).  
  
## <a name="remarks"></a>Remarques  
 Si la fonction qui est représentée par ce `ICorDebugFunction` instance a été compilé par JIT plusieurs fois, comme dans le cas des types génériques, `GetNativeCode` retourne un objet de code natif aléatoire.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
