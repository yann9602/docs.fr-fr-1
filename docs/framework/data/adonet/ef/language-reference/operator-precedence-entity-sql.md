---
title: "Priorité des opérateurs (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 537c9ae7c92c6abcbe597970f2b0ec29e399bc62
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="operator-precedence-entity-sql"></a>Priorité des opérateurs (Entity SQL)
Lorsqu’un [!INCLUDE[esql](../../../../../../includes/esql-md.md)] requête comporte plusieurs opérateurs, la priorité des opérateurs détermine l’ordre dans lequel les opérations sont effectuées. Cet ordre peut affecter considérablement le résultat de la requête.  
  
 L'ordre de priorité des opérateurs est indiqué dans le tableau suivant. Un opérateur avec un haut niveau de priorité est évalué avant un opérateur avec un faible niveau de priorité.  
  
|Niveau|Type d'opération|Opérateur|  
|-----------|--------------------|--------------|  
|1|Principale|`. , [] ()`|  
|2|Unaire|`! not`|  
|3|Multiplication|`* / %`|  
|4|Addition|`+ -`|  
|5|Classement|`< > <= >=`|  
|6|Égalité|`= != <>`|  
|7|AND conditionnel|`and &&`|  
|8|OR conditionnel|`or &#124;&#124;`|  
  
 Lorsque deux opérateurs dans une expression ont le même niveau de priorité, ils sont évalués de gauche à droite, en fonction de leur position dans la requête. Par exemple, `x+y-z` est évalué comme étant `(x+y)-z`.  
  
 Vous pouvez utiliser des parenthèses pour modifier la priorité habituelle des opérateurs dans une requête. Tout ce qui se trouve entre parenthèses est évalué en premier pour produire un seul résultat, qui est ensuite utilisé par un opérateur en dehors des parenthèses. Par exemple, `x+y*z` multiplie `y` par `z` , puis ajoute `x`, mais `(x+y)*z` ajoute `x` à `y` , puis multiplie le résultat par `z`.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble d’Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
