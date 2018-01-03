---
title: "ICorDebugInternalFrame2::IsCloserToLeaf, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b6b769c25e0cd706eb57965b73d0fcfdcf9b9ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a>ICorDebugInternalFrame2::IsCloserToLeaf, méthode
Vérifie si le `this` frame interne est proche de la feuille de l’objet ICorDebugFrame spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pFrameToCompare`  
 [in] Un pointeur vers la comparaison `ICorDebugFrame` objet.  
  
 `pIsCloser`  
 [out] `true` si le `this` frame interne est proche de la feuille que le frame spécifié par `pFrameToCompare`; sinon, `false`.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La comparaison a été effectuée avec succès.|  
|E_FAIL|La comparaison n’a pas pu être effectuée.|  
|E_INVALIDARG|`pFrameToCompare` ou `pIsCloser` est null.|  
  
## <a name="remarks"></a>Notes  
 `IsCloserToLeaf`peut être utilisé pour implémenter une stratégie pour entrelacer les frames internes avec d’autres frames sur la pile.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugInternalFrame2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
