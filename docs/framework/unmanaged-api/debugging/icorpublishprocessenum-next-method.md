---
title: "ICorPublishProcessEnum::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcessEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6823a8d973b997576da3271c85234b347f1c8562
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessenumnext-method"></a>ICorPublishProcessEnum::Next, méthode
Obtient le nombre spécifié de processus à partir de la collection, en commençant à la position actuelle du curseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre de processus à récupérer.  
  
 `objects`  
 [out] Un pointeur vers le tableau de récupérer [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objets, chacun d’eux représente un processus.  
  
 `pceltFetched`  
 [out] Pointeur vers le nombre de processus retournés. Cette valeur peut être null si `celt` fait partie.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub.idl, CorPub.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorPublishProcessEnum (Interface)](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)
