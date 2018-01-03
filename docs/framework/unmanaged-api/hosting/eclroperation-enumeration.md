---
title: "EClrOperation, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrOperation
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrOperation
helpviewer_keywords: EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 343ff04dba1a02660734beb726f9b895370a10af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="eclroperation-enumeration"></a>EClrOperation, énumération
Décrit l’ensemble des opérations pour lesquelles un hôte peut appliquer des actions de stratégie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|L’hôte peut spécifier des actions de stratégie à prendre lorsqu’un <xref:System.AppDomain> est déchargé de façon non progressive (brusque).|  
|`OPR_AppDomainUnload`|L’hôte peut spécifier des actions de stratégie à prendre lorsqu’un <xref:System.AppDomain> est déchargé.|  
|`OPR_FinalizerRun`|L’hôte peut spécifier des actions de stratégie à prendre lors de l’exécuteront des finaliseurs.|  
|`OPR_ProcessExit`|L’hôte peut spécifier des actions à entreprendre lorsque le processus s’arrête de stratégie.|  
|`OPR_ThreadAbort`|L’hôte peut spécifier des actions à entreprendre lorsqu’un thread est abandonné de stratégie.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|L’hôte peut spécifier des actions à entreprendre lorsqu’un abandon de thread non applicables se produit dans une région de code critique de stratégie.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|L’hôte peut spécifier des actions de stratégie à prendre lorsqu’un abandon de thread non applicables se produit dans une région de code non critique.|  
  
## <a name="remarks"></a>Notes  
 L’infrastructure de fiabilité du common language runtime (CLR) fait la distinction entre les abandons et ressources des échecs d’allocation qui se produisent dans les régions critiques de code et celles qui se produisent dans les régions de code non critiques. Cette distinction est conçue pour permettre aux hôtes de définir des stratégies différentes en fonction de l’endroit où une défaillance se produit dans le code.  
  
 A *région critique de code* est un espace où le CLR ne peut pas garantir qu’abandon d’une tâche ou l’échec d’une demande de ressources affectera uniquement la tâche en cours. Par exemple, si une tâche conserve un verrou et reçoit un HRESULT qui indique un échec lors d’une demande d’allocation de mémoire, il est insuffisant simplement pour abandonner cette tâche pour garantir la stabilité de la <xref:System.AppDomain>, car le <xref:System.AppDomain> peut contenir d’autres tâches en attente du verrou même. Abandon en cours tâche peut provoquer les autres tâches à cesser de répondre (blocage ou) indéfiniment. Dans ce cas, l’hôte doit pouvoir décharger l’intégralité de <xref:System.AppDomain> plutôt que de l’instabilité du risque.  
  
 A *région non critique de code*, quant à lui, est une région où le CLR peut garantir qu’un abandon ou un échec affectera uniquement la tâche sur laquelle l’erreur se produit.  
  
 Le CLR distingue également normale et les abandons abandons (non applicables). En général, un abandon normal ou correct fait en sorte d’exécuter des routines de gestion des exceptions et des finaliseurs avant d’abandonner une tâche, alors qu’un abandon brutal n’apporte aucune garantie de ce type.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [EClrFailure, énumération](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [EPolicyAction, énumération](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [ICLRPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [IHostPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
