---
title: "group, clause (R&#233;f&#233;rence&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "group"
  - "group_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "group (clause C#)"
  - "group (mot clé C#)"
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# group, clause (R&#233;f&#233;rence&#160;C#)
La clause `group` retourne une séquence d'objets <xref:System.Linq.IGrouping%602> qui contiennent zéro ou plus d'éléments qui correspondent à la valeur de clé pour le groupe.  Par exemple, vous pouvez grouper une séquence de chaînes d'après la première lettre de chaque chaîne.  Dans ce cas, la première lettre est la clé, a un type [char](../../../csharp/language-reference/keywords/char.md) et est stockée dans la propriété `Key` de chaque objet <xref:System.Linq.IGrouping%602>.  Le compilateur déduit le type de la clé.  
  
 Vous pouvez terminer une expression de requête avec une clause `group`, comme indiqué dans l'exemple suivant :  
  
 [!code-cs[cscsrefQueryKeywords#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_1.cs)]  
  
 Si vous souhaitez effectuer des opérations de requête supplémentaires sur chaque groupe, vous pouvez spécifier un identificateur temporaire en utilisant le mot clé contextuel [into](../../../csharp/language-reference/keywords/into.md).  Lorsque vous utilisez `into`, vous devez continuer la requête et finalement la terminer avec une instruction `select` ou une autre clause `group`, comme indiqué dans l'extrait suivant :  
  
 [!code-cs[cscsrefQueryKeywords#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_2.cs)]  
  
 Des exemples plus complets d'utilisation de `group` avec et sans `into` sont fournis dans la section Exemples de cette rubrique.  
  
## Énumération des résultats d'une requête de groupe  
 Étant donné que les objets <xref:System.Linq.IGrouping%602> produits par une requête `group` sont essentiellement une liste de listes, vous devez utiliser une boucle [foreach](../../../csharp/language-reference/keywords/foreach-in.md) imbriquée pour accéder aux éléments de chaque groupe.  La boucle externe itère au sein des clés de groupe et la boucle interne itère au sein de chaque élément du groupe lui\-même.  Un groupe peut avoir une clé, mais aucun élément.  Voici à quoi ressemble la boucle `foreach` qui exécute la requête dans les exemples de code précédents :  
  
 [!code-cs[cscsrefQueryKeywords#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_3.cs)]  
  
## Types de clés  
 Les clés de groupe peuvent être de tout type, comme une chaîne, un type numérique intégré; un type nommé défini par l'utilisateur ou un type anonyme.  
  
### Regroupement par chaîne  
 Les exemples de code précédents ont utilisé un `char`.  Une clé de chaîne aurait pu être spécifiée facilement à la place, par exemple le nom de famille complet :  
  
 [!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_4.cs)]  
  
### Regroupement par booléen  
 L'exemple suivant illustre l'utilisation d'une valeur booléenne pour une clé pour diviser les résultats en deux groupes.  Notez que la valeur est produite par une sous\-expression dans la clause `group`.  
  
 [!code-cs[cscsrefQueryKeywords#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_5.cs)]  
  
### Regroupement par plage numérique.  
 L'exemple suivant utilise une expression pour créer des clés de groupe numériques qui représentent une plage de centiles.  Notez l'utilisation de [let](../../../csharp/language-reference/keywords/let-clause.md) en tant qu'emplacement adéquat pour stocker un résultat d'appel de méthode, de sorte que vous n'avez pas à appeler la méthode deux fois dans la clause `group`.  Notez également dans la clause `group` que pour éviter une exception « division par zéro », le code vérifie que l'étudiant n'a pas une moyenne de zéro.  Pour plus d'informations sur l'utilisation sans risque de méthodes dans les expressions de requête, consultez [Comment : gérer des exceptions dans des expressions de requête](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).  
  
 [!code-cs[cscsrefQueryKeywords#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_6.cs)]  
  
### Regroupement par clés composites  
 Utilisez une clé composite lorsque vous souhaitez grouper des éléments d'après plusieurs clés.  Vous créez une clé composite en utilisant un type anonyme ou un type nommé pour conserver l'élément clé.  Dans l'exemple suivant, supposons qu'une classe `Person` a été déclarée avec les membres nommés `surname` et `city`.  La clause `group` provoque la création d'un groupe séparé pour chaque ensemble de personnes avec le même nom et la même ville.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Utilisez un type nommé si vous devez passer la variable de requête à une autre méthode.  Créez une classe spéciale à l'aide de propriétés implémentées automatiquement pour les clés, puis substituez les méthodes <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A>.  Vous pouvez également utiliser un struct, auquel cas il n'est pas strictement nécessaire de substituer ces méthodes.  Pour plus d'informations, consultez [Comment : implémenter une classe Lightweight avec des propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) et [How to: Query for Duplicate Files in a Directory Tree \(LINQ\)](../Topic/How%20to:%20Query%20for%20Duplicate%20Files%20in%20a%20Directory%20Tree%20\(LINQ\).md).  La dernière rubrique présente un exemple de code qui illustre comment utiliser une clé composite avec un type nommé.  
  
## Exemple  
 L'exemple suivant affiche le modèle standard pour organiser les données source en groupes lorsque aucune logique de requête supplémentaire n'est appliquée aux groupes.  On appelle ceci un regroupement sans continuation.  Les éléments d'un tableau de chaînes sont groupés d'après leur première lettre.  Le résultat de la requête est un type <xref:System.Linq.IGrouping%602> qui contient une propriété `Key` publique de type `char` et une collection <xref:System.Collections.Generic.IEnumerable%601> qui contient chaque élément dans le regroupement.  
  
 Le résultat d'une clause `group` est une séquence de séquences.  Par conséquent, pour accéder aux éléments individuels dans chaque groupe retourné, utilisez une boucle `foreach` imbriquée à l'intérieur de la boucle qui itère au sein des clés de groupe, comme indiqué dans l'exemple suivant.  
  
 [!code-cs[cscsrefQueryKeywords#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_7.cs)]  
  
## Exemple  
 Cet exemple indique comment exécuter une logique supplémentaire sur les groupes après les avoir créés, en utilisant une *continuation* avec `into`.  Pour plus d'informations, consultez [into](../../../csharp/language-reference/keywords/into.md).  L'exemple suivant interroge chaque groupe pour sélectionner uniquement ceux dont la valeur de clé est une voyelle.  
  
 [!code-cs[cscsrefQueryKeywords#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_8.cs)]  
  
## Notes  
 À la compilation, les clauses `group` sont traduites en appels à la méthode <xref:System.Linq.Enumerable.GroupBy%2A>.  
  
## Voir aussi  
 <xref:System.Linq.IGrouping%602>   
 <xref:System.Linq.Enumerable.GroupBy%2A>   
 <xref:System.Linq.Enumerable.ThenBy%2A>   
 <xref:System.Linq.Enumerable.ThenByDescending%2A>   
 [Mots clés de requête \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Comment : créer un groupe imbriqué](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)   
 [Comment : regrouper les résultats d'une requête](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)   
 [Comment : effectuer une sous\-requête sur une opération de regroupement](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)