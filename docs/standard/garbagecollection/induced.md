---
title: "Collections forcées"
description: "Collections forcées"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3e09b9dd-a800-4e56-b468-619f910ae22e
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: a10822518f0687dc7bbb06dd0fb77f6d9a3196fb

---

# <a name="induced-collections"></a>Collections forcées

Dans la plupart des cas, le Garbage collector peut déterminer le meilleur moment pour exécuter une collection. En outre, vous devez lui permettre de s’exécuter de façon indépendante. Dans de rares cas, une collection forcée peut toutefois améliorer les performances de votre application. Vous pouvez alors induire le garbage collection à l’aide de la méthode [GC.Collect](xref:System.GC.Collect) pour forcer un garbage collection. 

Utilisez la méthode [Collect](xref:System.GC.Collect) quand la quantité de mémoire utilisée à un point spécifique dans le code de votre application diminue considérablement. Par exemple, si votre application utilise une boîte de dialogue complexe comportant plusieurs contrôles, l’appel de [Collect](xref:System.GC.Collect) quand la boîte de dialogue est fermée peut améliorer les performances en libérant immédiatement la mémoire utilisée par la boîte de dialogue. Vérifiez que votre application n’induit pas trop fréquemment le garbage collection. En effet, les performances risquent d’être affectées si le Garbage collector tente de récupérer des objets à des moments inopportuns. Vous pouvez fournir une valeur d’énumération [GCCollectionMode.Optimized](xref:System.GCCollectionMode.Optimized) à la méthode [Collect](xref:System.GC.Collect) pour effectuer une collection uniquement lorsqu’elle est productive, comme décrit dans la section suivante.

## <a name="gc-collection-mode"></a>Mode de collection GC

Vous pouvez utiliser l’une des surcharges de méthode [GC.Collect](xref:System.GC.Collect)qui inclut une valeur [GCCollectionMode](xref:System.GCCollectionMode) pour spécifier le comportement d’une collection forcée, comme suit.

Valeur de GCCollectionMode | Description
---------------------- | ----------- 
[Default](xref:System.GCCollectionMode.Default) | Utilise le paramètre de garbage collection par défaut pour la version en cours d’exécution du .NET Framework.
[Forced](xref:System.GCCollectionMode.Forced) | Force l’exécution immédiate du garbage collection. Cela équivaut à appeler la surcharge [GC.Collect()](xref:System.GC.Collect). Il en résulte une collection de blocage complète de toutes les générations. Vous pouvez également compacter le tas des objets volumineux en définissant la propriété [GCSettings.LargeObjectHeapCompactionMode](xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode) avec la valeur [GCLargeObjectHeapCompactionMode.CompactOnce](xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce) avant de forcer un garbage collection de blocage total immédiat. 
[Optimized](xref:System.GCCollectionMode.Optimized) | Permet au Garbage collector de déterminer si le moment est opportun pour récupérer des objets. Le Garbage collector peut déterminer qu’une collection n’est pas assez productive pour être effectuée. Dans ce cas, aucun objet n’est récupéré.
 
## <a name="background-or-blocking-collections"></a>Collections d’arrière-plan ou de blocage

Vous pouvez appeler la surcharge de méthode [GC.Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) pour spécifier si une collection induite bloque ou non. Le type de collection effectué dépend d’une combinaison des paramètres *mode* et *blocking* de la méthode. *mode* est un membre de l’énumération [GCCollectionMode](xref:System.GCCollectionMode), et *blocking* est une valeur [Boolean](xref:System.Boolean). Le tableau suivant résume l’interaction des arguments mode et blocking. 

*mode* | *blocking* = true | *blocking* = false
------ | ----------------- | ------------------
[Forced](xref:System.GCCollectionMode.Forced) ou [Default](xref:System.GCCollectionMode.Default) | Une collection de blocage est exécutée dès que possible. Si une collection d’arrière-plan est en cours et que la génération a la valeur 0 ou 1, la méthode [Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) déclenche immédiatement une collection de blocage et retourne une valeur quand la collection est terminée. Si une collection d’arrière-plan est en cours et que le paramètre generation a la valeur 2, la méthode attend la fin de la collection d’arrière-plan, déclenche une collection de blocage de génération 2, puis retourne une valeur. | Une collection est exécutée dès que possible. La méthode [Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) demande une collection d’arrière-plan, mais cela n’est pas garanti ; selon les cas, une collection de blocage peut toujours être exécutée. Si une collection d’arrière-plan est déjà en cours, la méthode retourne immédiatement une valeur. 
[Optimized](xref:System.GCCollectionMode.Optimized) | Une collection de blocage peut être effectuée, en fonction de l’état du Garbage collector et du paramètre generation. Le Garbage collector tente de fournir des performances optimales. | Une collection de blocage peut être effectuée, en fonction de l’état du Garbage collector. La méthode [Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) demande une collection d’arrière-plan, mais cela n’est pas garanti ; selon les cas, une collection de blocage peut toujours être exécutée. Le Garbage collector tente de fournir des performances optimales. Si une collection d’arrière-plan est déjà en cours, la méthode retourne immédiatement une valeur. 
 
## <a name="see-also"></a>Voir aussi

[Modes de latence](latency.md)

[Garbage collection dans le .NET](index.md)



<!--HONumber=Nov16_HO1-->


