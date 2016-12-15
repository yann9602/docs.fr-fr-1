---
title: "from, clause (R&#233;f&#233;rence&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "from_CSharpKeyword"
  - "from"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "from (clause C#)"
  - "from (mot clé C#)"
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
caps.latest.revision: 27
caps.handback.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# from, clause (R&#233;f&#233;rence&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une expression de requête doit commencer par une clause `from`.  En outre, une expression de requête peut contenir des sous\-requêtes qui commencent également par une clause `from`.  La clause `from` spécifie les éléments suivants :  
  
-   La source de données sur laquelle la requête ou la sous\-requête sera exécutée.  
  
-   Une *variable de portée* locale qui représente chaque élément dans la séquence source.  
  
 La variable de portée et la source de données sont toutes les deux fortement typées.  La source de données référencée dans la clause `from` doit avoir un type de <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601> ou un type dérivé tel que <xref:System.Linq.IQueryable%601>.  
  
 Dans l'exemple suivant, `numbers` est la source de données et `num` est la variable de portée.  Notez que les deux variables sont fortement typées même lorsque le mot clé [var](../../../csharp/language-reference/keywords/var.md) est utilisé.  
  
 [!code-cs[cscsrefQueryKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_1.cs)]  
  
## Variable de portée  
 Le compilateur déduit le type de la variable de portée lorsque la source de données implémente <xref:System.Collections.Generic.IEnumerable%601>.  Par exemple, si la source a un type de `IEnumerable<Customer>`, alors la variable de portée est déduite pour être `Customer`.  Vous devez spécifier le type explicitement uniquement lorsque la source est un type `IEnumerable` non générique tel que <xref:System.Collections.ArrayList>.  Pour plus d'informations, consultez [How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md).  
  
 Dans l'exemple précédent, `num` est déduit pour être de type `int`.  Comme la variable de portée est fortement typée, vous pouvez appeler des méthodes sur celle\-ci ou l'utiliser dans d'autres opérations.  Par exemple, au lieu d'écrire `select num`, vous pourriez écrire `select num.ToString()` pour que l'expression de requête retourne une séquence de chaînes à la place d'entiers.  Vous pouvez également écrire `select n + 10` pour que l'expression retourne la séquence 14, 11, 13, 12, 10.  Pour plus d'informations, consultez [select, clause](../../../csharp/language-reference/keywords/select-clause.md).  
  
 La variable de portée est semblable à une variable d'itération dans une instruction [foreach](../../../csharp/language-reference/keywords/foreach-in.md) à une différence près qui est importante : une variable de portée ne stocke jamais réellement de données de la source.  En termes de syntaxe, son utilisation est simplement plus pratique et elle permet à la requête de décrire ce qui se produira lors de son exécution.  Pour plus d'informations, consultez [Introduction to LINQ Queries \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
## Clauses from composées  
 Dans quelques cas, chaque élément dans la séquence source peut être une séquence ou contenir une séquence.  Par exemple, votre source de données peut être un `IEnumerable<Student>` où chaque objet Student dans la séquence contient une liste de notes d'examens.  Pour accéder à la liste interne dans chaque élément `Student`, vous pouvez utiliser des clauses `from` composées.  Cette technique est proche de celle consistant à utiliser des instructions [foreach](../../../csharp/language-reference/keywords/foreach-in.md) imbriquées.  Vous pouvez ajouter des clauses [where](../../../csharp/language-reference/keywords/partial-method.md) ou [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) à l'une et l'autre des clauses `from` pour filtrer les résultats.  L'exemple suivant présente une séquence d'objets `Student` et chacun contient un `List` interne des entiers qui représentent des notes d'examens.  Pour accéder à la liste interne, utilisez une clause `from` composée.  Vous pouvez insérer des clauses entre les deux clauses `from` si nécessaire.  
  
 [!code-cs[cscsrefQueryKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_2.cs)]  
  
## Utilisation de plusieurs clauses pour effectuer des jointures  
 Une clause `from` composée est utilisée pour accéder aux collections internes dans une source de données unique.  Toutefois, une requête peut également contenir plusieurs clauses `from` qui génèrent des requêtes supplémentaires de sources de données indépendantes.  Cette technique vous permet d'effectuer certains types d'opérations de jointure qui ne sont pas possibles en utilisant la [clause de jointure](../../../csharp/language-reference/keywords/join-clause.md).  
  
 L'exemple suivant montre comment utiliser deux clauses `from` pour former une jointure croisée complète de deux sources de données.  
  
 [!code-cs[cscsrefQueryKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_3.cs)]  
  
 Pour plus d'informations sur les opérations de jointure qui utilisent plusieurs clauses `from`, consultez [Comment : effectuer des opérations de jointure personnalisées](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).  
  
## Voir aussi  
 [Mots clés de requête \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)