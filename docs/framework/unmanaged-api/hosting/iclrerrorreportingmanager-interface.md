---
title: ICLRErrorReportingManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager
helpviewer_keywords: ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ac362432a5d0c613f4ee1409ee15d92bfef3aeb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager, interface
Fournit des méthodes qui permettent à l’hôte configurer des vidages de pile personnalisé pour le rapport d’erreurs.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BeginCustomDump, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|Spécifie la configuration de vidages de pile personnalisé pour le rapport d’erreurs.|  
|[EndCustomDump, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|Efface la configuration du vidage de pile personnalisée qui a été définie par un appel précédent à `BeginCustomDump`.|  
|[GetBucketParametersForCurrentException, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Obtient le compartiment Watson de l’exception actuelle sur le thread appelant.|  
  
## <a name="remarks"></a>Notes  
 Le `BeginCustomDump` méthode définit la configuration de vidage de pile personnalisée. Le `EndCustomDump` méthode efface la configuration de vidage de pile personnalisée et libère tout état associé. Il doit être appelée une fois que le dump personnalisé est terminé.  
  
> [!IMPORTANT]
>  Échec d’appel `EndCustomDump` provoque une fuite de mémoire.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ECustomDumpItemKind, énumération](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
