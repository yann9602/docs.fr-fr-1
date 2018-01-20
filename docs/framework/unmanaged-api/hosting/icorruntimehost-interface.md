---
title: ICorRuntimeHost, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost
helpviewer_keywords: ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1280c49c2eea6a06eca10ebd8896b0722e321547
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost, interface
Fournit des méthodes qui permettent à l’hôte démarrer et arrêter le common language runtime (CLR) explicitement, pour créer et configurer des domaines d’application, pour accéder au domaine par défaut et d’énumérer tous les domaines en cours d’exécution dans le processus.  
  
 Dans le .NET Framework version 2.0, cette interface est remplacée par [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CloseEnum, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|Réinitialise un énumérateur de domaine au début de la liste des domaines.|  
|[CreateDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|Crée un domaine d’application. L’appelant reçoit un pointeur d’interface de type <xref:System._AppDomain> à une instance de type <xref:System.AppDomain?displayProperty=nameWithType>.|  
|[CreateDomainEx, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|Crée un domaine d’application. Cette méthode permet à l’appelant de passer une instance IAppDomainSetup pour configurer des fonctionnalités supplémentaires de retourné <xref:System._AppDomain> instance.|  
|[CreateDomainSetup, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|Obtient un pointeur d’interface de type `IAppDomainSetup` à un <xref:System.AppDomainSetup> instance. `IAppDomainSetup`Fournit des méthodes pour configurer les aspects d’un domaine d’application avant qu’il est créé.|  
|[CreateEvidence, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|Obtient un pointeur d’interface de type <xref:System.Security.Principal.IIdentity>, ce qui permet à l’hôte de créer la preuve de sécurité à passer à [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) ou [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).|  
|[CreateLogicalThreadState, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|Ne pas utiliser.|  
|[CurrentDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|Obtient un pointeur d’interface de type <xref:System._AppDomain> qui représente le domaine chargé sur le thread actuel.|  
|[DeleteLogicalThreadState, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|Ne pas utiliser.|  
|[EnumDomains, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|Obtient un énumérateur pour les domaines dans le processus actuel.|  
|[GetConfiguration, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|Obtient un objet qui permet à l’hôte spécifier la configuration de rappel du CLR.|  
|[GetDefaultDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|Obtient un pointeur d’interface de type <xref:System._AppDomain> qui représente le domaine par défaut pour le processus actuel.|  
|[LocksHeldByLogicalThread, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|Ne pas utiliser.|  
|[MapFile, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|Mappe le fichier spécifié dans la mémoire. Cette méthode est obsolète.|  
|[NextDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|Obtient un pointeur d’interface au domaine suivant dans l’énumération.|  
|[Start, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|Démarre le CLR.|  
|[Stop, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|Arrête l’exécution de code dans le runtime pour le processus actuel.|  
|[SwitchInLogicalThreadState, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|Ne pas utiliser.|  
|[SwitchOutLogicalThreadState, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|Ne pas utiliser.|  
|[UnloadDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|Décharge le domaine d’application du processus en cours.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** 1.0, 1.1  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.AppDomain>  
 [Hébergement d’applications WPF](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [ICLRRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [Hôtes de runtime](http://msdn.microsoft.com/library/99d9246a-b994-4fe5-985c-8588d1d59998)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CorRuntimeHost, coclasse](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
