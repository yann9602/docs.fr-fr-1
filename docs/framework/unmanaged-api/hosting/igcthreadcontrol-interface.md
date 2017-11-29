---
title: IGCThreadControl, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCThreadControl
helpviewer_keywords: IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 66afef7dec0637e98249838ae06ae6f1161df3f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl, interface
Fournit des méthodes pour participer à la planification des threads qui seraient sinon bloqués pour un garbage collection.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[SuspensionEnding (méthode)](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|Avertit l’hôte que le runtime est la reprise de threads après un garbage collection ou une suspension.|  
|[SuspensionStarting (méthode)](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|Avertit l’hôte que le runtime débute une suspension du thread pour un garbage collection ou une suspension.|  
|[ThreadIsBlockingForSuspension (méthode)](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|Avertit l’hôte que le thread qui effectue l’appel va bloquer, peut-être pour un garbage collection ou une suspension.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
