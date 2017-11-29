---
title: IHostAssemblyStore, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 284afbe73bea28a0aafe8d5e9e030c43be94aea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore, interface
Fournit des méthodes qui permettent à un hôte de charger des assemblys et des modules indépendamment le common language runtime (CLR).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ProvideAssembly, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|Obtient une référence à un assembly qui n’est pas référencé par le [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) retourné par un appel à [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[ProvideModule (méthode)](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|Résout un module dans un assembly ou un fichier de ressources (non incorporé) lié.|  
  
## <a name="remarks"></a>Remarques  
 `IHostAssemblyStore`fournit un moyen pour un hôte de charger efficacement des assemblys selon identité d’assembly. L’hôte charge les assemblys en retournant `IStream` instances qui pointent directement vers les octets.  
  
 Le CLR détermine si un hôte a implémenté `IHostAssemblyStore` en appelant `IHostAssemblyManager::GetNonHostAssemblyStores` lors de l’initialisation. Cela permet à l’hôte, par exemple, de contrôler la liaison aux assemblys d’utilisateur, mais s’appuyer sur le runtime pour la liaison aux assemblys .NET Framework.  
  
> [!NOTE]
>  Fournir une implémentation de `IHostAssemblyStore`, l’hôte spécifie son intention de résoudre tous les assemblys qui ne sont pas référencés par le `ICLRAssemblyReferenceList` retourné par `IHostAssemblyManager::GetNonHostStoreAssemblies`.  
  
> [!NOTE]
>  La version 2.0 du .NET Framework ne fournit pas un moyen de l’hôte de charger l’image native d’un assembly, tel que fourni par le [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utilitaire.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRAssemblyReferenceList (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
