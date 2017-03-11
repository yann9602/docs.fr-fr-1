---
redirect_url: /dotnet/articles/csharp/linq/group-query-results
caps.handback.revision: 19
---
# Comment&#160;: regrouper les r&#233;sultats d&#39;une requ&#234;te (Guide de programmation&#160;C#)
Le regroupement est l'une des fonctions les plus puissantes de [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)].  Les exemples suivants indiquent comment grouper des données de plusieurs façons :  
  
-   Par une propriété unique.  
  
-   Par la première lettre d'une propriété de type chaîne.  
  
-   Par une plage numérique calculée.  
  
-   Par prédicat booléen ou une autre expression.  
  
-   Par une clé composée.  
  
 De plus, le deux dernières requêtes projettent leurs résultats dans un nouveau type anonyme qui contient uniquement le prénom et le nom de l'étudiant.  Pour plus d'informations, consultez [group, clause](../../../csharp/language-reference/keywords/group-clause.md).  
  
## Exemple  
 Tous les exemples de cette rubrique utilisent les classes d'assistance et sources de données suivantes.  
  
 [!code-cs[csProgGuideLINQ#15](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#15)]  
  
## Exemple  
 L'exemple suivant indique comment grouper des éléments source en utilisant une propriété unique de l'élément comme clé de groupe.  Dans ce cas, la clé est `string`, le nom de l'étudiant.  Il est également possible d'utiliser une sous\-chaîne pour la clé.  L'opération de regroupement utilise le comparateur d'égalité par défaut pour le type.  
  
 Collez la méthode suivante dans la classe `StudentClass`.  Modifiez l'instruction d'appel dans la méthode `Main` pour `sc.GroupBySingleProperty()`.  
  
 [!code-cs[csProgGuideLINQ#17](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#17)]  
  
## Exemple  
 L'exemple suivant indique comment grouper des éléments source en utilisant une méthode différente de la propriété de l'objet pour la clé de groupe.  Dans cet exemple, la clé est la première lettre du nom de l'étudiant.  
  
 Collez la méthode suivante dans la classe `StudentClass`.  Modifiez l'instruction d'appel dans la méthode `Main` pour `sc.GroupBySubstring()`.  
  
 [!code-cs[csProgGuideLINQ#18](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#18)]  
  
## Exemple  
 L'exemple suivant indique comment grouper des éléments source en utilisant une plage numérique comme clé de groupe.  La requête projette ensuite les résultats dans un type anonyme qui contient uniquement le prénom et le nom, ainsi que la plage de centiles à laquelle appartient l'étudiant.  Un type anonyme est utilisé car il n'est pas nécessaire d'utiliser l'objet `Student` complet pour afficher les résultats.  `GetPercentile` est une fonction d'assistance qui calcule un centile en fonction de la note moyenne de l'étudiant.  La méthode retourne un entier compris entre 0 et 10.  
  
 [!code-cs[csProgGuideLINQ#50](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#50)]  
  
 Collez la méthode suivante dans la classe `StudentClass`.  Modifiez l'instruction d'appel dans la méthode `Main` pour `sc.GroupByRange()`.  
  
 [!code-cs[csProgGuideLINQ#19](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#19)]  
  
## Exemple  
 L'exemple suivant indique comment grouper des éléments source à l'aide d'une expression de comparaison booléenne.  Dans cet exemple, l'expression booléenne teste si la note moyenne obtenue par un étudiant à un examen est supérieure à 75.  Comme dans les exemples précédents, les résultats sont projetés dans un type anonyme, car l'élément source complet n'est pas nécessaire.  Notez que les propriétés du type anonyme deviennent des propriétés sur le membre `Key` et sont accessibles par nom lors de l'exécution de la requête.  
  
 Collez la méthode suivante dans la classe `StudentClass`.  Modifiez l'instruction d'appel dans la méthode `Main` pour `sc.GroupByBoolean()`.  
  
 [!code-cs[csProgGuideLINQ#20](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#20)]  
  
## Exemple  
 L'exemple suivant indique comment utiliser un type anonyme pour encapsuler une clé qui contient plusieurs valeurs.  Dans cet exemple, la première valeur de la clé est la première lettre du nom de l'étudiant.  La deuxième valeur de clé est une valeur booléenne qui spécifie si l'étudiant a obtenu un score supérieur à 85 lors du premier examen.  Vous pouvez classer les groupes en fonction d'une propriété quelconque de la clé.  
  
 Collez la méthode suivante dans la classe `StudentClass`.  Modifiez l'instruction d'appel dans la méthode `Main` pour `sc.GroupByCompositeKey()`.  
  
 [!code-cs[csProgGuideLINQ#21](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#21)]  
  
## Compilation du code  
 Copiez et collez chaque méthode que vous souhaitez tester dans la classe `StudentClass`.  Ajoutez une instruction d'appel de la méthode à la méthode `Main` et appuyez sur F5.  
  
 Lorsque vous adaptez ces méthodes à votre propre application, souvenez\-vous que LINQ requiert la version 3.5 ou 4 du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] et que le projet doit contenir une référence à System.Core.dll et une directive using pour System.Linq.  Les types LINQ to SQL, LINQ to XML et LINQ to DataSet requièrent des directives using et des références supplémentaires.  Pour plus d'informations, consultez [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Voir aussi  
 <xref:System.Linq.Enumerable.GroupBy%2A>   
 <xref:System.Linq.IGrouping%602>   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [group, clause](../../../csharp/language-reference/keywords/group-clause.md)   
 [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Comment : effectuer une sous\-requête sur une opération de regroupement](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)   
 [Comment : créer un groupe imbriqué](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)   
 [Grouping Data](../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)