---
title: "Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61231715a24978e7fe57b2c9e87e7968dc0fdbc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5
Cette section décrit les interfaces non managées hôtes peuvent utiliser pour intégrer le common language runtime (CLR) dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]et les versions ultérieures dans leurs applications. Ces interfaces fournissent des méthodes pour un ordinateur hôte configurer et charger le runtime dans un processus.  
  
 En commençant par le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], l’hébergement de toutes les interfaces ont les caractéristiques suivantes :  
  
-   Elles utilisent la gestion de la durée de vie (`AddRef` et `Release`), l’encapsulation (contexte implicite) et `QueryInterface` à partir de COM.  
  
-   Elles n’utilisent pas les types COM tels que `BSTR`, `SAFEARRAY`, ou `VARIANT`.  
  
-   Aucun modèle cloisonné, d’agrégation, ou l’activation de Registre qui utilisent la [fonction CoCreateInstance](http://go.microsoft.com/fwlink/?LinkId=142894).  
  
## <a name="in-this-section"></a>Dans cette section  
 [ICLRAppDomainResourceMonitor, interface](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 Fournit des méthodes qui inspectent mémoire et l’utilisation de l’UC d’un domaine d’application.  
  
 [ICLRDomainManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 Permet à l’hôte spécifier le Gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut et pour spécifier les propriétés d’initialisation.  
  
 [ICLRGCManager2, interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 Fournit la [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) (méthode), ce qui permet à un hôte définir la taille du segment garbage collection et la taille maximale de la génération du système de garbage collection 0 pour les valeurs supérieure à `DWORD`.  
  
 [ICLRMetaHost, interface](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 Fournit des méthodes qui retournent une version spécifique du CLR, répertorient tous les installés, répertorient tous les runtimes in-process, retournent l’interface d’activation et découvrir la version CLR utilisée pour compiler un assembly.  
  
 [ICLRMetaHostPolicy, interface](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 Fournit la [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) méthode qui fournit une interface CLR selon des critères de stratégie assembly managé et la version des fichiers de configuration.  
  
 [ICLRRuntimeInfo, interface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 Fournit des méthodes qui retournent des informations sur un runtime spécifique, y compris la version, le répertoire et l’état de charge.  
  
 [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 Fournit des fonctions statiques globales de base pour la signature des assemblys avec des noms forts. Tous les [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) méthodes retournent des valeurs HRESULT COM standard.  
  
 [ICLRStrongName2, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 Fournit la possibilité de créer des noms forts dans le groupe de SHA-2 d’algorithmes de hachage sécurisé (SHA-256, SHA-384 et SHA-512).  
  
 [ICLRTask2, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 Fournit toutes les fonctionnalités de la [ICLRTask (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); en outre, fournit des méthodes qui permettent d’abandons de threads pour être retardée sur le thread actuel.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Coclasses et interfaces d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Décrit les interfaces d’hébergement fournis avec les versions de .NET Framework 1.0 et 1.1.  
  
 [Interfaces d’hébergement CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 Décrit les interfaces d’hébergement fournis avec les versions de .NET Framework 2.0, 3.0 et 3.5.  
  
 [Hébergement d’applications WPF](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 Présente l’hébergement dans le .NET Framework.
