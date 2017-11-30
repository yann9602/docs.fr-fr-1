---
title: "Collections forcées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 92918e347b10dfcf3a0d6e2c08cec8c7a6963f5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="induced-collections"></a>Collections forcées
Dans la plupart des cas, le Garbage collector peut déterminer le meilleur moment pour exécuter une collection. En outre, vous devez lui permettre de s’exécuter de façon indépendante. Dans de rares cas, une collection forcée peut toutefois améliorer les performances de votre application. Dans ce cas, vous pouvez induire le garbage collection à l’aide de la <xref:System.GC.Collect%2A?displayProperty=nameWithType> méthode pour forcer une opération garbage collection.  
  
 Utilisez la <xref:System.GC.Collect%2A?displayProperty=nameWithType> méthode lorsqu’il existe une réduction considérable de quantité de mémoire utilisée sur un point spécifique dans le code de votre application. Par exemple, si votre application utilise une boîte de dialogue complexe comportant plusieurs contrôles, l’appel <xref:System.GC.Collect%2A> lorsque la boîte de dialogue est fermée peut améliorer les performances en libérant immédiatement de la mémoire utilisée par la boîte de dialogue. Vérifiez que votre application n’induit pas trop fréquemment le garbage collection. En effet, les performances risquent d’être affectées si le Garbage collector tente de récupérer des objets à des moments inopportuns. Vous pouvez fournir un <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> valeur d’énumération pour la <xref:System.GC.Collect%2A> méthode pour collecter uniquement lorsque la collection est productive, comme indiqué dans la section suivante.  
  
## <a name="gc-collection-mode"></a>Mode de collection GC  
 Vous pouvez utiliser l’une de le <xref:System.GC.Collect%2A?displayProperty=nameWithType> surcharges de méthode qui inclut un <xref:System.GCCollectionMode> valeur pour spécifier le comportement d’une collection forcée comme suit.  
  
|Valeur `GCCollectionMode`|Description|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Utilise le paramètre de valeur par défaut garbage collection pour la version en cours d’exécution de .NET.|  
|<xref:System.GCCollectionMode.Forced>|Force l’exécution immédiate du garbage collection. Cela équivaut à appeler le <xref:System.GC.Collect?displayProperty=nameWithType> de surcharge. Il en résulte une collection de blocage complète de toutes les générations.<br /><br /> Vous pouvez également compacter le tas d’objets volumineux en définissant le <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> propriété <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> avant de forcer une immédiate garbage collection de blocage.|  
|<xref:System.GCCollectionMode.Optimized>|Permet au Garbage collector de déterminer si le moment est opportun pour récupérer des objets.<br /><br /> Le Garbage collector peut déterminer qu’une collection n’est pas assez productive pour être effectuée. Dans ce cas, aucun objet n’est récupéré.|  
  
## <a name="background-or-blocking-collections"></a>Collections d’arrière-plan ou de blocage  
 Vous pouvez appeler la <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> la surcharge de méthode pour spécifier si une collection INDUITE bloque ou non. Le type de collection effectuée dépend d’une combinaison de la méthode `mode` et `blocking` paramètres. `mode`est un membre de la <xref:System.GCCollectionMode> énumération, et `blocking` est un <xref:System.Boolean> valeur. Le tableau suivant résume l’interaction de le `mode` et `blocking` arguments.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> ou <xref:System.GCCollectionMode.Default>|Une collection de blocage est exécutée dès que possible. Si une collection d’arrière-plan est en cours d’exécution et la génération est 0 ou 1, le <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> méthode déclenche une collection de blocage immédiatement et retourne la fin de la collection. Si une collection d’arrière-plan est en cours d’exécution et le `generation` paramètre est 2, la méthode attend la collection d’arrière-plan est terminée, déclenche une collection de génération 2 blocage et renvoie.|Une collection est exécutée dès que possible. Le <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> méthode demande une collection d’arrière-plan, mais cela n’est pas garanti ; selon les circonstances, une collection de blocage peut toujours être effectuée. Si une collection d’arrière-plan est déjà en cours, la méthode retourne immédiatement une valeur.|  
|<xref:System.GCCollectionMode.Optimized>|Une collection de blocage peut être effectuée, selon l’état du garbage collector et `generation` paramètre. Le Garbage collector tente de fournir des performances optimales.|Une collection de blocage peut être effectuée, en fonction de l’état du Garbage collector. Le <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> méthode demande une collection d’arrière-plan, mais cela n’est pas garanti ; selon les circonstances, une collection de blocage peut toujours être effectuée. Le Garbage collector tente de fournir des performances optimales. Si une collection d’arrière-plan est déjà en cours, la méthode retourne immédiatement une valeur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Modes de latence](../../../docs/standard/garbage-collection/latency.md)  
 [Nettoyage de la mémoire](../../../docs/standard/garbage-collection/index.md)
