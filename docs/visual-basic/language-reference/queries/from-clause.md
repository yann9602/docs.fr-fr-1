---
title: "From Clause (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.QueryFrom"
  - "vb.QueryFromIn"
  - "vb.QueryFromLet"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], From"
  - "From clause"
  - "From statement"
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# From Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie une ou plusieurs variables de portée et une collection pour requêtes.  
  
## Syntaxe  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`element`|Obligatoire.  *Variable de portée* utilisée pour itérer au sein des éléments de la collection.  Une variable de portée sert à se reporter à chaque membre de la `collection` alors que la requête itère au sein de cette `collection`.  Doit être un type énumérable.|  
|`type`|Facultatif.  Type de `element`.  Si aucun `type` n'est spécifié, le type d'`element` est déduit de `collection`.|  
|`collection`|Obligatoire.  Fait référence à la collection à interroger.  Doit être un type énumérable.|  
  
## Notes  
 La clause `From` permet d'identifier les données sources d'une requête et les variables utilisées pour faire référence à un élément de la collection de sources.  Ces variables sont appelées *variables de portée*.  La clause `From` est requise pour toute requête, sauf lorsque la clause `Aggregate` est utilisée pour identifier une requête qui ne renvoie que des résultats regroupés.  Pour plus d'informations, consultez [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Vous pouvez spécifier plusieurs clauses `From` dans une requête pour identifier plusieurs collections devant être jointes.  Lorsque vous spécifiez plusieurs collections, elles sont itérées indépendamment, mais vous pouvez les joindre les unes aux autres si elles sont liées.  Pour joindre des collections de manière implicite, utilisez la clause `Select` ; pour les joindre de manière explicite, utilisez la clause `Join` ou la clause `Group Join`.  Si vous le souhaitez, vous pouvez spécifier des variables de portée et des collections multiples dans une clause `From` unique, chaque variable de portée et chaque collection étant séparée de ses voisines par une virgule.  L'exemple de code qui suit montre les deux options de syntaxe pour la clause `From`.  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 La clause `From` définit la portée d'une requête semblable à la portée d'une boucle `For`.  Par conséquent, chaque variable de portée `element` de la requête doit recevoir un nom unique.  Comme vous pouvez spécifier plusieurs clauses `From` par requête, les clauses `From` suivantes peuvent se reporter à des variables de portée de la clause `From`, ou se reporter pour aligner des variables de portée d'une clause `From` précédente.  Par exemple, l'exemple suivant affiche une clause `From` imbriquée, où la collection dans la deuxième clause est basée sur une propriété de la variable de portée de la première clause.  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 Chaque clause `From` peut être suivie de toute combinaison de clauses de requête supplémentaires pour affiner la requête.  Vous pouvez affiner la requête des manières suivantes :  
  
-   Combinez plusieurs collections de manière implicite, en utilisant les clauses `From` et `Select`, ou de manière explicite, en utilisant les clauses `Join` ou `Group Join`.  
  
-   Utilisez la clause `Where` pour filtrer le résultat de la requête.  
  
-   Triez le résultat à l'aide de la clause `Order By`.  
  
-   Groupez les résultats similaires, en utilisant la clause `Group By`.  
  
-   Utilisez la clause `Aggregate` pour identifier les fonctions d'agrégation à évaluer pour le résultat de la requête toute entière.  
  
-   Utilisez la clause `Let` pour introduire une variable d'itération dont la valeur est déterminée par une expression au lieu d'une collection.  
  
-   Utilisez la clause `Distinct` pour ignorer les doublons dans les résultats de la requête.  
  
-   Identifiez des parties du résultat à retourner en utilisant les clauses `Skip`, `Take`, `Skip While` et `Take While`.  
  
## Exemple  
 L'expression de requête suivante utilise une clause `From` pour déclarer une variable de portée `cust` pour chaque objet `Customer` de la collection `customers`.  La clause `Where` utilise la variable de portée pour restreindre la sortie aux clients de la région spécifiée.  La boucle `For Each` affiche le nom de société pour chaque client dans le résultat de la requête.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## Voir aussi  
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [For Each...Next, instruction](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [For...Next, instruction](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Distinct Clause](../../../visual-basic/language-reference/queries/distinct-clause.md)   
 [Join Clause](../../../visual-basic/language-reference/queries/join-clause.md)   
 [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Let Clause](../../../visual-basic/language-reference/queries/let-clause.md)   
 [Skip Clause](../../../visual-basic/language-reference/queries/skip-clause.md)   
 [Take Clause](../../../visual-basic/language-reference/queries/take-clause.md)   
 [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md)