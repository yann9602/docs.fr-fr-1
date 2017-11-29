---
title: "Énumérations d'hébergement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged enumerations [.NET Framework], hosting
- enumerations [.NET Framework hosting]
- hosting enumerations [.NET Framework]
ms.assetid: e09131eb-1f7d-4f52-ae42-7393e9b62ef6
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f415b4f3062a83f97d2bf186981289cf16e555a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-enumerations"></a>Énumérations d'hébergement
Cette section décrit les énumérations non managées utilisées par l’API d’hébergement.  
  
## <a name="in-this-section"></a>Dans cette section  
 [CLSID_RESOLUTION_FLAGS (énumération)](../../../../docs/framework/unmanaged-api/hosting/clsid-resolution-flags-enumeration.md)  
 Contient des valeurs qui indiquent comment le common language runtime (CLR) doit résoudre un `CLSID`.  
  
 [COR_GC_STAT_TYPES (énumération)](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)  
 Spécifie les statistiques à enregistrer pour un garbage collection.  
  
 [COR_GC_THREAD_STATS_TYPES (énumération)](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-types-enumeration.md)  
 Indique les statistiques d’un thread de garbage collection.  
  
 [EApiCategories (énumération)](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 Décrit les catégories de fonctionnalités que l’hôte peut bloquer l’exécution dans du code partiellement fiable.  
  
 [EBindPolicyLevels (énumération)](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md)  
 Fournit des indicateurs qui spécifient le niveau auquel appliquer ou modifier une stratégie de l’assembly.  
  
 [ECLRAssemblyIdentityFlags (énumération)](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md)  
 Indique le type de l’identité d’un assembly.  
  
 [EClrEvent (énumération)](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 Décrit les événements CLR pour lequel l’hôte peut enregistrer des rappels.  
  
 [EClrFailure (énumération)](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 Décrit l’ensemble des erreurs pour lequel un hôte peut définir des actions de stratégie.  
  
 [EClrOperation (énumération)](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 Décrit l’ensemble des opérations pour lesquelles un hôte peut appliquer des actions de stratégie.  
  
 [EClrUnhandledException (énumération)](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)  
 Décrit les options disponibles pour la gestion des exceptions qui ne sont pas gérées dans le code utilisateur.  
  
 [EContextType (énumération)](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 Décrit le contexte de sécurité du thread en cours d’exécution.  
  
 [ECustomDumpFlavor (énumération)](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 Contient des valeurs qui indiquent les éléments à inclure dans un sous-ensemble personnalisé d’un segment de mémoire de vidage lors du signalement des erreurs.  
  
 [ECustomDumpItemKind (énumération)](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 Réservé à l’extension future de la [CustomDumpItem (Structure)](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) structure.  
  
 [EHostApplicationPolicy (énumération)](../../../../docs/framework/unmanaged-api/hosting/ehostapplicationpolicy-enumeration.md)  
 Indique comment modifier un [IHostAssemblyManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md) objet d’interface. Cette énumération a été déconseillée.  
  
 [EHostBindingPolicyModifyFlags (énumération)](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md)  
 Permet à l’hôte spécifier le type de redirection que le CLR doit effectuer lors de l’application des modifications de la stratégie à partir d’un assembly source vers un assembly cible.  
  
 [EInitializeNewDomainFlags (énumération)](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)  
 Permet à l’hôte de fournir le runtime avec des informations sur l’initialisation d’un domaine d’application.  
  
 [EMemoryAvailable (énumération)](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md)  
 Contient des valeurs qui indiquent la quantité de mémoire physique disponible sur l’ordinateur.  
  
 [EMemoryCriticalLevel (énumération)](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)  
 Contient des valeurs qui indiquent l’impact d’un échec lors de l’allocation de mémoire spécifique a été demandée, mais ne peut pas être satisfaite.  
  
 [EPolicyAction (énumération)](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 Décrit les actions de stratégie que l’hôte peut définir pour les opérations décrites par [EClrOperation, énumération](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) et les échecs décrits par [EClrFailure, énumération](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
 [ESymbolReadingPolicy (énumération)](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md)  
 Contient des valeurs qui définissent la stratégie pour la lecture des fichiers de programme (PDB) de la base de données.  
  
 [ETaskType (énumération)](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md)  
 Contient des valeurs qui indiquent le type de tâche représentée par une [ICLRTask (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) ou [IHostTask (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.  
  
 [HOST_TYPE (énumération)](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)  
 Contient des valeurs qui spécifient le type d’hôte qui lance une application.  
  
 [MALLOC_TYPE (énumération)](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md)  
 Contient des valeurs qui spécifient les caractéristiques de la mémoire est allouée.  
  
 [METAHOST_CONFIG_FLAGS (énumération)](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md)  
 Décrit les indicateurs possibles retournés dans le `pdwConfigFlags` paramètre de la [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) (méthode).  
  
 [METAHOST_POLICY_FLAGS (énumération)](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)  
 Fournit des stratégies de liaison qui sont communes à la plupart des hôtes de runtime.  
  
 [RUNTIME_INFO_FLAGS (énumération)](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)  
 Contient des valeurs qui indiquent les informations sur le CLR doivent être retournées.  
  
 [StackOverflowType (énumération)](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md)  
 Contient des valeurs qui indiquent la cause sous-jacente d’un événement de dépassement de capacité de pile.  
  
 [STARTUP_FLAGS (énumération)](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)  
 Contient des valeurs qui indiquent le comportement de démarrage du CLR.  
  
 [ValidatorFlags (énumération)](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)  
 Contient des valeurs qui indiquent le type de validation doit être effectuée dans un appel à [méthode Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md).  
  
 [WAIT_OPTION (énumération)](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)  
 Indique l’action de qu'un hôte doit prendre si l’opération demandée par le CLR se bloque.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Coclasses d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [Fonctions d’hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [Structures d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
