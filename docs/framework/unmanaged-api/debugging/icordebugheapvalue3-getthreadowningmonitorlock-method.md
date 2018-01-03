---
title: "ICorDebugHeapValue3::GetThreadOwningMonitorLock, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a2198e54c764fde0248563b040ac98984001888
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock, méthode
Retourne le thread managé qui possède le verrou du moniteur sur cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppThread`  
 [out] Le thread managé qui possède le verrou du moniteur sur cet objet.  
  
 `pAcquisitionCount`  
 [out] Le nombre de fois où que ce thread aurait pour libérer le verrou avant qu’il redevienne sans propriétaire.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|S_FALSE|Aucun thread managé ne possède le verrou du moniteur sur cet objet.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
 Si un thread managé possède le verrou du moniteur sur cet objet :  
  
-   La méthode retourne S_OK.  
  
-   L’objet thread est valide jusqu'à ce que le thread se ferme.  
  
 Si aucun thread managé possède le verrou du moniteur sur cet objet, `ppThread` et `pAcquisitionCount` sont identiques, et la méthode retourne S_FALSE.  
  
 Si `ppThread` ou `pAcquisitionCount` n’est pas un pointeur valid, le résultat est indéfini.  
  
 Si une erreur se produit et il ne peut pas déterminer qui, le cas échéant, le thread possède le verrou du moniteur sur cet objet, la méthode retourne un HRESULT qui indique un échec.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
