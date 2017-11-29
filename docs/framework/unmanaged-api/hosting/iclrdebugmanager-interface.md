---
title: ICLRDebugManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager
helpviewer_keywords: ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e537b955524f2721868ddf5da9fccf68f9d4efd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager, interface
Fournit des méthodes qui permettent à un hôte à associer un ensemble de tâches à un identificateur et un nom convivial.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BeginConnection, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|Établit une connexion entre l’hôte et le débogueur pour associer des tâches à un identificateur et un nom convivial.|  
|[EndConnection (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|Supprime l’association entre une liste de tâches et un identificateur et un nom convivial.|  
|[GetDacl (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|Cette méthode n’est pas implémentée.|  
|[IsDebuggerAttached (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|Obtient une valeur qui indique si un débogueur est attaché au processus.|  
|[SetConnectionTasks (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|Associe une liste de [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances avec un identificateur et un nom convivial.|  
|[SetDacl (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|Cette méthode n’est pas implémentée.|  
|[SetSymbolReadingPolicy (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|Définit la stratégie pour la lecture des fichiers de programme (PDB) de la base de données. La stratégie détermine si les informations sur les fichiers et les numéros de ligne sont incluses dans les piles d’appels.|  
  
## <a name="remarks"></a>Remarques  
 Dans les scénarios de débogage, un hôte peut souhaiter regrouper des tâches en fonction de sa propre logique de programmation. Par exemple, un regroupement permettrait à un développeur d’afficher uniquement les tâches requises par les API du développeur, au lieu d’afficher toutes les tâches en cours d’exécution dans le processus. `ICLRDebugManager`permet à l’hôte implémenter ce type de regroupement.  
  
> [!IMPORTANT]
>  Trois `ICLRDebugManager` méthodes, `BeginConnection`, `SetConnectionTasks` et `EndConnection`, dépendent les uns des autres. Elles doivent être appelées dans l’ordre indiqué à fonctionner comme prévu.  
  
 Le regroupement et les identificateurs et les noms conviviaux que l’hôte assigne au regroupement, n’ont aucune signification pour le common language runtime (CLR). Le CLR passe simplement les informations au débogueur.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
