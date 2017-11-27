---
title: "EApiCategories, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EApiCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: EApiCategories
helpviewer_keywords: EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eaff0133020fe84e58f8a130bffc8ddc2a55a19d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="eapicategories-enumeration"></a>EApiCategories, énumération
Décrit les catégories de fonctionnalités que l’hôte peut bloquer l’exécution dans du code partiellement fiable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eAll`|Spécifie que tous gérés des classes et membres qui sont couverts par d’autres `EApiCategories` champs pas s’exécuter dans du code partiellement fiable.|  
|`eExternalProcessMgmt`|Spécifie que les classes et les membres qui permettent la création, la manipulation et la destruction de processus externes doit être bloquée en cours d’exécution dans du code partiellement fiable.|  
|`eExternalThreading`|Spécifie que les classes et les membres qui permettent la création, la manipulation et la destruction de threads externes doit être bloquée en cours d’exécution dans du code partiellement fiable.|  
|`eMayLeakOnAbort`|Spécifie que les types managés et les membres qui pourraient potentiellement une fuite de mémoire d’abandon doit être bloquée en cours d’exécution dans du code partiellement fiable.|  
|`eNoCategory`|Spécifie qu’aucune catégorie de code managé doit être bloquée en cours d’exécution dans du code partiellement fiable.|  
|`eSecurityInfrastructure`|Spécifie que l’infrastructure de sécurité du common language runtime (CLR) doit être bloquée utilisé par du code partiellement fiable.|  
|`eSelfAffectingProcessMgmt`|Spécifie que les classes et les membres dont les fonctions peuvent affecter le processus hébergé doit être bloquée en cours d’exécution dans du code partiellement fiable.|  
|`eSelfAffectingThreading`|Spécifie que les classes et les membres dont les fonctions peuvent affecter des threads dans le processus hébergé doit être bloquée en cours d’exécution dans du code partiellement fiable.|  
|`eSharedState`|Spécifie que les classes et les membres qui exposent l’état partagé doit être bloquée en cours d’exécution dans du code partiellement fiable.|  
|`eSynchronization`|Spécifie que les classes du Common language runtime et les membres qui permettent de conserver des verrous de code utilisateur courants être bloqué de s’exécuter dans du code partiellement fiable.|  
|`eUI`|Spécifie que les classes et les membres qui autorisent ou nécessitent une interaction humaine doit être bloquée en cours d’exécution dans du code partiellement fiable.|  
  
## <a name="remarks"></a>Remarques  
 Le [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) méthode prend un paramètre de type `EApiCategories`.  
  
 Le `EApiCategories` énumération et la `SetProtectedCategories` méthode sont directement liés à la <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> classe. La classe managée est utilisée avec la <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> énumération, dont les valeurs correspondent directement à la `EApiCategories` pour marquer des types managés et les membres qui exposent des fonctions correspondant aux catégories décrites par les valeurs `EApiCategories`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRHostProtectionManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
