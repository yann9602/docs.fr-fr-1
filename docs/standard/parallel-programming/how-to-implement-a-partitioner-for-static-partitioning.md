---
title: "How to: Implement a Partitioner for Static Partitioning | Microsoft Docs"
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
  - "tasks, how to create a static partitioner"
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# How to: Implement a Partitioner for Static Partitioning
L'exemple suivant affiche une façon d'implémenter un partitionneur personnalisé simple pour PLINQ qui exécute le partitionnement statique.  Étant donné que le partitionneur ne prend pas en charge de partitions dynamiques, il n'est pas consommable à partir de <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName>.  Ce partitionneur particulier peut fournir une accélération sur le partitionneur de plages par défaut pour les sources de données pour lesquelles chaque élément requiert une quantité croissante de temps de traitement.  
  
## Exemple  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Les partitions dans cet exemple sont basées sur l'hypothèse d'une augmentation linéaire du temps de traitement pour chaque élément.  Dans le monde réel, il peut être difficile de prédire des temps de traitement de cette façon.  Si vous utilisez un partitionneur statique avec une source de données spécifique, vous pouvez optimiser la formule de partitionnement pour la source, ajouter la logique d'équilibrage de charge ou utiliser une approche de partitionnement par segments comme cela est indiqué dans [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## Voir aussi  
 [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)