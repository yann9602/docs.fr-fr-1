---
title: "How to: Synchronize Concurrent Operations with a Barrier | Microsoft Docs"
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
  - "Barrier, how to use"
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Synchronize Concurrent Operations with a Barrier
L'exemple suivant indique comment synchroniser des tâches simultanées avec un <xref:System.Threading.Barrier>.  
  
## Exemple  
 L'objectif du programme suivant est de compter le nombre d'itérations \(ou phases\) nécessaires pour que deux threads trouvent leur moitié de solution sur la même phase à l'aide d'un algorithme aléatoire pour réorganiser l'ordre des mots.  Une fois que chaque thread a mélangé ses mots, l'opération post\-phase de cloisonnement compare les deux résultats pour voir si la phrase complète a été restituée avec les mots dans le bon ordre.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 Un <xref:System.Threading.Barrier> est un objet qui empêche des tâches individuelles dans une opération en parallèle de continuer jusqu'à ce que toutes les tâches atteignent le cloisonnement.  Cela est utile lorsqu'une opération en parallèle se produit par phases et que chaque phase requiert la synchronisation entre les tâches.  Dans cet exemple, l'opération se déroule en deux phases.  Lors de la première phase, chaque tâche remplit sa section de la mémoire tampon avec des données.  Une fois que chaque tâche a rempli sa section, elle signale au cloisonnement qu'elle est prête à continuer, puis attend.  Lorsque toutes les tâches ont prévenu le cloisonnement, elles sont débloquées et la deuxième phase démarre.  Le cloisonnement est nécessaire car la seconde phase requiert que chaque tâche ait accès à toutes les données déjà générées.  Sans le cloisonnement, les premières tâches à avoir terminé peuvent essayer de lire à partir de mémoires tampons qui n'ont pas encore été remplies par les tâches.  Vous pouvez synchroniser de cette manière n'importe quel nombre de phases.  
  
## Voir aussi  
 [Data Structures for Parallel Programming](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)