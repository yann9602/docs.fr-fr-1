---
title: "ICorDebugNativeFrame::GetIP, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f9ea20577b3132a2378013e7c5fa8356c14c8b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetip-method"></a>ICorDebugNativeFrame::GetIP, méthode
Obtient le code natif offset emplacement auquel le pointeur d’instruction est actuellement défini.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pnOffset`  
 [out] Pointeur vers l’emplacement de décalage dans le code natif.  
  
## <a name="remarks"></a>Notes  
 Si le frame de pile qui est représenté par ce « ICorDebugNativeFrame » est actif, le décalage est l’adresse de l’instruction suivante à exécuter. Si ce frame de pile n’est pas actif, le décalage est l’adresse de l’instruction suivante à exécuter lorsque le frame de pile est réactivé.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 
