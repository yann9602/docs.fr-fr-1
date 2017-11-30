---
title: "IGCThreadControl::SuspensionEnding, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl.SuspensionEnding
api_location: mscoree.dll
api_type: COM
f1_keywords: SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4460d2b0eaf10d20ddd0c3641279a8ffc05c245
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="igcthreadcontrolsuspensionending-method"></a>IGCThreadControl::SuspensionEnding, méthode
Avertit l’hôte que le runtime est la reprise de threads après un garbage collection ou une suspension.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Generation`  
 [in] La génération sur lequel une opération garbage collection a été effectuée.  
  
## <a name="remarks"></a>Remarques  
 Ne replanifiez pas de threads pendant le `SuspensionEnding` rappel.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IGCThreadControl (Interface)](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
