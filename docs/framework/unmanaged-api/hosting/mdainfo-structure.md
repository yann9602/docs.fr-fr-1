---
title: MDAInfo, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: MDAInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: MDAInfo
helpviewer_keywords: MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53a999028f2677599598caf55e62f10721f61fe3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="mdainfo-structure"></a>MDAInfo, structure
Fournit des détails sur la `Event_MDAFired` événement qui déclenche la création d’un assistant débogage managé (MDA).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`lpMDACaption`|Le titre de l’Assistant Débogage MANAGÉ actuel. Le titre décrit le genre d’échec qui a déclenché la `Event_MDAFired` événement.|  
|`lpMDAMessage`|Le message de sortie fourni par l’Assistant Débogage MANAGÉ actuel.|  
  
## <a name="remarks"></a>Notes  
 Assistants de débogage managés (MDA) sont outils de débogage qui fonctionnent conjointement avec le common language runtime (CLR) pour effectuer des tâches telles que l’identification des conditions non valides dans le moteur d’exécution ou le vidage des informations supplémentaires sur l’état de la moteur. MDA génèrent des messages XML sur les événements qui sont difficiles à intercepter. Ils sont particulièrement utiles pour déboguer des transitions entre code managé et non managé.  
  
 Le runtime effectue les étapes suivantes lorsqu’un événement qui déclenche la création d’un Assistant Débogage MANAGÉ est déclenché :  
  
-   Si l’hôte n’a pas inscrit un [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance en appelant [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) recevoir les notifications d’un `Event_MDAFired` événement, le runtime continue avec son comportement par défaut, non hébergé.  
  
-   Si l’ordinateur hôte a inscrit un gestionnaire pour cet événement, le runtime vérifie si un débogueur est attaché au processus. S’il s’agit, le runtime arrête le débogueur. Lorsque le débogueur continue, il appelle l’hôte. Si aucun débogueur n’est attaché, le runtime appelle `IActionOnCLREvent::OnEvent` et passe un pointeur vers un `MDAInfo` l’instance comme le `data` paramètre.  
  
 L’hôte peut choisir d’activer les MDA et d’être averti quand un Assistant Débogage MANAGÉ est activé. Cela permet de l’hôte de substituer le comportement par défaut et d’abandonner le thread managé qui a déclenché l’événement pour l’empêcher d’endommager l’état du processus. Pour plus d’informations sur l’utilisation des Assistants Débogage managé, consultez [diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.idl  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
