---
title: "Comment&#160;: effectuer des jointures internes (Guide de programmation&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "jointures internes (LINQ en C#)"
  - "jointures (C#), internes"
  - "requêtes (LINQ en C#), jointures"
  - "expressions de requête (LINQ en C#), jointures"
ms.assetid: d9edb404-8314-413e-ae51-83bb86c7a4b5
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: effectuer des jointures internes (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Dans les termes de base de données relationnelle, une *jointure interne* génère un jeu de résultats dans lequel chaque élément de la première collection apparaît une fois pour chaque élément correspondant dans la deuxième collection.  Si un élément de la première collection n'a pas d'éléments correspondants, il n'apparaît pas dans le jeu de résultats.  La méthode <xref:System.Linq.Enumerable.Join%2A>, qui est appelée par la clause `join` dans C\#, implémente une jointure interne.  
  
 Cette rubrique explique comment effectuer quatre variations d'une jointure interne :  
  
-   Une jointure interne simple qui met en corrélation des éléments de deux sources de données selon une clé simple.  
  
-   Une jointure interne qui met en corrélation des éléments de deux sources de données selon une clé *composite*.  Une clé composite, qui est une clé qui se compose de plusieurs valeurs, vous permet de mettre en corrélation des éléments selon plusieurs propriétés.  
  
-   Une *jointure multiple* dans laquelle les opérations de jointure consécutives sont ajoutées l'une à l'autre.  
  
-   Une jointure interne implémentée en utilisant une jointure groupée.  
  
## Exemple  
  
## Exemple de jointure de clé simple  
 L'exemple suivant crée deux collections qui contiennent des objets de deux types définis par l'utilisateur, `Person` et `Pet`.  La requête utilise la clause `join` dans C\# pour faire correspondre des objets `Person` avec des objets `Pet` dont `Owner` est `Person`.  La clause `select` dans C\# définit l'apparence des objets résultants.  Dans cet exemple, les objets résultants sont des types anonymes qui se composent du prénom du propriétaire et du nom de l'animal domestique.  
  
 [!code-cs[CsLINQProgJoining#1](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-inner-joins_1.cs)]  
  
 Notez que l'objet `Person` dont `LastName` est « Huff » n'apparaît pas dans le jeu de résultats, car aucun objet `Pet` qui a `Pet.Owner` n'est égal à `Person`.  
  
## Exemple  
  
## Exemple de jointure de clé composite  
 Au lieu de mettre en corrélation des éléments selon une seule propriété, vous pouvez utiliser une clé composite pour comparer des éléments selon plusieurs propriétés.  Pour ce faire, spécifiez la fonction de sélection de clé de chaque collection pour retourner un type anonyme qui se compose des propriétés vous souhaitez comparer.  Si vous étiquetez les propriétés, elles doivent avoir la même étiquette dans le type anonyme de chaque clé.  Les propriétés doivent également apparaître dans le même ordre.  
  
 L'exemple suivant utilise une liste d'objets `Employee` et une liste d'objets `Student` pour déterminer quels employés sont également des étudiants.  Ces deux types ont une propriété `FirstName` et `LastName` de type <xref:System.String>.  Les fonctions qui créent les clés de jointure à partir des éléments de chaque liste retournent un type anonyme qui se compose des propriétés `FirstName` et `LastName` de chaque élément.  L'opération de jointure compare ces clés composites à la recherche d'une égalité et retourne des paires d'objets dans chaque liste présentant une correspondance entre le prénom et le nom.  
  
 [!code-cs[CsLINQProgJoining#2](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-inner-joins_2.cs)]  
  
## Exemple  
  
## Exemple de jointure multiple  
 Toutes les opérations de jointure peuvent être ajoutées l'une à l'autre, quelle que soit leur nombre, pour effectuer une jointure multiple.  Chaque clause `join` dans C\# met en corrélation une source de données spécifiée avec les résultats de la jointure précédente.  
  
 L'exemple suivant crée trois collections : une liste d'objets `Person`, une liste d'objets `Cat` et une liste d'objets `Dog`.  
  
 La première clause `join` dans C\# correspond à des personnes et des chats basés sur un objet `Person` correspondant à `Cat.Owner`.  Elle retourne une séquence de types anonymes qui contiennent l'objet `Person` et `Cat.Name`.  
  
 La deuxième clause `join` dans C\# met en corrélation les types anonymes retournés par la première jointure avec les objets `Dog` de la liste de chiens fournie, selon une clé composite qui se compose de la propriété `Owner` de type `Person` et de la première lettre du nom de l'animal.  Elle retourne une séquence de types anonymes qui contiennent les propriétés `Cat.Name` et `Dog.Name` de chaque paire correspondante.  Étant donné qu'il s'agit d'une jointure interne, seuls les objets de la première source de données qui ont une correspondance dans la deuxième source de données sont retournés.  
  
 [!code-cs[CsLINQProgJoining#3](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-inner-joins_3.cs)]  
  
## Exemple  
  
## Exemple de jointure interne à l'aide d'une jointure groupée  
 L'exemple suivant indique comment implémenter une jointure interne en utilisant une jointure groupée.  
  
 Dans `query1`, la liste d'objets `Person` est jointe par groupe à la liste d'objets `Pet` en fonction de l'objet `Person` qui correspond à la propriété `Pet.Owner`.  La jointure groupée crée une collection de groupes intermédiaires où chaque groupe se compose d'un objet `Person` et d'une séquence d'objets `Pet` correspondants.  
  
 En ajoutant une deuxième clause `from` à la requête, cette séquence de séquences est combinée \(ou aplatie\) dans une séquence plus longue.  Le type des éléments de la séquence finale est spécifié par la clause `select`.  Dans cet exemple, ce type est un type anonyme qui se compose des propriétés `Person.FirstName` et `Pet.Name` pour chaque paire correspondante.  
  
 Le résultat de `query1` est équivalent au jeu de résultats qui aurait été obtenu en utilisant la clause `join` sans la clause `into` pour effectuer une jointure interne.  La variable `query2` illustre cette requête équivalente.  
  
 [!code-cs[CsLINQProgJoining#4](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-inner-joins_4.cs)]  
  
## Compilation du code  
  
-   Créez un projet d'application console dans [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)].  
  
-   Ajoutez une référence à System.Core.dll si elle n'est pas déjà référencée.  
  
-   Incluez l'espace de noms <xref:System.Linq>.  
  
-   Copiez et collez le code à partir de l'exemple dans le fichier program.cs, sous la méthode `Main`.  Ajoutez une ligne de code à la méthode `Main` pour appeler la méthode que vous avez collée.  
  
-   Exécutez le programme.  
  
## Voir aussi  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [Comment : effectuer des jointures groupées](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [Procédures : effectuer des jointures externes gauches](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [Procédure : joindre deux collections](../Topic/How%20to:%20Join%20Two%20Collections%20\(C%23\)%20\(LINQ%20to%20XML\).md)   
 [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)