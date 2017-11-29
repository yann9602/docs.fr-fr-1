---
title: "STARTUP_FLAGS, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: STARTUP_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: STARTUP_FLAGS
helpviewer_keywords: STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ebfb45e6d568b4fa1db209264e02332df636474f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="startupflags-enumeration"></a>STARTUP_FLAGS, énumération
Contient des valeurs qui indiquent le comportement de démarrage du common language runtime (CLR). Par défaut, le garbage collection est non simultané et seule la bibliothèque de classes de base est chargée dans la zone indépendant du domaine.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|Spécifie que le garbage collection simultané doit être utilisé. Si l’appelant demande la build du serveur et le garbage collection simultané sur un ordinateur à un seul processeur, la build de la station de travail et le garbage collection non simultané sont exécutés à la place. **Remarque :** le garbage collection simultané n’est pas pris en charge dans les applications qui sont en cours d’exécution WOW64 x86 émulateur sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64). Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes 64 bits de Windows, consultez [Applications en cours d’exécution de 32 bits](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Spécifie que l’optimisation de chargeur doit se produire.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Spécifie qu’aucun assembly n’est chargé comme indépendant du domaine.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Spécifie que tous les assemblys sont chargés comme indépendants du domaine.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Spécifie que tous les assemblys avec nom fort sont chargés comme indépendants du domaine.|  
|`STARTUP_LOADER_SAFEMODE`|Spécifie que stratégie de version CLR n’est pas appliquée à la version passée. La version exacte spécifiée du CLR est chargée. Le shim n’évalue pas la stratégie pour déterminer la version compatible la plus récente.|  
|`STARTUP_LOADER_SETPREFERENCE`|Spécifie que le runtime par défaut doit être défini, mais pas démarré.|  
|`STARTUP_SERVER_GC`|Spécifie que la garbage collection côté serveur sera utilisée.|  
|`STARTUP_HOARD_GC_VM`|Spécifie que le garbage collection conserve l’adresse virtuelle utilisée.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Spécifie que mélange d’une interface d’hébergement n'est pas autorisé.|  
|`STARTUP_LEGACY_IMPERSONATION`|Spécifie que l’emprunt d’identité ne doit pas transmis entre des points asynchrones par défaut.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|Spécifie que la pile des threads complète ne doit pas être validée lorsque le thread commence à s’exécuter.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Spécifie que les emprunts d’identité managés et les emprunts d’identité obtenus via la plate-forme appellent seront transmis entre points asynchrones. Par défaut, seuls emprunts d’identité managés circule entre des points asynchrones.|  
|`STARTUP_TRIM_GC_COMMIT`|Spécifie que le garbage collection utilise moins d’espace validé lors de la mémoire système est insuffisante. Consultez `gcTrimCommitOnLowMemory` dans [optimisation pour l’hébergement Web partagé](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Spécifie que le suivi d’événements pour Windows (ETW) est activé pour les événements du common language runtime. À compter de Windows Vista, le suivi d’événements est toujours activé, cet indicateur n’a aucun effet. Consultez [contrôle de l’enregistrement .NET Framework](../../../../docs/framework/performance/controlling-logging.md).|  
|`STARTUP_ARM`|Spécifie que l’analyse de ressource de domaine d’application est activée. Consultez le <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> propriété et [ \<appDomainResourceMonitoring > élément](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
