---
title: "ICLRErrorReportingManager::GetBucketParametersForCurrentException, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager.GetBucketParametersForCurrentException
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager::GetBucketParametersForCurrentException
helpviewer_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException method [.NET Framework hosting]
- GetBucketParametersForCurrentException method [.NET Framework hosting]
ms.assetid: a13ec8a6-8e18-4acb-8054-77f5b1a0e0b9
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f920ceb802231112ef1b855fd0a78d3a0e6ca4c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a>ICLRErrorReportingManager::GetBucketParametersForCurrentException, méthode
Obtient le compartiment Watson de l’exception actuelle sur le thread appelant.  
  
 A *compartiment* est une collection de données qui sont liées à la même erreur de code d’erreur. *Watson* fait référence à un ensemble de technologies de collecte et analyse des données qui sont associées à une exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pParams`  
 [out] Un pointeur vers un [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure qui contient les données d’erreur pour l’exception.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRErrorReportingManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
