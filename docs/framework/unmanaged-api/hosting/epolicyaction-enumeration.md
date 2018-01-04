---
title: "EPolicyAction, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EPolicyAction
api_location: mscoree.dll
api_type: COM
f1_keywords: EPolicyAction
helpviewer_keywords: EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5de55d46eead37962fad7d7c1c5bd1766e772fe8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction, énumération
Décrit les actions de stratégie que l’hôte peut définir pour les opérations décrites par [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) et les échecs décrits par [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eAbortThread`|Spécifie que le common language runtime (CLR) doit abandonner le thread normalement. Un abandon correct implique des tentatives d’exécution de tous les `finally` bloque les `catch` blocs liés aux abandons de thread et les finaliseurs.|  
|`eDisableRuntime`|Spécifie que le CLR doit entrer dans un état désactivé. Aucun autre code managé peut être exécuté dans le processus affecté et les threads sont empêchés d’entrer dans le CLR.|  
|`eExitProcess`|Spécifie que le CLR doit tenter une sortie normale du processus, y compris l’exécution des finaliseurs et effectuer des opérations de nettoyage et la journalisation.|  
|`eFastExitProcess`|Spécifie que le CLR doit quitter le processus immédiatement, sans exécuter les finaliseurs ou effectuer des opérations de nettoyage et la journalisation. Toutefois, la notification est envoyée au débogueur.|  
|`eNoAction`|Spécifie qu’aucune action doit être effectuée.|  
|`eRudeAbortThread`|Spécifie que le CLR doit effectuer un abandon de thread non applicables. Seuls les `catch` et `finally` blocs marqués avec <xref:System.EnterpriseServices.MustRunInClientContextAttribute> sont exécutées.|  
|`eRudeExitProcess`|Spécifie que le CLR doit quitter le processus sans exécuter les finaliseurs ou la journalisation des opérations.|  
|`eRudeUnloadAppDomain`|Spécifie que le CLR doit effectuer un déchargement brutal de le <xref:System.AppDomain>. Seuls les finaliseurs marqués avec <xref:System.EnterpriseServices.MustRunInClientContextAttribute> sont exécutées. De même, tous les threads avec cette <xref:System.AppDomain> dans leur pile reçoivent un `ThreadAbortException`, mais uniquement ceux `catch` et `finally` blocs marqués avec <xref:System.EnterpriseServices.MustRunInClientContextAttribute> sont exécutées.|  
|`eThrowException`|Spécifie qu’une exception correspondant à la condition, tels que l’insuffisance de mémoire, un dépassement de tampon, etc., doit être levée.|  
|`eUnloadAppDomain`|Spécifie que le <xref:System.AppDomain> doit être déchargée. Le CLR tente d’exécuter des finaliseurs.|  
  
## <a name="remarks"></a>Notes  
 L’hôte définit des actions de stratégie en appelant des méthodes de la [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface. Pour plus d’informations sur les abandons non applicables et ordonnés, consultez le [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) énumération.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [EClrFailure, énumération](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [ICLRPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [IHostPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
