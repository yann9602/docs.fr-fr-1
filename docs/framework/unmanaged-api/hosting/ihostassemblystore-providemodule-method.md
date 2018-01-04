---
title: "IHostAssemblyStore::ProvideModule, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore.ProvideModule
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b29f19933ae985d15627d1eba2622f350a52e72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule, méthode
Résout un fichier de ressources du module dans un assembly ou un élément lié (mais non incorporé).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pBindInfo`  
 [in] Un pointeur vers un [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance qui décrit le module demandé <xref:System.AppDomain>, assembly et le nom de module.  
  
 `pdwModuleId`  
 [out] Un pointeur vers un identificateur unique pour le `IStream` qui contient le module chargé.  
  
 `ppStmModuleImage`  
 [out] Un pointeur vers l’adresse d’un `IStream` de l’objet, qui contient l’image exécutable portable (PE) à charger, ou null si le module est introuvable.  
  
 `ppStmPDB`  
 [out] Un pointeur vers l’adresse d’un `IStream` de l’objet, qui contient les informations de débogage (PDB) de programme pour le module demandé, ou null si le fichier .pdb est introuvable.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ProvideModule`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance grave et inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0 X 80070002)|L’assembly demandé ou une ressource liée n’a pas pu être localisée.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId`n’est pas assez grande pour contenir l’identificateur que l’hôte souhaite retourner.|  
  
## <a name="remarks"></a>Notes  
 La valeur d’identité retournée pour `pdwModuleId` est spécifiée par l’hôte. Les identificateurs doivent être uniques au sein de la durée de vie d’un processus. Le CLR utilise cette valeur comme identificateur unique pour le flux associé. Il vérifie chaque valeur sur les valeurs de `pAssemblyId` retournées par les appels à [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) et les valeurs de `pdwModuleId` retourné par d’autres appels à `ProvideModule`. Si l’hôte retourne la même valeur d’identificateur pour une autre `IStream`, le CLR vérifie si le contenu de ce flux a déjà été mappé. Dans ce cas, le CLR charge la copie existante de l’image au lieu de mapper une nouvelle. Par conséquent, l’identificateur doit également se chevauchent pas avec les identificateurs de l’assembly retournés à partir de `ProvideAssembly`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRAssemblyReferenceList, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
