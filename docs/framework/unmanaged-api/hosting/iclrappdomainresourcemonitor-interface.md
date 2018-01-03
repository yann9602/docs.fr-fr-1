---
title: ICLRAppDomainResourceMonitor, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor
helpviewer_keywords: ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bebd39fce4f6aa6f570b3af348332bf7bcc87ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrappdomainresourcemonitor-interface"></a>ICLRAppDomainResourceMonitor, interface
Fournit des méthodes qui inspectent mémoire et l’utilisation de l’UC d’un domaine d’application.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCurrentAllocated, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|Obtient la taille totale, en octets, de toutes les allocations de mémoire effectuées par le domaine d’application depuis sa création, sans soustraire la mémoire qui a été par le garbage collector.|  
|[GetCurrentSurvived, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|Obtient le nombre d’octets qui ont survécu à la dernière complète, le garbage collection de blocage et qui sont référencés par le domaine d’application actuel.|  
|[GetCurrentCpuTime, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|Obtient le temps processeur total utilisé par tous les threads pendant leur exécution dans le domaine d’application actuel, depuis le domaine d’application a été créé.|  
  
## <a name="remarks"></a>Notes  
 Le `ICLRAppDomainResourceMonitor` interface fournit des fonctionnalités qui sont semblables aux propriétés managées suivantes :  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [\<appDomainResourceMonitoring > élément](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [Analyse de ressource de domaine d'application](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hébergement d’applications WPF](../../../../docs/framework/unmanaged-api/hosting/index.md)
