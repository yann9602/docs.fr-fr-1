---
title: ICorPublishProcess, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess
helpviewer_keywords: ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cb62da277ff13bea33969bb9c728cac5d5a15554
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess, interface
Fournit des méthodes qui accèdent aux informations à afficher sur un processus.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumAppDomains (méthode)](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|Obtient un [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance qui contient les domaines d’application dans le processus référencé par ce `ICorPublishProcess`.|  
|[GetDisplayName (méthode)](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|Obtient le chemin d’accès complet du fichier exécutable pour le processus référencé par ce `ICorPublishProcess`.|  
|[GetProcessID (méthode)](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|Obtient l’identificateur de système d’exploitation pour le processus référencé par ce `ICorPublishProcess`.|  
|[IsManaged, méthode](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|Obtient une valeur qui indique si le processus référencé par ce `ICorPublishProcess` est connu pour être en cours d’exécution du code managé.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub.idl, CorPub.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [CorpubPublish (coclasse)](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
