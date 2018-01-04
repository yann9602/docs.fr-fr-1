---
title: "EClrFailure, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrFailure
helpviewer_keywords: EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e25a5378349dd476321765bb085db958e29670e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="eclrfailure-enumeration"></a>EClrFailure, énumération
Décrit l’ensemble des erreurs pour lequel un hôte peut définir des actions de stratégie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|Une erreur s’est produite pendant une tentative d’allouer une ressource (par exemple, un thread, un bloc de mémoire ou un verrou) dans une région de code non critique.|  
|`FAIL_CriticalResource`|Une erreur s’est produite pendant une tentative d’allouer une ressource (par exemple, un thread, un bloc de mémoire ou un verrou) dans une région de code critique.|  
|`FAIL_FatalRuntime`|Le common language runtime (CLR) n’est plus en mesure d’exécuter du code managé dans le processus. Désormais, les appels à toute fonction d’hébergement retournent une valeur HRESULT de HOST_E_CLRNOTAVAILABLE.|  
|`FAIL_OrphanedLock`|Un thread n’a pas pu libérer un verrou lors du retour d’un <xref:System.AppDomain> objet. L’hôte ne peut pas définir cet échec pour provoquer l’abandon d’un thread.|  
|`FAIL_StackOverflow`|Un débordement de pile s’est produite.|  
|`FAIL_AccessViolation`|Une tentative a été effectuée pour lire ou écrire la mémoire protégée. Non pris en charge dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].|  
|`FAIL_CodeContract`|Un échec de contrat de code s’est produite. Consultez [les contrats de Code](../../../../docs/framework/debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Notes  
 Consultez le [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) méthode pour obtenir la liste de [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs de l’hôte peut utiliser pour spécifier les actions de stratégie pour les conditions d’échec. Pour plus d’informations sur les régions non critiques et de code, consultez [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [SetActionOnFailure, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)  
 [IHostPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
