---
title: From, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ecdc8b70fb1ae164a6c78998ce11db9938fbb56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="from-clause-visual-basic"></a>From, clause (Visual Basic)
Spécifie une ou plusieurs variables de plage et une collection à interroger.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`element`|Obligatoire. A *variable de portée* utilisé pour itérer sur les éléments de la collection. Une variable de portée est utilisée pour faire référence à chaque membre de la `collection` que la requête itère le `collection`. Doit être un type énumérable.|  
|`type`|Facultatif. Type d'élément `element`. Si aucun `type` est spécifié, le type de `element` est déduit à partir de `collection`.|  
|`collection`|Obligatoire. Fait référence à la collection à interroger. Doit être un type énumérable.|  
  
## <a name="remarks"></a>Remarques  
 Le `From` clause est utilisée pour identifier les données sources pour une requête et les variables qui sont utilisées pour faire référence à un élément dans la collection source. Ces variables sont appelées *les variables de plage*. Le `From` clause est requise pour une requête, sauf quand le `Aggregate` clause est utilisée pour identifier une requête qui retourne des résultats uniquement regroupés. Pour plus d’informations, consultez [Aggregate, Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Vous pouvez spécifier plusieurs `From` clauses dans une requête pour identifier plusieurs collections à joindre. Lorsque plusieurs collections sont spécifiées, elles sont itérées indépendamment, ou vous pouvez les joindre si elles sont associées. Vous pouvez joindre implicitement des collections à l’aide de la `Select` clause, ou explicitement en utilisant la `Join` ou `Group Join` clauses. En guise d’alternative, vous pouvez spécifier des variables de portée et des collections multiples dans une seule `From` clause, avec chaque variable de portée et les collections séparées des autres par une virgule. L’exemple de code suivant montre les deux options de syntaxe pour le `From` clause.  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 Le `From` clause définit l’étendue d’une requête, qui est semblable à la portée d’un `For` boucle. Par conséquent, chaque `element` variable de portée dans la portée d’une requête doit avoir un nom unique. Étant donné que vous pouvez spécifier plusieurs `From` clauses d’une requête, ultérieure `From` clauses peuvent faire référence à des variables de portée dans le `From` clause, ou ils peuvent faire référence à des variables de plage dans une précédente `From` clause. Par exemple, l’exemple suivant montre une manière imbriquée `From` clause où la collection dans la deuxième clause est basée sur une propriété de la variable de portée dans la première clause.  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 Chaque `From` clause peut être suivie de n’importe quelle combinaison de clauses de requête supplémentaires pour affiner la requête. Vous pouvez affiner la requête comme suit :  
  
-   Combinez plusieurs collections de manière implicite à l’aide de la `From` et `Select` clauses, ou explicitement en utilisant la `Join` ou `Group Join` clauses.  
  
-   Utilisez le `Where` clause pour filtrer les résultats de la requête.  
  
-   Trier le résultat à l’aide de la `Order By` clause.  
  
-   Regrouper des résultats similaires à l’aide du `Group By` clause.  
  
-   Utilisez le `Aggregate` clause pour identifier les fonctions d’agrégation à évaluer pour le résultat de toute requête.  
  
-   Utilisez le `Let` clause pour introduire une variable d’itération dont la valeur est déterminée par une expression au lieu d’une collection.  
  
-   Utilisez le `Distinct` clause pour ignorer les résultats de la requête en double.  
  
-   Identifier les parties du résultat à retourner à l’aide de la `Skip`, `Take`, `Skip While`, et `Take While` clauses.  
  
## <a name="example"></a>Exemple  
 La requête suivante expression utilise une `From` clause pour déclarer une variable de portée `cust` pour chaque `Customer` de l’objet dans le `customers` collection. Le `Where` clause utilise la variable de portée pour restreindre la sortie aux clients à partir de la région spécifiée. Le `For Each` boucle affiche le nom de société pour chaque client dans le résultat de la requête.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes](../../../visual-basic/language-reference/queries/queries.md)  
 [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [For Each...Next (instruction)](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Aggregate (clause)](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Distinct (clause)](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [Join (clause)](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Group Join (clause)](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Order By (clause)](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Let (clause)](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Skip (clause)](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take (clause)](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While (clause)](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take While (clause)](../../../visual-basic/language-reference/queries/take-while-clause.md)
