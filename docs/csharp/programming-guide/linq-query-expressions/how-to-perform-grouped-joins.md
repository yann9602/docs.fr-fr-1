---
redirect_url: /dotnet/articles/csharp/linq/perform-grouped-joins
caps.handback.revision: 23
---
# Comment&#160;: effectuer des jointures group&#233;es (Guide de programmation&#160;C#)
La jointure groupée permet de produire des structures de données hiérarchiques.  Elle associe chaque élément de la première collection à un jeu d'éléments corrélés de la deuxième collection.  
  
 Par exemple, une classe ou une table de base de données relationnelle nommée Student peut contenir deux champs : Id et Name.  Une deuxième classe ou table de base de données relationnelle nommée Course peut contenir deux champs : StudentId et CourseTitle.  Une jointure groupée de ces deux sources de données, basée sur les champs Student.Id et Course.StudentId correspondants, regroupe chaque Student avec une collection d'objets Course \(qui peut être vide\).  
  
> [!NOTE]
>  Chaque élément de la première collection apparaît dans le jeu de résultats d'une jointure groupée même si des éléments corrélés sont détectés dans la deuxième collection.  Si aucun élément corrélé n'est détecté, la séquence d'éléments corrélés pour cet élément est vide.  Le sélecteur de résultat a par conséquent accès à chaque élément de la première collection.  Cela diffère du sélecteur de résultat dans une jointure non groupée, qui ne peut pas accéder aux éléments de la première collection qui n'ont pas de correspondance dans la deuxième collection.  
  
 Le premier exemple de cette rubrique vous montre comment effectuer une jointure groupée.  Le deuxième exemple vous montre comment utiliser une jointure groupée pour créer des éléments XML.  
  
## Exemple  
  
### Exemple de Group Join  
 L'exemple suivant effectue une jointure groupée d'objets de type `Person` et `Pet` basés sur `Person` qui correspond à la propriété `Pet.Owner`.  Contrairement à une jointure non groupée qui produit une paire d'éléments pour chaque correspondance, la jointure groupée produit un seul objet résultant pour chaque élément de la première collection, un objet `Person` dans cet exemple.  Les éléments correspondants de la deuxième collection, qui sont des objets `Pet` dans cet exemple, sont groupés dans une collection.  Enfin, la fonction de sélection de résultat crée un type anonyme pour chaque correspondance qui se compose de `Person.FirstName` et d'une collection d'objets `Pet`.  
  
 [!code-cs[CsLINQProgJoining#5](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-grouped-joins_1.cs)]  
  
## Exemple  
  
### Group Join pour créer un exemple XML  
 Les jointures groupées sont appropriées pour créer du XML à l'aide de [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)].  L'exemple suivant est semblable à l'exemple précédent mais au lieu de créer des types anonymes, la fonction de sélection de résultat crée des éléments XML qui représentent les objets joints.  Pour plus d'informations sur [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)], consultez [LINQ to XML](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 [!code-cs[CsLINQProgJoining#6](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-grouped-joins_2.cs)]  
  
## Compilation du code  
  
-   Créez un projet d'application console dans [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)].  
  
-   Ajoutez une référence à System.Core.dll et à System.Xml.Linq.dll si elles ne sont pas déjà référencées.  
  
-   Incluez les espaces de noms <xref:System.Linq> et <xref:System.Xml.Linq>.  
  
-   Copiez et collez le code à partir de l'exemple dans le fichier program.cs, sous la méthode `Main`.  Ajoutez une ligne de code à la méthode `Main` pour appeler la méthode que vous avez collée.  
  
-   Exécutez le programme.  
  
## Voir aussi  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [Comment : effectuer des jointures internes](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [Procédures : effectuer des jointures externes gauches](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [LINQ to XML](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)   
 [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)