---
title: "ICLRRuntimeHost::ExecuteInDefaultAppDomain, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ae0e006cdaa983fd7a3c9f650b61d4579aeaf0ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a>ICLRRuntimeHost::ExecuteInDefaultAppDomain, méthode
Appelle la méthode spécifiée du type spécifié dans l’assembly managé spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwzAssemblyPath`  
 [in] Le chemin d’accès à la <xref:System.Reflection.Assembly> qui définit le <xref:System.Type> dont la méthode doit être appelée.  
  
 `pwzTypeName`  
 [in] Le nom de la <xref:System.Type> qui définit la méthode à appeler.  
  
 `pwzMethodName`  
 [in] Le nom de la méthode à appeler.  
  
 `pwzArgument`  
 [in] Le paramètre de chaîne à passer à la méthode.  
  
 `pReturnValue`  
 [out] La valeur entière retournée par la méthode appelée.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ExecuteInDefaultAppDomain`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance grave et inconnue s’est produite. Si une méthode retourne E_FAIL, la liste de révocation n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  
 La méthode appelée doit avoir la signature suivante :  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 où `pwzMethodName` représente le nom de la méthode appelée, et `pwzArgument` représente la valeur de chaîne passée en tant que paramètre à cette méthode. Si la valeur HRESULT est définie à S_OK, `pReturnValue` est définie sur la valeur entière retournée par la méthode appelée. Dans le cas contraire, `pReturnValue` n’est pas définie.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRRuntimeHost (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
