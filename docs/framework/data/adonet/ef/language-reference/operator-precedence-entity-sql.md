---
title: "Priorit&#233; des op&#233;rateurs (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Priorit&#233; des op&#233;rateurs (Entity SQL)
Lorsqu'une requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] comporte plusieurs opérateurs, la priorité de ces derniers détermine l'ordre d'exécution des opérations.  Cet ordre peut affecter considérablement le résultat de la requête.  
  
 L'ordre de priorité des opérateurs est indiqué dans le tableau suivant.  Un opérateur avec un haut niveau de priorité est évalué avant un opérateur avec un faible niveau de priorité.  
  
|Niveau|Type d'opération|Opérateur|  
|------------|----------------------|---------------|  
|1|Principale|`. , [] ()`|  
|2|Unaire|`! not`|  
|3|Multiplication|`* / %`|  
|4|Addition|`+ -`|  
|5|Classement|`< > <= >=`|  
|6|Égalité|`= != <>`|  
|7|AND conditionnel|`and &&`|  
|8|OR conditionnel|`or &#124;&#124;`|  
  
 Lorsque deux opérateurs dans une expression ont le même niveau de priorité, ils sont évalués de gauche à droite, en fonction de leur position dans la requête.  Par exemple,  `x+y-z`  est évalué comme étant  `(x+y)-z`.  
  
 Vous pouvez utiliser des parenthèses pour modifier la priorité habituelle des opérateurs dans une requête.  Tout ce qui se trouve entre parenthèses est évalué en premier pour produire un seul résultat, qui est ensuite utilisé par un opérateur en dehors des parenthèses.  Par exemple, `x+y*z` multiplie `y` par `z` puis ajoute `x`, mais `(x+y)*z` ajoute `x` à `y` puis multiplie le résultat par `z`.  
  
## Voir aussi  
 [Vue d'ensemble d'Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)