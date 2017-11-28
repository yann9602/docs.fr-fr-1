---
title: "from, clause (Référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f718f50d2b8d6f5c612113414a2106fed37fe0fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="from-clause-c-reference"></a>from, clause (Référence C#)
Une expression de requête doit commencer par une clause `from`. Une expression de requête peut également contenir des sous-requêtes qui commencent elles aussi par une clause `from`. La clause `from` spécifie les éléments suivants :  
  
-   La source de données sur laquelle la requête ou la sous-requête est exécutée.  
  
-   Une *variable de portée locale* qui représente chaque élément dans la séquence source.  
  
 La variable de portée et la source de données sont toutes les deux fortement typées. La source de données référencée dans la clause `from` doit avoir un type <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601> ou un type dérivé comme <xref:System.Linq.IQueryable%601>.  
  
 Dans l’exemple suivant, `numbers` est la source de données tandis que `num` est la variable de portée. Notez que les deux variables sont fortement typées même si le mot clé [var](../../../csharp/language-reference/keywords/var.md) est utilisé.  
  
 [!code-csharp[cscsrefQueryKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_1.cs)]  
  
## <a name="the-range-variable"></a>Variable de portée  
 Le compilateur déduit le type de la variable de portée quand la source de données implémente <xref:System.Collections.Generic.IEnumerable%601>. Par exemple, si la source a un type `IEnumerable<Customer>`, la variable de portée est déduite comme étant `Customer`. Vous devez spécifier le type de façon explicite uniquement quand la source est un type `IEnumerable` non générique comme <xref:System.Collections.ArrayList>. Pour plus d’informations, consultez [Guide pratique pour interroger une liste de tableaux avec LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).  
  
 Dans l’exemple précédent, `num` est déduit comme étant de type `int`. Comme la variable de portée est fortement typée, vous pouvez appeler des méthodes sur celle-ci ou l’utiliser dans d’autres opérations. Par exemple, au lieu d’écrire `select num`, vous pouvez écrire `select num.ToString()` pour que l’expression de requête retourne une séquence de chaînes à la place d’entiers. Vous pouvez également écrire `select n + 10` pour que l’expression retourne la séquence 14, 11, 13, 12, 10. Pour plus d’informations, consultez [select, clause](../../../csharp/language-reference/keywords/select-clause.md).  
  
 La variable de portée est semblable à une variable d’itération dans une instruction [foreach](../../../csharp/language-reference/keywords/foreach-in.md) à une différence près, très importante : une variable de portée ne stocke jamais réellement de données de la source. Il s’agit juste d’un avantage syntaxique pratique qui permet à la requête de décrire ce qui se produira lors de son exécution. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
## <a name="compound-from-clauses"></a>Clauses from composées  
 Dans certains cas, chaque élément dans la séquence source peut être une séquence ou contenir une séquence. Par exemple, votre source de données peut être un `IEnumerable<Student>` où chaque objet Student dans la séquence contient une liste de notes d’examens. Pour accéder à la liste interne dans chaque élément `Student`, vous pouvez utiliser des clauses `from` composées. Cette technique est proche de celle consistant à utiliser des instructions [foreach](../../../csharp/language-reference/keywords/foreach-in.md) imbriquées. Vous pouvez ajouter des clauses [where](../../../csharp/language-reference/keywords/partial-method.md) ou [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) à l’une et l’autre des clauses `from` pour filtrer les résultats. L’exemple suivant présente une séquence d’objets `Student` et chacun contient un `List` interne des entiers qui représentent des notes d’examens. Pour accéder à la liste interne, utilisez une clause `from` composée. Vous pouvez insérer des clauses entre les deux clauses `from` si nécessaire.  
  
 [!code-csharp[cscsrefQueryKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_2.cs)]  
  
## <a name="using-multiple-from-clauses-to-perform-joins"></a>Utilisation de plusieurs clauses from pour effectuer des jointures  
 Une clause `from` composée est utilisée pour accéder aux collections internes dans une source de données unique. Toutefois, une requête peut également contenir plusieurs clauses `from` qui génèrent des requêtes supplémentaires de sources de données indépendantes. Cette technique vous permet d’effectuer certains types d’opérations de jointure qui ne sont pas possibles en utilisant la [clause join](../../../csharp/language-reference/keywords/join-clause.md).  
  
 L’exemple suivant montre comment utiliser deux clauses `from` pour former une jointure croisée complète de deux sources de données.  
  
 [!code-csharp[cscsrefQueryKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_3.cs)]  
  
 Pour plus d’informations sur les opérations de jointure qui utilisent plusieurs clauses `from`, consultez [Guide pratique pour effectuer des opérations de jointure personnalisées](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés de requête (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
