---
title: "ICorDebugFunction2::SetJMCStatus, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ecbcd5b8171a169fbfdd7175d3d9dfbbcb3855f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus, méthode
Marque la fonction représentée par ICorDebugFunction2 pour uniquement mon Code pas à pas détaillé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bIsJustMyCode`  
 [in] La valeur `true` pour marquer la fonction en tant que code utilisateur ; sinon, valeur `false`.  
  
## <a name="return-values"></a>Valeurs de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|La fonction a été marquée avec succès.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|La fonction n’a pas pu être marquée comme du code utilisateur, car il ne peut pas être débogué.|  
  
## <a name="remarks"></a>Remarques  
 Une exécution pas à pas uniquement mon Code ignorera le code non-utilisateur. Code utilisateur doit être un sous-ensemble de code pouvant être débogué.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
