---
title: "Aggregate Clause (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryAggregateIn"
  - "vb.QueryAggregate"
  - "vb.QueryAggregateInto"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Aggregate clause"
  - "Aggregate statement"
  - "queries [Visual Basic], Aggregate"
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Aggregate Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Applique une ou plusieurs fonctions d'agrégation à une collection.  
  
## Syntaxe  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`element`|Obligatoire.  Variable utilisée pour itérer au sein des éléments de la collection.|  
|`type`|Facultatif.  Type de `element`.  Si aucun type n'est spécifié, le type d'`element` est déduit de `collection`.|  
|`collection`|Obligatoire.  Fait référence à la collection sur laquelle opérer.|  
|`clause`|Facultatif.  Une ou plusieurs clauses de requête, telles qu'une clause `Where`, pour affiner le résultat de la requête auquel appliquer la ou les clauses d'agrégation.|  
|`expressionList`|Obligatoire.  Une ou plusieurs expressions délimitées par des virgules qui identifient une fonction d'agrégation à appliquer à la collection.  Vous pouvez appliquer un alias à une fonction d'agrégation pour spécifier un nom de membre pour le résultat de la requête.  Si aucun alias n'est fourni, le nom de la fonction d'agrégation est utilisé.  Pour obtenir des exemples, consultez la section sur les fonctions d'agrégation plus loin dans cette rubrique.|  
  
## Notes  
 La clause `Aggregate` peut être utilisée pour inclure des fonctions d'agrégation dans vos requêtes.  Les fonctions d'agrégation effectuent des vérifications et des calculs sur un jeu de valeurs et retournent une valeur unique.  Vous pouvez accéder à la valeur calculée à l'aide d'un membre du type du résultat de la requête.  Les fonctions d'agrégation standard que vous pouvez utiliser sont les suivantes : `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`et `Sum`.  Ces fonctions sont connues des développeurs qui sont familiarisés avec les agrégats dans SQL.  Ils sont décrits dans la section suivante de cette rubrique.  
  
 Le résultat d'une fonction d'agrégation est inclus dans le résultat de la requête sous la forme d'un champ du type de résultat de requête.  Vous pouvez fournir un alias pour le résultat de la fonction d'agrégation pour spécifier le nom du membre du type de résultat de la requête qui maintiendra la valeur d'agrégation.  Si aucun alias n'est fourni, le nom de la fonction d'agrégation est utilisé.  
  
 La clause `Aggregate` peut commencer une requête ou être incluse comme clause supplémentaire dans une requête.  Si la clause `Aggregate` commence une requête, il en résulte une valeur unique qui est le résultat de la fonction d'agrégation spécifiée dans la clause `Into`.  Si plusieurs fonctions d'agrégation sont spécifiées dans la clause `Into`, la requête retourne un type unique avec une propriété séparée pour référencer le résultat de chaque fonction d'agrégation de la clause `Into`.  Si la clause `Aggregate` est incluse comme clause supplémentaire dans une requête, le type retourné dans la collection de requêtes aura une propriété distincte pour référencer le résultat de chaque fonction d'agrégation de la clause `Into`.  
  
## Fonctions d'agrégation  
 La liste suivante décrit les fonctions d'agrégation standard qui peuvent être utilisées avec la clause `Aggregate`.  
  
|||  
|-|-|  
|Fonction|Description|  
|`All`|Retourne la valeur `true` si tous les éléments de la collection satisfont une condition spécifiée ; sinon retourne la valeur `false`.  Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|Retourne la valeur `true` si un élément de la collection satisfait une condition spécifiée ; sinon retourne la valeur `false`.  Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|Calcule la moyenne de tous les éléments de la collection ou une expression fournie pour tous les éléments de la collection.  Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|Compte le nombre d'éléments de la collection.  Vous pouvez fournir une expression `Boolean` facultative pour compter uniquement le nombre d'éléments de la collection qui satisfont une condition.  Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|Fait référence aux résultats de la requête groupés suite à une clause `Group By` ou `Group Join`.  La fonction `Group` est valide uniquement dans la clause `Into` d'une clause `Group By` ou `Group Join`.  Pour plus d'informations et d'exemples, consultez [Group By, clause](../../../visual-basic/language-reference/queries/group-by-clause.md) et [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md).|  
|`LongCount`|Compte le nombre d'éléments de la collection.  Vous pouvez fournir une expression `Boolean` facultative pour compter uniquement le nombre d'éléments de la collection qui satisfont une condition.  Retourne le résultat sous la forme de `Long`.  Pour obtenir un exemple, consultez la fonction d'agrégation `Count`.|  
|`Max`|Calcule la valeur maximale de la collection ou une expression fournie pour tous ses éléments.  Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|Calcule la valeur minimale de la collection ou une expression fournie pour tous ses éléments.  Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|Calcule la somme de tous les éléments de la collection ou une expression fournie pour tous les éléments de la collection.  Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## Exemple  
 L'exemple de code suivant indique comment utiliser la clause `Aggregate` pour appliquer des fonctions d'agrégation à un résultat de requête.  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## Création de fonctions d'agrégation définies par l'utilisateur  
 Vous pouvez inclure vos propres fonctions d'agrégation personnalisées dans une expression de requête en ajoutant des méthodes d'extension au type <xref:System.Collections.Generic.IEnumerable%601>.  Votre méthode personnalisée peut ensuite effectuer un calcul ou une opération sur la collection énumérable qui a référencé votre fonction d'agrégation.  Pour plus d'informations sur les méthodes d'extension, consultez [méthodes d'extension.](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Par exemple, l'exemple de code suivant représente une fonction d'agrégation personnalisée qui calcule la valeur médiane d'une collection de nombres.  Il y a deux surcharges de la méthode d'extension `Median`.  La première surcharge accepte, comme entrée, une collection de type `IEnumerable(Of Double)`.  Si la fonction d'agrégation `Median` est appelée pour un champ de requête de type `Double`, cette méthode sera appelée.  La deuxième méthode de surcharge `Median` peut être passée à tout type générique.  La surcharge générique de la méthode `Median` prend un deuxième paramètre qui référence l'expression lambda `Func(Of T, Double)` pour projeter une valeur pour un type \(d'une collection\) comme valeur correspondante de type `Double`.  Il délègue alors le calcul de la valeur médiane à l'autre surcharge de la méthode `Median`.  Pour plus d'informations sur les expressions lambda, consultez [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 L'exemple de code suivant illustre des requêtes d'exemple qui appellent la fonction d'agrégation `Median` sur une collection de type `Integer` et de type `Double`.  La requête qui appelle la fonction d'agrégation `Median` sur la collection de type `Double` appelle la surcharge de la méthode `Median` qui accepte, comme entrée, une collection de type `Double`.  La requête qui appelle la fonction d'agrégation `Median` sur la collection de type `Integer` appelle la surcharge générique de la méthode `Median`.  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Group By, clause](../../../visual-basic/language-reference/queries/group-by-clause.md)