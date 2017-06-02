---
title: "Collections forc&#233;es | Microsoft Docs"
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
  - "garbage collection, forcé"
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# Collections forc&#233;es
Dans la plupart des cas, le garbage collector peut déterminer le meilleur moment d'exécution d'une collection. En outre, vous devez lui permettre de s'exécuter de façon indépendante.  Dans de rares cas, une collection forcée peut toutefois améliorer les performances de votre application.  Dans ces cas, vous pouvez induire le garbage collection à l'aide de la méthode <xref:System.GC.Collect%2A?displayProperty=fullName> pour forcer un garbage collection.  
  
 Utilisez la méthode <xref:System.GC.Collect%2A?displayProperty=fullName> lorsque la quantité de mémoire utilisée à un point spécifique dans le code de votre application diminue considérablement.  Par exemple, si votre application utilise une boîte de dialogue complexe comportant plusieurs contrôles, l'appel de <xref:System.GC.Collect%2A> lorsque la boîte de dialogue est fermée peut améliorer les performances en libérant immédiatement de la mémoire utilisée par la boîte de dialogue.  Assurez\-vous que votre application n'induit pas trop fréquemment le garbage collection. En effet, les performances risquent d'être affectées si le garbage collector essaie de récupérer des objets aux moments inopportuns.  Vous pouvez fournir une valeur d'énumération <xref:System.GCCollectionMode?displayProperty=fullName> à la méthode <xref:System.GC.Collect%2A> pour collecter uniquement lorsque la collection est productive, comme décrit dans la section suivante.  
  
## Mode de collection GC  
 Vous pouvez utiliser l'une des surcharges de méthode <xref:System.GC.Collect%2A?displayProperty=fullName> qui incluent une valeur <xref:System.GCCollectionMode> pour spécifier le comportement d'une collection forcée, comme suit.  
  
|Valeur de `GCCollectionMode`|Description|  
|----------------------------------|-----------------|  
|<xref:System.GCCollectionMode>|Utilise le paramètre de garbage collection par défaut pour la version actuelle du .NET Framework.|  
|<xref:System.GCCollectionMode>|Force l'exécution immédiate du garbage collection.  Cela équivaut à appeler la surcharge <xref:System.GC.Collect?displayProperty=fullName>.  Il en résulte une collection bloquante complète de toutes les générations.<br /><br /> Vous pouvez également compacter le tas des objets volumineux en définissant la propriété <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=fullName> avec la valeur <xref:System.Runtime.GCLargeObjectHeapCompactionMode?displayProperty=fullName> avant de forcer un garbage collection de blocage total immédiat.|  
|<xref:System.GCCollectionMode>|Permet au garbage collector de déterminer s'il vaut mieux récupérer des objets maintenant ou plus tard.<br /><br /> Par exemple, le garbage collector peut déterminer qu'une collection n'est pas assez productive pour être effectuée. Dans ce cas, aucun objet n'est récupéré.|  
  
## Collections d'arrière\-plan ou bloquantes  
 Vous pouvez appeler la surcharge de méthode <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=fullName> pour spécifier si une collection induite bloque ou non.  Le type de collection effectué dépend d'une combinaison des paramètres `mode` et `blocking` de la méthode.  `mode` est un membre de l'énumération <xref:System.GCCollectionMode>, et `blocking` est une valeur <xref:System.Boolean>.  Le tableau suivant résume l'interaction des arguments `mode` et `blocking`.  
  
|`mode`|`blocking` \= `true`|`blocking` \= `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode> ou <xref:System.GCCollectionMode>|Une collecte bloquante est exécutée dès que possible.  Si une collection d'arrière\-plan est en cours et que la génération a la valeur 0 ou 1, la méthode <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> déclenche immédiatement une collection bloquante et retourne à la fin de la collection.  Si une collection d'arrière\-plan est en cours et que le paramètre `generation` a la valeur 2, la méthode attend la fin de la collection d'arrière\-plan, déclenche une collection bloquante de génération 2 et effectue un retour.|Une collecte est exécutée dès que possible.  La méthode <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> demande une collection d'arrière\-plan, mais cela n'est pas garanti ; selon les cas, une collection bloquante peut toujours être exécutée.  Si une collection d'arrière\-plan est déjà en cours, la méthode effectue un retour immédiat.|  
|<xref:System.GCCollectionMode>|Une collecte bloquante peut être exécutée, selon l'état du récupérateur de mémoire et du paramètre `generation`.  Le garbage collector essaie de fournir des performances optimales.|Une collecte peut être exécutée, selon l'état du récupérateur de mémoire.  La méthode <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> demande une collection d'arrière\-plan, mais cela n'est pas garanti ; selon les cas, une collection bloquante peut toujours être exécutée.  Le garbage collector essaie de fournir des performances optimales.  Si une collection d'arrière\-plan est déjà en cours, la méthode effectue un retour immédiat.|  
  
## Voir aussi  
 [Latency Modes](../../../docs/standard/garbage-collection/latency.md)   
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)