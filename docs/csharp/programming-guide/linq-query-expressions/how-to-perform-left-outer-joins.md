---
redirect_url: /dotnet/articles/csharp/linq/perform-left-outer-joins
caps.handback.revision: 23
---
# Proc&#233;dures&#160;: effectuer des jointures externes gauches (Guide de programmation&#160;C#)
Une jointure externe gauche est une jointure dans laquelle chaque élément de la première collection est retourné, indépendamment, le cas échéant, des éléments corrélés dans la deuxième collection.  Vous pouvez utiliser [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] pour effectuer une jointure externe gauche en appelant la méthode d' <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> sur les résultats d'une jointure groupée.  
  
## Exemple  
 L'exemple suivant montre comment utiliser la méthode <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> sur les résultats d'une jointure groupée pour effectuer une jointure externe gauche.  
  
 La première étape pour produire une jointure externe gauche de deux collections consiste à effectuer une jointure interne en utilisant une jointure groupée.  Consultez [Comment : effectuer des jointures internes](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md) pour obtenir une explication de ce processus. Dans cet exemple, la liste d'objets d' `Person` INNER\- est attachée à la liste d'objets d' `Pet` sur un objet d' `Person` qui correspond à `Pet.Owner`.  
  
 La deuxième étape consiste à inclure chaque élément de la première collection \(gauche\) dans le jeu de résultats même si cet élément n'a aucune correspondance dans la collection de droite.  Cela est accompli en appelant <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> sur chaque séquence d'éléments correspondants de la jointure groupée.  Dans cet exemple, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> est appelé à chaque séquence de correspondre à des objets d' `Pet` .  La méthode retourne une collection qui contient un seul, valeur par défaut si la séquence de correspondre à des objets d' `Pet` est vide pour tout objet d' `Person`, garantissant ainsi que chaque objet d' `Person` est représenté dans la collection de résultats.  
  
> [!NOTE]
>  La valeur par défaut pour un type référence est `null`; par conséquent, l'exemple vérifie une référence null avant d'accéder à chaque élément de chaque collection d' `Pet` .  
  
 [!code-cs[CsLINQProgJoining#7](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-left-outer-joins_1.cs)]  
  
## Compilation du code  
  
-   Créez un projet d'application console dans [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)].  
  
-   Ajoutez une référence à System.Core.dll si elle n'est pas déjà référencée.  
  
-   Incluez l'espace de noms <xref:System.Linq>.  
  
-   Copiez et collez le code de l'exemple dans le fichier program.cs, sous la méthode d' `Main` dans la classe d' `Program` .  Ajoutez une ligne de code à la méthode d' `Main` pour appeler la méthode d' `LeftOuterJoinExample` .  
  
-   Exécutez le programme.  
  
## Voir aussi  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [Comment : effectuer des jointures internes](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [Comment : effectuer des jointures groupées](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)