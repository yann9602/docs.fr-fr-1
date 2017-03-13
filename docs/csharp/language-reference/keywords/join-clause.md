---
title: "join, clause (R&#233;f&#233;rence&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "join"
  - "join_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Join (clause C#)"
  - "join (mot clé C#)"
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# join, clause (R&#233;f&#233;rence&#160;C#)
La clause `join` est utile pour associer des éléments de séquences source différentes qui n'ont aucune relation directe dans le modèle objet.  La seule spécification est que les éléments de chaque source partagent une valeur qui peut être comparée pour déterminer leur égalité.  Par exemple, un distributeur de nourriture peut avoir une liste de fournisseurs d'un certain produit et une liste d'acheteurs.  Une clause `join` peut être utilisée, par exemple, pour créer une liste des fournisseurs et des acheteurs de ce produit qui sont tous dans la même région spécifiée.  
  
 Une clause `join` prend deux séquences source comme entrée.  Les éléments de chaque séquence doivent être ou contenir une propriété qui peut être comparée à une propriété correspondante dans l'autre séquence.  La clause `join` compare les clés spécifiées pour déterminer leur égalité en utilisant le mot clé spécial `equals`.  Toutes les jointures effectuées par la clause `join` sont des équijointures.  La forme de la sortie d'une clause `join` dépend du type spécifique de jointure que vous effectuez.  Les trois types de jointures les plus courants sont  
  
-   Jointure interne  
  
-   Jointure groupée  
  
-   Jointure externe gauche  
  
## Jointure interne  
 L'exemple suivant présente une équijointure interne simple.  Cette requête produit une séquence en deux dimensions des paires « nom de produit\/catégorie ».  La même chaîne de catégorie apparaîtra dans plusieurs éléments.  Si un élément de `categories` n'a aucun `products` correspondant, cette catégorie n'apparaîtra pas dans les résultats.  
  
 [!code-cs[cscsrefQueryKeywords#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_1.cs)]  
  
 Pour plus d'informations, consultez [Comment : effectuer des jointures internes](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md).  
  
## Group Join  
 Une clause `join` avec une expression `into` est appelée une jointure groupée.  
  
 [!code-cs[cscsrefQueryKeywords#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_2.cs)]  
  
 Une jointure groupée produit une séquence de résultat hiérarchique, qui associe des éléments dans la séquence source gauche à un ou plusieurs éléments correspondants dans la séquence source droite.  Une jointure groupée n'a aucun équivalent en termes relationnels ; il s'agit essentiellement d'une séquence de tableaux d'objets.  
  
 Si aucun élément de la bonne séquence source est recherché pour correspondre à un élément dans la source gauche, la clause `join` produira un tableau vide pour cet élément.  Par conséquent, la jointure groupée est encore fondamentalement une équijointure interne, mais la séquence de résultat est organisée en groupes.  
  
 Si vous sélectionnez uniquement les résultats d'une jointure groupée, vous pouvez accéder aux éléments, mais vous ne pouvez pas identifier la clé à laquelle ils correspondent.  Par conséquent, il est généralement plus utile de sélectionner les résultats de la jointure groupée dans un nouveau type qui a également le nom de la clé, comme indiqué dans l'exemple précédent.  
  
 Bien sûr, vous pouvez également utiliser le résultat d'une jointure groupée comme générateur d'une autre sous\-requête :  
  
 [!code-cs[cscsrefQueryKeywords#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_3.cs)]  
  
 Pour plus d'informations, consultez [Comment : effectuer des jointures groupées](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md).  
  
## Jointure externe gauche  
 Dans une jointure externe gauche, tous les éléments de la séquence source gauche sont retournés, même s'ils n'ont aucun élément correspondant dans la séquence droite.  Pour effectuer une jointure externe gauche dans [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)], utilisez la méthode `DefaultIfEmpty` en association avec une jointure groupée pour spécifier un élément de droite par défaut à produire si un élément de gauche n'a aucune correspondance.  Vous pouvez utiliser `null` comme valeur par défaut pour tout type référence ou vous pouvez spécifier un type par défaut défini par l'utilisateur.  Un type par défaut défini par l'utilisateur est présenté dans l'exemple suivant :  
  
 [!code-cs[cscsrefQueryKeywords#27](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_4.cs)]  
  
 Pour plus d'informations, consultez [Procédures : effectuer des jointures externes gauches](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md).  
  
## L'opérateur égal \(equals\)  
 Une clause `join` effectue une équijointure.  En d'autres termes, vous pouvez baser uniquement les correspondances sur l'égalité de deux clés.  D'autres types de comparaisons, comme « supérieur à » ou « différent de », ne sont pas pris en charge.  Pour préciser clairement que toutes les jointures sont des équijointures, la clause `join` utilise le mot clé `equals` au lieu de l'opérateur `==`.  Le mot clé `equals` peut être utilisé uniquement dans une clause `join` et diffère de l'opérateur `==` sur un plan important.  Avec `equals`, la clé gauche consomme la séquence source externe et la clé droite consomme la source interne.  La source externe est uniquement dans la portée sur le côté gauche de `equals` et la séquence source interne est uniquement dans la portée sur le côté droit.  
  
## Non\-équijointures  
 Vous pouvez effectuer des non\-équijointures, des jointures croisées et d'autres opérations de jointure personnalisées en utilisant plusieurs clauses `from` pour introduire indépendamment de nouvelles séquences dans une requête.  Pour plus d'informations, consultez [Comment : effectuer des opérations de jointure personnalisées](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).  
  
## Jointures sur les collections d'objets ousur les tables relationnelles  
 Dans une expression de requête [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)], les opérations de jointure sont effectuées sur les collections d'objets.  Les collections d'objets ne peuvent pas être « jointes » exactement de la même manière que deux tables relationnelles.  Dans [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)], les clauses `join` explicites sont requises uniquement lorsque deux séquences source ne sont pas liées par une quelconque relation.  Lorsque vous travaillez avec [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)], les tables de clés étrangères sont représentées dans le modèle objet comme des propriétés de la table primaire.  Par exemple, la table Customer a une relation de clé étrangère avec la table Orders dans la base de données Northwind.  Lorsque vous mappez les tables au modèle objet, la classe Customer a une propriété Orders qui contient la collection d'Orders associée à ce Customer.  En effet, la jointure a déjà été effectuée pour vous.  
  
 Pour plus d'informations sur l'interrogation de tables connexes dans le contexte de [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)], consultez [Procédure : mapper des relations de base de données](../Topic/How%20to:%20Map%20Database%20Relationships.md).  
  
## Clés composites  
 Vous pouvez effectuer un test d'égalité de plusieurs valeurs à l'aide d'une clé composite.  Pour plus d'informations, consultez [Comment : effectuer des opérations de jointure à l'aide de clés composites](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md).  Des clés composites peuvent également être utilisées dans une clause `group`.  
  
## Exemple  
 L'exemple suivant compare les résultats d'une jointure interne, d'une jointure groupée et d'une jointure externe gauche sur les mêmes sources de données en utilisant les mêmes clés correspondantes.  Du code supplémentaire est ajouté à ces exemples pour clarifier les résultats dans l'affichage de la console.  
  
 [!code-cs[cscsrefQueryKeywords#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_5.cs)]  
  
## Notes  
 Une clause `join` qui n'est pas suivie par `into` est traduite en un appel de méthode <xref:System.Linq.Enumerable.Join%2A>.  Une clause `join` qui est suivie par `into` est traduite en un appel de méthode <xref:System.Linq.Enumerable.GroupJoin%2A>.  
  
## Voir aussi  
 [Mots clés de requête \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [group, clause](../../../csharp/language-reference/keywords/group-clause.md)   
 [Procédures : effectuer des jointures externes gauches](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [Comment : effectuer des jointures internes](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [Comment : effectuer des jointures groupées](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [Comment : classer les résultats d'une clause Join](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)   
 [Comment : effectuer des opérations de jointure à l'aide de clés composites](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)   
 [Comment : installer des exemples de bases de données](../Topic/How%20to:%20Install%20Sample%20Databases.md)