---
title: Modes de latence
description: Modes de latence
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/18/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 810bd8be-5a48-42c6-b080-3afdb31fc61b
translationtype: Human Translation
ms.sourcegitcommit: de0dab146fc811e895dc32f98f877db5e757f82b
ms.openlocfilehash: e063482aaa1fad01f8e0cd9e8552c87a0b247571

---

# <a name="latency-modes"></a>Modes de latence

Pour récupérer des objets, le garbage collector doit arrêter tous les threads en cours d'exécution dans une application. Dans certaines situations, par exemple, quand une application récupère des données ou affiche du contenu, un garbage collection complet peut se produire à un moment critique et nuire aux performances. Vous pouvez ajuster le niveau d’intrusion du Garbage collector en définissant la propriété [GCSettings.LatencyMode](xref:System.Runtime.GCSettings.LatencyMode) sur l’une des valeurs [System.Runtime.GCLatencyMode](xref:System.Runtime.GCLatencyMode). 

La latence fait référence à la durée pendant laquelle le garbage collector effectue une intrusion dans votre application. Pendant les périodes de faible latence, le garbage collector est moins intrusif quant à la récupération des objets. L’énumération [System.Runtime.GCLatencyMode](xref:System.Runtime.GCLatencyMode) fournit deux paramètres de latence faible :

* [LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) supprime les collections de génération 2 et effectue uniquement des collections de génération 0 et 1. Elle ne peut être utilisée que pour de courtes durées. Sur des périodes plus longues, si le système connaît une sollicitation de mémoire importante, le garbage collector déclenchera une collection, qui pourra brièvement suspendre l'application et interrompre une opération critique. Ce paramètre est disponible uniquement pour le garbage collection des stations de travail. 

* [SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) supprime les collections de génération 2 de premier plan et effectue uniquement des collections de génération 0 et 1, ainsi que des collections de génération 2 d’arrière-plan. Il peut être utilisé pour de longues périodes et est disponible à la fois pour le garbage collection des stations de travail et des serveurs. Ce paramètre ne peut pas être utilisé si le [garbage collection simultané](https://msdn.microsoft.com/library/yhwwzef8.aspx) est désactivé.

Pendant les périodes de faible latence, les collections de génération 2 sont empêchées, sauf dans les cas suivants :

* Le système reçoit une notification de mémoire insuffisante du système d'exploitation.

* Le code de votre application déclenche une collection en appelant la méthode [GC.Collect](xref:System.GC.Collect(System.Int32)) et en spécifiant la valeur 2 pour le paramètre de génération.

Le tableau suivant répertorie les scénarios d’application pour l’utilisation des valeurs [GCLatencyMode](xref:System.Runtime.GCLatencyMode).

Mode de latence | Scénarios d'application
------------ | --------------------- 
[Batch](xref:System.Runtime.GCLatencyMode.Batch) | Pour les applications qui n'ont aucune interface utilisateur ou les opérations côté serveur. Il s’agit du mode par défaut quand le [garbage collection simultané](https://msdn.microsoft.com/library/yhwwzef8.aspx) est désactivé.
[Interactive](xref:System.Runtime.GCLatencyMode.Interactive) | Pour la plupart des applications qui ont une interface utilisateur. Pour les applications qui n'ont aucune interface utilisateur ou les opérations côté serveur. Il s’agit du mode par défaut quand le [garbage collection simultané](https://msdn.microsoft.com/library/yhwwzef8.aspx) est activé.
[LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) | Pour les applications qui ont des opérations de courte durée pour lesquelles le temps est important, et durant lesquelles les interruptions du garbage collector pourraient provoquer des perturbations. Par exemple, les applications qui ont des fonctions de rendu d'animation ou d'acquisition de données.
[SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) | Pour les applications qui ont des opérations pour lesquelles le temps est important, pendant une durée définie mais potentiellement longue durant laquelle les interruptions du garbage collector pourraient provoquer des perturbations. Par exemple, les applications nécessitant des temps de réponse rapides en raison du changement des données de marché pendant les heures de négociation.   Ce mode augmente davantage la taille du tas managé que les autres modes. Parce qu'il ne compacte pas le tas managé, une fragmentation plus importante est possible. Assurez-vous que suffisamment de mémoire est disponible.
 
## <a name="guidelines-for-using-low-latency"></a>Instructions sur l'utilisation de la faible latence

Quand vous utilisez le mode [LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency), respectez les consignes suivantes :

* Choisissez une période aussi courte que possible pour la faible latence.

* Évitez d'allouer de grandes quantités de mémoire pendant les périodes de faible latence. Vous pouvez recevoir des notifications de mémoire insuffisante, car le garbage collection récupère moins d'objets. 

* En mode de latence faible, réduisez le nombre d'allocations, notamment les allocations sur le tas des objets volumineux et les objets épinglés. 

* N'oubliez pas les threads qui peuvent être à l'origine d'allocations. Étant donné que le paramètre de propriété [LatencyMode](xref:System.Runtime.GCSettings.LatencyMode) s’étend à tout le processus, vous pouvez générer un [OutOfMemoryException](xref:System.OutOfMemoryException) sur n’importe quel thread à l’origine d’une allocation. 

* Vous pouvez forcer les collections de génération 2 pendant une période de latence basse en appelant la méthode [GC.Collect(Int32, GCCollectionMode)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode)).

## <a name="see-also"></a>Voir aussi

[System.GC](xref:System.GC)

[Collections forcées](induced.md)

[Garbage collection dans le .NET](index.md)



<!--HONumber=Nov16_HO1-->


