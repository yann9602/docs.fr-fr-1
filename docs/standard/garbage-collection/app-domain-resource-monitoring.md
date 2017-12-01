---
title: Analyse de ressource de domaine d'application
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring managed memory use by application domain
- application domains, memory use
- memory use, monitoring
- application domains, resource monitoring
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62a514f94857044af5020d36a1cfd6ce06741ac7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="application-domain-resource-monitoring"></a>Analyse de ressource de domaine d'application
Ressource de domaine d’application d’analyse (ARM) permet aux hôtes surveiller l’utilisation de l’UC et de la mémoire par domaine d’application. Cela est utile pour les ordinateurs hôtes telles que ASP.NET qui utilisent de nombreux domaines d’application dans un processus à long terme. L’hôte peut décharger le domaine d’application d’une application qui affecte les performances de l’ensemble du processus, mais uniquement s’il peut identifier l’application problématique. ARM fournit des informations qui peuvent être utilisées pour aider à prendre ces décisions.  
  
 Par exemple, un service d’hébergement peut avoir de nombreuses applications s’exécutant sur un serveur ASP.NET. Si une application dans le processus commence à consommer trop de mémoire ou trop de temps processeur, le service d’hébergement peut utiliser ARM pour identifier le domaine d’application qui provoque le problème.  
  
 ARM est suffisamment léger à utiliser dans des applications actives. Vous pouvez accéder aux informations à l’aide du suivi d’événements pour Windows (ETW) ou directement via l’API managé ou natif.  
  
## <a name="enabling-resource-monitoring"></a>Activer l’analyse des ressources  
 ARM peut être activé de quatre façons : en fournissant un fichier de configuration lorsque le common language runtime (CLR) est démarré, en utilisant une fonction non managée API d’hébergement, à l’aide de code managé ou en écoutant les événements ETW ARM.  
  
 Dès que ARM est activé, il commence à collecter des données sur tous les domaines d’application dans le processus. Si un domaine d’application a été créé avant l’activation de ARM, données cumulatives démarrent ARM est activé, et non lorsque le domaine d’application a été créé. Une fois qu’il est activé, ARM ne peut pas être désactivée.  
  
-   Vous pouvez activer ARM au démarrage du CLR en ajoutant le [ \<appDomainResourceMonitoring >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) élément pour le paramètre et le fichier de configuration de la `enabled` attribut `true`. La valeur `false` (la valeur par défaut) signifie uniquement que ARM n’est pas activé au démarrage ; vous pouvez l’activer ultérieurement en utilisant l’une des autres méthodes d’activation.  
  
-   L’hôte peut activer ARM en demandant le [ICLRAppDomainResourceMonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface d’hébergement. Une fois que cette interface est obtenue avec succès, ARM est activé.  
  
-   Le code managé peut activer ARM en définissant la méthode statique (`Shared` en Visual Basic) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> propriété `true`. Dès que la propriété est définie, ARM est activé.  
  
-   Vous pouvez activer ARM après le démarrage en écoutant les événements ETW. ARM est activé et commence à déclencher des événements pour tous les domaines d’application lorsque vous activez le fournisseur public `Microsoft-Windows-DotNETRuntime` à l’aide de la `AppDomainResourceManagementKeyword` (mot clé). Pour mettre en corrélation des données avec les domaines d’application et les threads, vous devez également activer le `Microsoft-Windows-DotNETRuntimeRundown` fournisseur avec le `ThreadingKeyword` (mot clé).  
  
## <a name="using-arm"></a>À l’aide de ARM  
 ARM fournit le temps processeur total utilisé par un domaine d’application et les trois types d’informations sur l’utilisation de la mémoire.  
  
-   **Nombre total de temps processeur pour un domaine d’application, en secondes**: elle est calculée en additionnant les temps de thread signalés par le système d’exploitation pour tous les threads passé à temps à s’exécuter dans le domaine d’application pendant sa durée de vie. Bloqué ou des threads en veille n’utilisent pas de temps processeur. Lorsqu’un thread appelle en code natif, le temps que le thread passe en code natif est inclus dans le nombre pour le domaine d’application où l’appel a été effectué.  
  
    -   API managée : <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> propriété.  
  
    -   API d’hébergement : [ICLRAppDomainResourceMonitor::GetCurrentCpuTime](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) (méthode).  
  
    -   Événements ETW : `ThreadCreated`, `ThreadAppDomainEnter`, et `ThreadTerminated` événements. Pour plus d’informations sur les fournisseurs et les mots clés, consultez « Événements de contrôle des ressources AppDomain » dans [événements ETW du CLR](../../../docs/framework/performance/clr-etw-events.md).  
  
-   **Nombre total de managé allocations effectuées par un domaine d’application pendant sa durée de vie, en octets**: nombre Total d’allocations ne reflète pas toujours l’utilisation de la mémoire par un domaine d’application, car les objets alloués peuvent être éphémères. Toutefois, si une application alloue et libère de grandes quantités d’objets, le coût des allocations peut être significatif.  
  
    -   API managée : <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> propriété.  
  
    -   API d’hébergement : [ICLRAppDomainResourceMonitor::GetCurrentAllocated](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) (méthode).  
  
    -   Événements ETW : `AppDomainMemAllocated` événement, `Allocated` champ.  
  
-   **Mémoire managée, en octets, qui est référencé par un domaine d’application et qui ont survécu à la collection de blocage la plus récente complet**: ce nombre est exact uniquement après un complet, collection de blocage. (Ce comportement diffère des collections simultanées, qui se produisent en arrière-plan et ne bloquent pas l’application.) Par exemple, le <xref:System.GC.Collect?displayProperty=nameWithType> surcharge de méthode provoque un collection de blocage complet.  
  
    -   API managée : <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> propriété.  
  
    -   API d’hébergement : [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) méthode `pAppDomainBytesSurvived` paramètre.  
  
    -   Événements ETW : `AppDomainMemSurvived` événement, `Survived` champ.  
  
-   **Nombre total de mémoire managée, en octets, qui est référencé par le processus et qui ont survécu à la collection de blocage la plus récente complet**: la mémoire restante pour les domaines d’application individuels peut être comparée à ce nombre.  
  
    -   API managée : <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> propriété.  
  
    -   API d’hébergement : [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) méthode `pTotalBytesSurvived` paramètre.  
  
    -   Événements ETW : `AppDomainMemSurvived` événement, `ProcessSurvived` champ.  
  
### <a name="determining-when-a-full-blocking-collection-occurs"></a>Pour déterminer quand un complet, Collection de blocage se produit  
 Pour déterminer quand la mémoire ayant survécu est précis, vous devez savoir quand une collecte bloquante complète s’est produite. La méthode pour y parvenir dépend de l’API vous permettent d’examiner les statistiques ARM.  
  
#### <a name="managed-api"></a>API managée  
 Si vous utilisez les propriétés de la <xref:System.AppDomain> (classe), vous pouvez utiliser la <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> méthode s’inscrire pour la notification des collectes complètes. Le seuil que vous utilisez n’est pas important, car vous attendez l’achèvement d’une collection, plutôt que l’approche d’une collection. Vous pouvez ensuite appeler la <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> (méthode), qui se bloque jusqu'à ce qu’une collection complète est terminée. Vous pouvez créer un thread qui appelle la méthode dans une boucle et d’effectue toutes les analyses nécessaires chaque fois que la méthode retourne.  
  
 Vous pouvez également appeler le <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> méthode régulièrement pour voir si le nombre de collections de génération 2 a augmenté. Selon la fréquence d’interrogation, cette technique peut ne pas fournit comme exactes une indication de l’occurrence d’une collection complète.  
  
#### <a name="hosting-api"></a>API d’hébergement  
 Si vous utilisez l’API d’hébergement non managée, votre hôte doit passer le CLR une implémentation de la [IHostGCManager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) interface. Le CLR appelle la [IHostGCManager::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) méthode lorsqu’il reprend l’exécution de threads qui ont été interrompues pendant l’exécution d’une collection. Le CLR passe la génération de la collection terminée en tant que paramètre de la méthode, afin que l’hôte puisse déterminer si la collection a été complète ou partielle. Votre implémentation de la [IHostGCManager::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) méthode peut interroger pour la mémoire restante, pour vous assurer que les nombres sont extraits dès qu’ils sont mis à jour.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [ICLRAppDomainResourceMonitor (Interface)](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [\<appDomainResourceMonitoring>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [Événements ETW du CLR](../../../docs/framework/performance/clr-etw-events.md)
