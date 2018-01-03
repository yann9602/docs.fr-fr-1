---
title: ICorPublish, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublish
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublish
helpviewer_keywords: ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7769d26d65a97ea8d1b109e0098eae7e7d51ed10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublish-interface"></a>ICorPublish, interface
Sert d’interface générale pour la publication des informations sur les processus et des informations sur les domaines d’application dans ces processus.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumProcesses, méthode](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|Obtient un [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance qui contient les processus managés s’exécutant sur cet ordinateur.|  
|[GetProcess, méthode](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|Obtient un [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance qui représente le processus avec l’identificateur spécifié.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub.idl, CorPub.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [CorpubPublish, coclasse](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
