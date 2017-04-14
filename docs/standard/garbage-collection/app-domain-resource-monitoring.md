---
title: "Application Domain Resource Monitoring | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "monitoring managed memory use by application domain"
  - "application domains, memory use"
  - "memory use, monitoring"
  - "application domains, resource monitoring"
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Application Domain Resource Monitoring
L'analyse de ressource de domaine d'application \(ARM\) permet aux hôtes de contrôler l'utilisation de l'UC et de la mémoire par domaine d'application.  Ceci est utile pour les hôtes tels qu'ASP.NET qui utilisent de nombreux domaines d'application dans un processus de longue durée.  L'hôte peut décharger le domaine d'application d'une application qui affecte de façon défavorable les performances de l'ensemble du processus, mais uniquement s'il peut identifier l'application problématique.  ARM fournit des informations qui peuvent être utilisées pour faciliter la prise de telles décisions.  
  
 Par exemple, un service d'hébergement peut avoir de nombreuses applications qui fonctionnent sur un serveur ASP.NET.  Si une application du processus commence à consommer trop de mémoire ou trop de temps processeur, le service d'hébergement peut utiliser ARM pour identifier le domaine d'application qui provoque le problème.  
  
 ARM est suffisamment léger pour être utilisé dans des applications actives.  Vous pouvez accéder aux informations à l'aide du suivi d'événements pour Windows \(ETW\) ou directement via des API managées ou natives.  
  
## Activation de l'analyse de ressource  
 ARM peut être activé de quatre façons : en fournissant un fichier de configuration lorsque le Common Language Runtime \(CLR\) est démarré, en utilisant une API d'hébergement non managée, en utilisant du code managé ou en écoutant des événements ETW ARM.  
  
 Dès que ARM est activé, il commence à collecter des données sur tous les domaines d'application du processus.  Si un domaine d'application a été créé avant l'activation de ARM, les données cumulatives démarrent avec l'activation de ARM, pas au moment de la création du domaine d'application. Une fois activé, ARM ne peut pas être désactivé.  
  
-   Vous pouvez activer ARM au démarrage du CLR en ajoutant l'élément [\<appDomainResourceMonitoring\>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) au fichier de configuration et en affectant à l'attribut `enabled` la valeur `true`.  La valeur `false` \(valeur par défaut\) signifie uniquement que ARM n'est pas activé au démarrage. Vous pouvez l'activer ultérieurement à l'aide de l'un des autres mécanismes d'activation.  
  
-   L'hôte peut activer ARM en demandant l'interface d'hébergement [ICLRAppDomainResourceMonitor](../../../ocs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md).  Une fois cette interface obtenue avec succès, ARM est activé.  
  
-   Le code managé peut activer ARM en définissant la propriété \(`Shared` en Visual Basic\) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=fullName> statique sur `true`.  Une fois la propriété définie, ARM est activé.  
  
-   Vous pouvez activer ARM après le démarrage en écoutant les événements ETW.  ARM est activé et commence à déclencher des événements pour tous les domaines d'application lorsque vous activez le fournisseur public `Microsoft-Windows-DotNETRuntime` à l'aide du mot clé `AppDomainResourceManagementKeyword`.  Pour mettre en corrélation des données avec les domaines d'application et les threads, vous devez également activer le fournisseur `Microsoft-Windows-DotNETRuntimeRundown` avec le mot clé `ThreadingKeyword`.  
  
## Utilisation de ARM  
 ARM fournit le temps processeur total utilisé par un domaine d'application et trois genres d'informations à propos de l'utilisation de la mémoire.  
  
-   **Temps processeur total pour un domaine d'application, en secondes** : calculé en additionnant les temps de thread signalés par le système d'exploitation pour tous les threads qui ont passé du temps à s'exécuter dans le domaine d'application pendant leur durée de vie.  Les threads bloqués ou en veille n'utilisent pas de temps processeur.  Lorsqu'un thread appelle en code natif, le temps que le thread passe en code natif est inclus dans le nombre pour le domaine d'application où l'appel a été passé.  
  
    -   API managée : propriété <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=fullName>.  
  
    -   API d'hébergement : méthode [ICLRAppDomainResourceMonitor::GetCurrentCpuTime](../Topic/ICLRAppDomainResourceMonitor::GetCurrentCpuTime%20Method.md).  
  
    -   Événements ETW : événements `ThreadCreated`, `ThreadAppDomainEnter` et `ThreadTerminated`.  Pour plus d'informations sur les fournisseurs et mots clés, consultez « Événements de contrôle des ressources AppDomain » dans [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md).  
  
-   **Allocations managées totales faites par un domaine d'application pendant sa durée de vie, en octets** : les allocations totales ne reflètent pas toujours l'utilisation de la mémoire par un domaine d'application, car les objets alloués peuvent être éphémères.  Toutefois, si une application alloue et libère de grandes quantités d'objets, le coût des allocations peut être significatif.  
  
    -   API managée : propriété <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=fullName>.  
  
    -   API d'hébergement : méthode [ICLRAppDomainResourceMonitor::GetCurrentAllocated](../Topic/ICLRAppDomainResourceMonitor::GetCurrentAllocated%20Method.md).  
  
    -   Événements ETW : événement `AppDomainMemAllocated`, champ `Allocated`.  
  
-   **Mémoire managée, en octets, qui est référencée par un domaine d'application et qui a survécu à la collecte bloquante complète la plus récente** : ce nombre est exact uniquement après une collecte bloquante complète. \(Les collectes simultanées, au contraire, se produisent en arrière\-plan et ne bloquent pas l'application.\) Par exemple, la surcharge de méthode <xref:System.GC.Collect?displayProperty=fullName> entraîne une collecte bloquante complète.  
  
    -   API managée : propriété <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=fullName>.  
  
    -   API d'hébergement : méthode [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../Topic/ICLRAppDomainResourceMonitor::GetCurrentSurvived%20Method.md), paramètre `pAppDomainBytesSurvived`.  
  
    -   Événements ETW : événement `AppDomainMemSurvived`, champ `Survived`.  
  
-   **Mémoire managée totale, en octets, qui est référencée par le processus et qui a survécu à la collecte bloquante complète la plus récente** : la mémoire ayant survécu des domaines d'application individuels peut être comparée à ce nombre.  
  
    -   API managée : propriété <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=fullName>.  
  
    -   API d'hébergement : méthode [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../Topic/ICLRAppDomainResourceMonitor::GetCurrentSurvived%20Method.md), paramètre `pTotalBytesSurvived`.  
  
    -   Événements ETW : événement `AppDomainMemSurvived`, champ `ProcessSurvived`.  
  
### Détermination d'une collecte bloquante complète  
 Pour déterminer quand la quantité de mémoire ayant survécu est exacte, vous devez savoir quand une collecte bloquante complète s'est produite.  La méthode utilisée pour cela dépend de l'API que vous utilisez pour examiner les statistiques ARM.  
  
#### API managée  
 Si vous utilisez les propriétés de la classe <xref:System.AppDomain>, vous pouvez utiliser la méthode <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=fullName> pour vous inscrire pour la notification des collectes complètes.  Le seuil que vous utilisez n'est pas important, car vous attendez l'achèvement d'une collecte plutôt que l'approche d'une collecte.  Vous pouvez ensuite appeler la méthode <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=fullName>, qui se bloque jusqu'à ce qu'une collecte complète soit terminée.  Vous pouvez créer un thread qui appelle la méthode dans une boucle et effectue toutes les analyses nécessaires chaque fois que la méthode est retournée.  
  
 Sinon, vous pouvez appeler la méthode <xref:System.GC.CollectionCount%2A?displayProperty=fullName> périodiquement pour voir si le nombre de collectes de génération 2 a augmenté.  En fonction de la fréquence d'interrogation, cette technique peut ne pas fournir une indication exacte de l'occurrence d'une collecte complète.  
  
#### API d'hébergement  
 Si vous utilisez l'API d'hébergement non managée, votre hôte doit passer une implémentation de l'interface [IHostGCManager](../../../ocs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) au CLR.  Le CLR appelle la méthode [IHostGCManager::SuspensionEnding](../Topic/IHostGCManager::SuspensionEnding%20Method.md) lorsqu'il reprend l'exécution des threads suspendus pendant une collecte.  Le CLR passe la génération de la collecte terminée comme un paramètre de la méthode, donc l'hôte peut déterminer si la collecte était complète ou partielle.  Votre implémentation de la méthode [IHostGCManager::SuspensionEnding](../Topic/IHostGCManager::SuspensionEnding%20Method.md) peut lancer une requête de la mémoire ayant survécu, afin de vérifier que les nombres sont extraits dès qu'ils sont mis à jour.  
  
## Voir aussi  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=fullName>   
 [ICLRAppDomainResourceMonitor, interface](../../../ocs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)   
 [\<appDomainResourceMonitoring\>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)   
 [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md)