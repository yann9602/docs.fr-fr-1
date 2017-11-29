---
title: AssemblyBindInfo, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyBindInfo
helpviewer_keywords: AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f23c8269c7dd7f85ad0f848c1dee2ed0bf903c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo, structure
Fournit des informations détaillées sur l’assembly référencé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`dwAppDomainId`|Un identificateur unique pour le `IStream` retourné par un appel à [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), à partir de laquelle l’assembly référencé doit être chargé.|  
|`lpReferencedIdentity`|Identificateur unique pour l’assembly référencé.|  
|`lpPostPolicyIdentity`|Identificateur de l’assembly référencé après l’application de toutes les valeurs de stratégie de liaison.|  
|`ePolicyLevel`|Parmi les [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs qui indiquent quelles stratégies de contrôle de version, le cas échéant, doivent être appliqués à l’assembly référencé.|  
  
## <a name="remarks"></a>Remarques  
 L’hôte fournit l’identificateur unique `dwAppDomainId` pour le common language runtime (CLR). Après un appel à `IHostAssemblyStore::ProvideAssembly` retourne, le runtime utilise l’identificateur pour déterminer si le contenu de la `IStream` a été mappé. Dans ce cas, le runtime charge la copie existante plutôt que de remapper le flux. Le runtime utilise également cet identificateur en tant que clé de recherche des flux retournés d’appels à [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md). Par conséquent, l’identificateur doit être unique pour les demandes du module et des requêtes de l’assembly.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.idl  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [ICLRAssemblyIdentityManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ICLRAssemblyReferenceList (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [ModuleBindInfo (Structure)](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
