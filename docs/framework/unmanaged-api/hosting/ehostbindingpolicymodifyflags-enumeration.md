---
title: "EHostBindingPolicyModifyFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EHostBindingPolicyModifyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: EHostBindingPolicyModifyFlags
helpviewer_keywords: EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ff7ec7487be649e353b48e537cf1d8d45f6962
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>EHostBindingPolicyModifyFlags, énumération
Permet à l’hôte spécifier le type de redirection que le common language runtime (CLR) doit effectuer lors de l’application des modifications de la stratégie à partir d’un assembly source vers un assembly cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|Spécifie que le CLR doit chaîner les valeurs de stratégie de l’assembly source vers ceux de l’assembly cible.|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|Spécifie que le CLR exécute l’action par défaut.|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|Spécifie que le CLR définit les valeurs de stratégie de l’assembly cible pour les valeurs maximales.|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|Spécifie que le CLR doit remplacer les valeurs de stratégie de l’assembly cible avec celles de l’assembly source.|  
  
## <a name="remarks"></a>Remarques  
 Le [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) méthode prend un paramètre de type `EHostBindingPolicyModifyFlags`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRHostBindingPolicyManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
