---
title: Effectuer des jointures internes
description: Guide pratique pour effectuer des jointures internes.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6492e536976b74fa0a0b06cdc94d8aad9584e5be
ms.lasthandoff: 03/13/2017

---
# <a name="perform-inner-joins"></a>Effectuer des jointures internes

Dans le domaine des bases de données relationnelles, une *jointure interne* produit un jeu de résultats dans lequel chaque élément de la première collection apparaît une fois pour chaque élément correspondant dans la deuxième collection. Si un élément de la première collection n’a pas d’élément correspondant, il n’apparaît pas dans le jeu de résultats. La méthode <xref:System.Linq.Enumerable.Join%2A>, qui est appelée par la clause `join` dans C#, implémente une jointure interne.  
  
 Cette rubrique explique comment effectuer quatre variations d’une jointure interne :  
  
-   Une jointure interne simple qui met en corrélation des éléments de deux sources de données sur la base d’une clé simple.  
  
-   Une jointure interne qui met en corrélation des éléments de deux sources de données sur la base d’une clé *composite*. Une clé composite, qui est une clé composée de plusieurs valeurs, permet de mettre en corrélation des éléments sur la base de plusieurs propriétés.  
  
-   Une *jointure multiple* dans laquelle les opérations de jointure consécutives sont ajoutées les unes aux autres.  
  
-   Une jointure interne qui est implémentée à l’aide d’une jointure groupée.  
  
## <a name="example"></a>Exemple  
  
## <a name="simple-key-join-example"></a>Exemple de jointure de clé simple  
 L’exemple suivant crée deux collections qui contiennent des objets de deux types définis par l’utilisateur, `Person` et `Pet`. La requête utilise la clause `join` dans C# pour faire correspondre les objets `Person` avec les objets `Pet` dont la propriété `Owner` est `Person`. La clause `select` dans C# définit l’apparence des objets résultants. Dans cet exemple, les objets résultants sont des types anonymes qui se composent du prénom du propriétaire et du nom de l’animal domestique.  
  
 [!code-cs[CsLINQProgJoining#1](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]  
  
 Notez que l’objet `Person` dont la propriété `LastName` est « Huff » n’apparaît pas dans le jeu de résultats, car il n’y a pas d’objet `Pet` ayant une propriété `Pet.Owner` égale à `Person`.  
  
## <a name="example"></a>Exemple  
  
## <a name="composite-key-join-example"></a>Exemple de jointure de clé composite  
 Au lieu de mettre en corrélation des éléments sur la base d’une seule propriété, vous pouvez utiliser une clé composite pour comparer des éléments en fonction de plusieurs propriétés. Pour ce faire, spécifiez la fonction de sélection de clé de chaque collection pour retourner un type anonyme qui se compose des propriétés à comparer. Si vous étiquetez les propriétés, elles doivent avoir la même étiquette dans le type anonyme de chaque clé. Les propriétés doivent également apparaître dans le même ordre.  
  
 L’exemple suivant utilise une liste d’objets `Employee` et une liste d’objets `Student` pour déterminer quels employés sont également étudiants. Ces deux types ont des propriétés `FirstName` et `LastName` de type <xref:System.String>. Les fonctions qui créent les clés de jointure à partir des éléments de chaque liste retournent un type anonyme qui se compose des propriétés `FirstName` et `LastName` de chaque élément. L’opération de jointure effectue une comparaison d’égalité de ces clés composites et retourne les paires d’objets de chaque liste où il y a correspondance entre le prénom et le nom.  
  
 [!code-cs[CsLINQProgJoining#2](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]  
  
## <a name="example"></a>Exemple  
  
## <a name="multiple-join-example"></a>Exemple de jointure multiple  
 Vous pouvez effectuer une jointure multiple en ajoutant n’importe quel nombre d’opérations de jointure les unes aux autres. Chaque clause `join` dans C# met en corrélation une source de données spécifiée avec les résultats de la jointure précédente.  
  
 L’exemple suivant crée trois collections : une liste d’objets `Person`, une liste d’objets `Cat` et une liste d’objets `Dog`.  
  
 La première clause `join` dans C# met en corrélation des personnes et des chats sur la base d’un objet `Person` correspondant à `Cat.Owner`. Elle retourne une séquence de types anonymes qui contiennent l’objet `Person` et la propriété `Cat.Name`.  
  
 La deuxième clause `join` dans C# met en corrélation les types anonymes retournés par la première jointure avec les objets `Dog` de la liste de chiens fournie, sur la base d’une clé composite constituée de la propriété `Owner` de type `Person` et de la première lettre du nom de l’animal. Elle retourne une séquence de types anonymes qui contiennent les propriétés `Cat.Name` et `Dog.Name` de chaque paire correspondante. Comme il s’agit d’une jointure interne, seuls les objets de la première source de données qui ont une correspondance dans la deuxième source de données sont retournés.  
  
 [!code-cs[CsLINQProgJoining#3](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]  
  
## <a name="example"></a>Exemple  
  
## <a name="inner-join-by-using-grouped-join-example"></a>Exemple de jointure interne à l’aide d’une jointure groupée  
 L’exemple suivant montre comment implémenter une jointure interne en utilisant une jointure groupée.  
  
 Dans `query1`, la liste d’objets `Person` est jointe par groupe à la liste d’objets `Pet` sur la base de l’objet `Person` qui correspond à la propriété `Pet.Owner`. La jointure groupée crée une collection de groupes intermédiaires où chaque groupe se compose d’un objet `Person` et d’une séquence d’objets `Pet` correspondants.  
  
 En ajoutant une deuxième clause `from` à la requête, cette séquence de séquences est combinée (ou aplatie) dans une séquence plus longue. Le type des éléments de la séquence finale est spécifié par la clause `select`. Dans cet exemple, ce type est un type anonyme qui se compose des propriétés `Person.FirstName` et `Pet.Name` pour chaque paire correspondante.  
  
 Le résultat de `query1` est équivalent au jeu de résultats qui aurait été obtenu en utilisant la clause `join` sans la clause `into` pour effectuer une jointure interne. La variable `query2` illustre cette requête équivalente.  
  
 [!code-cs[CsLINQProgJoining#4](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Effectuer des jointures groupées](perform-grouped-joins.md)   
 [Effectuer des jointures externes gauches](perform-left-outer-joins.md)   
 [Types anonymes](../programming-guide/classes-and-structs/anonymous-types.md)   
 
