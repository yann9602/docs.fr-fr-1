---
title: "IGCHostControl::RequestVirtualMemLimit, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHostControl.RequestVirtualMemLimit
api_location: mscoree.dll
api_type: COM
f1_keywords: RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4892cf5dc3a3663f1bccc95d1975bfe96277faa5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a>IGCHostControl::RequestVirtualMemLimit, méthode
Demande à l’hôte de modifier les limites de mémoire virtuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `sztMaxVirtualMemMB`  
 [in] La taille de la mémoire à allouer.  
  
 `psztNewMaxVirtualMemMB`  
 [dans, out] Pointeur vers la taille réelle de la mémoire allouée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IGCHostControl (Interface)](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
