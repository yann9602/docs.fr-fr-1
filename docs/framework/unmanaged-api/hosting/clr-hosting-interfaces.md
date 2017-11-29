---
title: "Interfaces d'hébergement du CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3efdf649d0039f2eb6b39d5cb17c839b90e97508
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="clr-hosting-interfaces"></a>Interfaces d'hébergement du CLR
Cette section décrit les interfaces non managées hôtes peuvent utiliser pour intégrer le common language runtime (CLR) dans leurs applications. Les informations relatives à la version du .NET Framework 2.0 et versions ultérieures. Ces interfaces permettent à l’hôte de contrôler beaucoup plus d’aspects du runtime que les versions 1.0 et 1.1 et fournissent ainsi l’intégration entre le CLR et le modèle d’exécution de l’ordinateur hôte.  
  
 Dans la version 1.0 et 1.1 du .NET Framework, le modèle d’hébergement activé un hôte non managé de charger le CLR dans un processus, de configurer certains paramètres et de recevoir des notifications d’événements. Toutefois, en général, l’hôte et le CLR s’exécutaient indépendamment dans ce processus. Dans le .NET Framework version 2.0 et les versions ultérieures, des couches d’abstraction permettent à l’hôte fournit plusieurs ressources actuellement offertes par les types dans l’assembly Win32, et l’ensemble de fonctionnalités que l’hôte peut configurer.  
  
## <a name="in-this-section"></a>Dans cette section  
 [IActionOnCLREvent (Interface)](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Fournit une méthode qui effectue un rappel pour un événement enregistré.  
  
 [IApartmentCallback (Interface)](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Fournit des méthodes pour effectuer des rappels dans un thread cloisonné.  
  
 [IAppDomainBinding (Interface)](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Fournit des méthodes pour la configuration de l’exécution.  
  
 [ICatalogServices (Interface)](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Fournit des méthodes pour les services de catalogage. (Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement depuis votre code.)  
  
 [ICLRAssemblyIdentityManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 Fournit des méthodes qui prennent en charge la communication entre l’hôte et le CLR sur les assemblys.  
  
 [ICLRAssemblyReferenceList (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 Gère une liste d’assemblys qui sont chargés par le CLR et non par l’hôte.  
  
 [ICLRControl (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Fournit des méthodes pour l’hôte d’accéder à et de configurer différents aspects du CLR.  
  
 [ICLRDebugManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Fournit des méthodes qui permettent à un hôte à associer un ensemble de tâches à un identificateur et un nom convivial.  
  
 [ICLRErrorReportingManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Fournit des méthodes qui permettent à l’hôte configurer des dumps de tas personnalisés pour le rapport d’erreurs.  
  
 [ICLRGCManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du CLR.  
  
 [ICLRHostBindingPolicyManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Fournit des méthodes pour l’hôte d’évaluer et de communiquer les modifications dans les informations de stratégie pour les assemblys.  
  
 [ICLRHostProtectionManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Permet à l’hôte bloquer les classes managées spécifiques, les méthodes, les propriétés et les champs de l’exécution dans du code partiellement fiable.  
  
 [ICLRIoCompletionManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 Implémente une méthode de rappel qui permet à l’hôte informer le CLR de l’état des demandes d’e/s spécifiées.  
  
 [ICLRMemoryNotificationCallback (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Permet à l’hôte de signaler des conditions de sollicitation de la mémoire à l’aide d’une approche similaire à celle de Win32 `CreateMemoryResourceNotification` (fonction).  
  
 [ICLROnEventManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Fournit des méthodes qui permettent à l’hôte inscrire et désinscrire des rappels pour les événements du CLR.  
  
 [ICLRPolicyManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 Fournit des méthodes qui permettent à l’hôte spécifier les actions à entreprendre en cas de défaillances et des délais d’expiration de stratégie.  
  
 [ICLRProbingAssemblyEnum (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 Fournit des méthodes qui permettent à l’hôte d’obtenir les identités d’identification d’un assembly à l’aide des informations d’identité de l’assembly qui est internes au CLR, sans avoir à créer ou à comprendre cette identité.  
  
 [ICLRReferenceAssemblyEnum (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Fournit des méthodes qui permettent à l’hôte de manipuler le jeu d’assemblys référencés par un fichier ou un flux à l’aide des données d’identité qui est internes au CLR, sans avoir à créer ou à comprendre ces identités.  
  
 [ICLRRuntimeHost (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Fournit des fonctions semblables à [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), avec une méthode supplémentaire pour définir l’interface de contrôle hôte.  
  
 [ICLRSyncManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 Fournit des méthodes pour l’ordinateur hôte pour obtenir des informations sur les tâches demandées et pour détecter les blocages dans son implémentation de synchronisation.  
  
 [ICLRTask (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 Fournit des méthodes qui permettent à l’hôte pour effectuer des demandes du CLR, ou pour fournir une notification au CLR sur la tâche associée.  
  
 [ICLRTaskManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 Fournit des méthodes qui permettent à l’hôte à demander explicitement que le CLR crée une tâche et obtenir la tâche en cours d’exécution et définir le langage géographique et la culture pour la tâche.  
  
 [ICLRValidator (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Fournit des méthodes pour la validation des images (PE) exécutables portables et de rapports d’erreurs de validation.  
  
 [ICorConfiguration (Interface)](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 Fournit des méthodes pour la configuration du CLR.  
  
 [ICorThreadpool (Interface)](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 Fournit des méthodes pour accéder au pool de threads.  
  
 [IDebuggerInfo (Interface)](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Fournit des méthodes pour obtenir des informations sur l’état des services de débogage.  
  
 [IDebuggerThreadControl (Interface)](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Fournit des méthodes pour notifier l’hôte sur le blocage et déblocage des threads par les services de débogage.  
  
 [IGCHost (Interface)](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Fournit des méthodes pour obtenir des informations sur le système de garbage collection et contrôler certains aspects du garbage collection.  
  
 [IGCHost2 (Interface)](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Fournit la [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) méthode qui permet à un hôte définir la taille du segment garbage collection et la taille maximale de la génération du système de garbage collection zéro aux valeurs supérieur `DWORD`.  
  
 [IGCHostControl (Interface)](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Fournit une méthode qui permet au garbage collector de demander à l’hôte de modifier les limites de mémoire virtuelle.  
  
 [IGCThreadControl (Interface)](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Fournit des méthodes pour participer à la planification des threads qui seraient sinon bloqués pour le garbage collection.  
  
 [IHostAssemblyManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 Fournit des méthodes qui permettent à un hôte de spécifier des ensembles d’assemblys qui doivent être chargés par le CLR ou par l’hôte.  
  
 [IHostAssemblyStore (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Fournit des méthodes qui permettent à un hôte de charger des assemblys et des modules indépendamment du CLR.  
  
 [IHostAutoEvent (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Fournit une représentation d’un événement de réinitialisation automatique implémenté par l’hôte.  
  
 [IHostControl (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Fournit des méthodes pour configurer le chargement d’assemblys et pour déterminer quelles interfaces d’hébergement l’hôte prend en charge.  
  
 [IHostCrst (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 Sert de représentation sous forme de l’hôte d’une section critique pour les threads.  
  
 [IHostGCManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 Fournit des méthodes qui notifier l’hôte d’événements dans le mécanisme de garbage collection implémentés par le CLR.  
  
 [IHostIoCompletionManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Fournit des méthodes qui permettent au CLR d’interagir avec les ports de terminaison d’e/s fournis par l’hôte.  
  
 [IHostMalloc (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 Fournit des méthodes pour le CLR demander des allocations fines à partir du tas via l’hôte.  
  
 [IHostManualEvent (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Fournit l’implémentation de l’hôte d’une représentation d’un événement de réinitialisation manuelle.  
  
 [IHostMemoryManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Fournit des méthodes pour le CLR effectuer des demandes de mémoire virtuelle via l’hôte, au lieu d’utiliser les fonctions de mémoire virtuelle Win32 standard.  
  
 [IHostPolicyManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Fournit des méthodes qui informent l’hôte des actions que le CLR effectue en cas d’abandon, les délais d’attente ou d’échec.  
  
 [IHostSecurityContext (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Permet de gérer les informations de contexte de sécurité implémentées par l’hôte au CLR.  
  
 [IHostSecurityManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Fournit des méthodes qui permettent d’accéder à et contrôlent le contexte de sécurité du thread en cours d’exécution.  
  
 [IHostSemaphore (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Fournit une représentation d’un sémaphore implémenté par l’hôte.  
  
 [IHostSyncManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Fournit des méthodes pour que le CLR crée des primitives de synchronisation en appelant l’hôte, au lieu d’utiliser les fonctions de synchronisation Win32.  
  
 [IHostTask (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Fournit des méthodes qui permettent au CLR de communiquer avec l’hôte pour gérer les tâches.  
  
 [IHostTaskManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Fournit des méthodes qui permettent au CLR de travailler avec les tâches via l’hôte au lieu d’utiliser les fonctions de threading ou fiber de système d’exploitation standard.  
  
 [IHostThreadPoolManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 Fournit des méthodes pour le CLR pour configurer le pool de threads et en file d’attente des éléments de travail au pool de threads.  
  
 [IManagedObject (Interface)](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Fournit des méthodes pour contrôler un objet managé.  
  
 « IObjectHandle »  
 Fournit une méthode pour désencapsuler les objets marshalés par valeur à partir de l’indirection.  
  
 [ITypeName (Interface)](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Fournit des méthodes pour obtenir des informations de nom de type. (Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement depuis votre code.)  
  
 [ITypeNameBuilder (Interface)](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Fournit des méthodes pour la création d’un nom de type. (Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement depuis votre code.)  
  
 [ITypeNameFactory (Interface)](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Fournit des méthodes pour détruire un nom de type. (Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement depuis votre code.)  
  
 « IValidator »  
 Fournit des méthodes pour la validation des images (PE) exécutables portables et de rapports d’erreurs de validation.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Les Coclasses et les Interfaces d’hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Contient des rubriques qui décrivent les interfaces d’hébergement fournis dans le .NET Framework version 1.0 et 1.1.  
  
 [Interfaces d’hébergement CLR est ajouté dans le .NET Framework 4 et 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Contient des rubriques qui décrivent les interfaces d’hébergement fournis dans le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].
