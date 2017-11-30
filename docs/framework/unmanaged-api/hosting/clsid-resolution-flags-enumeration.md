---
title: "CLSID_RESOLUTION_FLAGS, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLSID_RESOLUTION_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: CLSID_RESOLUTION_FLAGS
helpviewer_keywords: CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17e74e8b39ff9079973063f4ea703607411ab93d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="clsidresolutionflags-enumeration"></a>CLSID_RESOLUTION_FLAGS, énumération
Contient des valeurs qui indiquent comment le common language runtime (CLR) doit résoudre un `CLSID`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|Indique le comportement par défaut.|  
|`CLSID_RESOLUTION_REGISTERED`|Indique que le runtime recherche dans le Registre et applique la stratégie de shim.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
