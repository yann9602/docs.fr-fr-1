---
title: "ICorDebugInternalFrame2::GetFrameAddress, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2.GetFrameAddress Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f44f0707892197398e4638a5e6d037fba7c8fc71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2getframeaddress-method"></a>ICorDebugInternalFrame2::GetFrameAddress, méthode
Retourne l’adresse de la pile du frame interne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pAddress`  
 [out] Pointeur vers le `CORDB_ADDRESS` pour le frame interne.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L’adresse du frame interne a été retourné avec succès.|  
|E_FAIL|L’adresse du frame interne n’a pas pu être retourné.|  
|E_INVALIDARG|`pAddress` a la valeur `null`.|  
  
## <a name="remarks"></a>Notes  
 La valeur retournée dans `pAddress` peut être utilisé pour déterminer l’emplacement du frame interne par rapport aux autres frames sur la pile. Même sur les ordinateurs basés sur IA-64, le frame interne vit uniquement sur la pile, et il n’existe aucun pointeur correspondant vers un magasin de stockage.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugInternalFrame2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
