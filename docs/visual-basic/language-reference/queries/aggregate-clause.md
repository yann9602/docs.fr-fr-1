---
title: Aggregate, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47017414a92bfbca0df4ce6e2b70398a01762d37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate, clause (Visual Basic)
Applique une ou plusieurs fonctions d’agrégation à une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`element`|Obligatoire. Variable utilisée pour parcourir les éléments de la collection.|  
|`type`|Facultatif. Type d'élément `element`. Si aucun type n’est spécifié, le type de `element` est déduit à partir de `collection`.|  
|`collection`|Obligatoire. Fait référence à la collection sur laquelle opérer.|  
|`clause`|Facultatif. Une ou plusieurs clauses de requête, comme un `Where` clause, pour affiner le résultat de la requête pour appliquer l’ou les clauses d’agrégation.|  
|`expressionList`|Obligatoire. Une ou plusieurs virgules expressions qui identifient une fonction d’agrégation à appliquer à la collection. Vous pouvez appliquer un alias à une fonction d’agrégation pour spécifier un nom de membre pour le résultat de la requête. Si aucun alias n’est fourni, le nom de la fonction d’agrégation est utilisé. Pour obtenir des exemples, consultez la section sur les fonctions d’agrégation plus loin dans cette rubrique.|  
  
## <a name="remarks"></a>Remarques  
 Le `Aggregate` clause peut être utilisée pour inclure des fonctions d’agrégation dans vos requêtes. Fonctions d’agrégation effectuent des vérifications et des calculs sur un ensemble de valeurs et retournent une valeur unique. Vous pouvez accéder à la valeur calculée à l’aide d’un membre du type du résultat de requête. Les fonctions d’agrégation standards que vous pouvez utiliser sont les `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, et `Sum` fonctions. Ces fonctions sont familières aux développeurs qui sont familiarisés avec les agrégats dans SQL. Ils sont décrits dans la section suivante de cette rubrique.  
  
 Le résultat d’une fonction d’agrégation est inclus dans le résultat de requête en tant que champ de type de résultat de requête. Vous pouvez fournir un alias pour le résultat de la fonction d’agrégation spécifier le nom du membre du type du résultat de requête qui contiendra la valeur d’agrégation. Si aucun alias n’est fourni, le nom de la fonction d’agrégation est utilisé.  
  
 Le `Aggregate` clause peut commencer une requête, ou il peut être inclus en tant que clause supplémentaire dans une requête. Si le `Aggregate` clause commence une requête, le résultat est une valeur unique qui est le résultat de la fonction d’agrégation spécifiée dans le `Into` clause. Si plusieurs fonctions d’agrégation sont spécifiée dans le `Into` clause, la requête retourne un type unique avec une propriété séparée pour référencer le résultat de chaque fonction d’agrégation dans la `Into` clause. Si le `Aggregate` clause est incluse en tant que clause supplémentaire dans une requête, le type retourné dans la collection de requêtes aura une propriété distincte pour référencer le résultat de chaque fonction d’agrégation dans la `Into` clause.  
  
## <a name="aggregate-functions"></a>Fonctions d'agrégation  
 La liste suivante décrit les fonctions d’agrégation standards qui peuvent être utilisées avec le `Aggregate` clause.  
  
|Fonction|Description|  
|---|---|  
|`All`|Retourne `true` si tous les éléments de la collection répondent à une condition spécifiée ; sinon, retourne `false`. Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|Retourne `true` si un élément de la collection satisfait une condition spécifiée ; sinon, retourne `false`. Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|Calcule la moyenne de tous les éléments de la collection, ou une expression fournie pour tous les éléments dans la collection. Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|Compte le nombre d’éléments dans la collection. Vous pouvez fournir un texte facultatif `Boolean` expression pour compter uniquement le nombre d’éléments dans la collection qui répondent à une condition. Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|Fait référence à des résultats de requête sont regroupés à la suite d’un `Group By` ou `Group Join` clause. Le `Group` (fonction) est valide uniquement dans les `Into` clause d’une `Group By` ou `Group Join` clause. Pour plus d’informations et d’exemples, consultez [Group By Clause](../../../visual-basic/language-reference/queries/group-by-clause.md) et [Group Join, Clause](../../../visual-basic/language-reference/queries/group-join-clause.md).|  
|`LongCount`|Compte le nombre d’éléments dans la collection. Vous pouvez fournir un texte facultatif `Boolean` expression pour compter uniquement le nombre d’éléments dans la collection qui répondent à une condition. Retourne le résultat comme un `Long`. Pour obtenir un exemple, consultez la `Count` fonction d’agrégation.|  
|`Max`|Calcule la valeur maximale de la collection, ou une expression fournie pour tous les éléments dans la collection. Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|Calcule la valeur minimale de la collection, ou une expression fournie pour tous les éléments dans la collection. Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|Calcule la somme de tous les éléments dans la collection, ou une expression fournie pour tous les éléments dans la collection. Voici un exemple :<br /><br /> [!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser le `Aggregate` clause pour appliquer des fonctions d’agrégation à un résultat de requête.  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Création de fonctions d’agrégation définies par l’utilisateur  
 Vous pouvez inclure vos propres fonctions d’agrégation personnalisées dans une expression de requête en ajoutant des méthodes d’extension pour le <xref:System.Collections.Generic.IEnumerable%601> type. Votre méthode personnalisée peut ensuite effectuer un calcul ou une opération sur la collection énumérable qui a référencé votre fonction d’agrégation. Pour plus d’informations sur les méthodes d’extension, consultez [Méthodes d’extension](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Par exemple, l’exemple de code suivant montre une fonction d’agrégation personnalisée qui calcule la valeur médiane d’une collection de nombres. Il existe deux surcharges de la `Median` méthode d’extension. La première surcharge accepte comme entrée, une collection de type `IEnumerable(Of Double)`. Si le `Median` fonction d’agrégation est appelée pour un champ de requête de type `Double`, cette méthode est appelée. La deuxième surcharge de la `Median` un type générique peut être passé à la méthode. La surcharge générique de la `Median` méthode prend un deuxième paramètre qui référence le `Func(Of T, Double)` une expression lambda à une valeur pour un type (à partir d’une collection) du projet en tant que la valeur correspondante de type `Double`. Elle délègue ensuite le calcul de la valeur médiane à l’autre surcharge de la `Median` (méthode). Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 Le code suivant exemple représente un exemple de requêtes qui appellent le `Median` fonction sur une collection de type d’agrégation `Integer`et une collection de type `Double`. La requête qui appelle la `Median` fonction sur la collection de type d’agrégation `Double` appelle la surcharge de la `Median` méthode qui accepte comme entrée, une collection de type `Double`. La requête qui appelle la `Median` fonction sur la collection de type d’agrégation `Integer` appelle la surcharge générique de la `Median` (méthode).  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Requêtes](../../../visual-basic/language-reference/queries/queries.md)  
 [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Group By (clause)](../../../visual-basic/language-reference/queries/group-by-clause.md)
