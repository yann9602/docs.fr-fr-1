---
title: "S&#233;curit&#233; des threads dans les expressions r&#233;guli&#232;res | Microsoft Docs"
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
  - ".NET Framework (expressions régulières), threads"
  - "analyser du texte avec des expressions régulières, threads"
  - "mise en correspondance de modèles avec des expressions régulières, threads"
  - "expressions régulières, threads"
  - "rechercher avec des expressions régulières, threads"
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# S&#233;curit&#233; des threads dans les expressions r&#233;guli&#232;res
La classe <xref:System.Text.RegularExpressions.Regex> elle\-même est thread\-safe et immuable \(en lecture seule\).  Cela signifie que les objets **Regex** peuvent être créés sur n'importe quel thread et partagé par plusieurs threads ; les méthodes de mise en correspondance peuvent être appelées à partir de n'importe quel thread et ne jamais modifier aucun état global.  
  
 Cependant, les objets résultats \(**Match** et **MatchCollection**\) retournés par **Regex** doivent être utilisés sur un seul thread.  Bien que bon nombre de ces objets soient logiquement immuables, leurs implémentations risquent de retarder le calcul de certains résultats pour améliorer les performances ; par conséquent, les appelants sont obligés d'en sérialiser l'accès.  
  
 Si le besoin se fait sentir de partager les objets résultats **Regex** sur plusieurs threads, ces objets peuvent être convertis en instances thread\-safe en appelant leurs méthodes synchronisées.  À l'exception des énumérateurs, toutes les classes d'expressions régulières sont thread\-safe ou peuvent être converties en objets thread\-safe par une méthode synchronisée.  
  
 Les énumérateurs sont la seule exception.  Une application doit sérialiser les appels destinés aux énumérateurs de collection.  La règle est la suivante : si une collection peut être énumérée simultanément sur plusieurs threads, vous devez synchroniser les méthodes d'énumération sur l'objet racine de la collection à laquelle accède l'énumérateur.  
  
## Voir aussi  
 [Expressions régulières du .NET Framework](../../../docs/standard/base-types/regular-expressions.md)