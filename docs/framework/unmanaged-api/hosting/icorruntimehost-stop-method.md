---
title: "ICorRuntimeHost::Stop, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f6bf66065293107efae7f401a584b7342f29125
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehoststop-method"></a>ICorRuntimeHost::Stop, méthode
Arrête l’exécution de code dans le runtime pour le processus actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L’opération a réussi.|  
|S_FALSE|L’opération a échoué.|  
|E_FAIL|Une défaillance grave et inconnue s’est produite. Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus. Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.|  
  
## <a name="remarks"></a>Remarques  
 Il est généralement pas nécessaire d’appeler le `Stop` (méthode), car le code s’arrête l’exécution lorsque le processus s’arrête.  
  
> [!NOTE]
>  Après un appel à `Stop`, le CLR ne peut pas être réinitialisé dans le même processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** 1.0, 1.1  
  
## <a name="see-also"></a>Voir aussi  
 [ICorRuntimeHost (Interface)](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
