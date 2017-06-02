---
title: "How to: Measure PLINQ Query Performance | Microsoft Docs"
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
  - "PLINQ queries, how to measure performance"
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Measure PLINQ Query Performance
Cet exemple montre comment utiliser la classe <xref:System.Diagnostics.Stopwatch> pour mesurer la durée d'exécution d'une requête PLINQ.  
  
## Exemple  
 Cet exemple utilise une boucle `foreach` vide \(`For Each` en Visual Basic\) pour mesurer la durée d'exécution de requête.  Dans du code réel, la boucle contient en général des étapes de traitement supplémentaires qui viennent s'ajouter à la durée totale d'exécution de la requête.  Remarquez que le chronomètre est lancé juste avant la boucle, car c'est à ce moment là que l'exécution de la requête commence.  Si vous avez besoin de mesures plus affinées, vous pouvez utiliser la propriété `ElapsedTicks` au lieu de `ElapsedMilliseconds`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Connaître la durée d'exécution totale est utile lorsque vous expérimentez avec les implémentations de requête, mais elle ne révèle pas tout.  Pour en savoir plus sur l'interaction des threads de requête les uns avec les autres et avec d'autres processus en cours d'exécution, utilisez le visualiseur concurrentiel.  Pour plus d'informations, consultez [Visualiseur concurrence](../Topic/Concurrency%20Visualizer.md).  
  
## Voir aussi  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)