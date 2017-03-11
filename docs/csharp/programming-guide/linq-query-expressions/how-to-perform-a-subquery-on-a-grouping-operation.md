---
redirect_url: /dotnet/articles/csharp/linq/perform-a-subquery-on-a-grouping-operation
caps.handback.revision: 15
---
# Comment&#160;: effectuer une sous-requ&#234;te sur une op&#233;ration de regroupement (Guide de programmation&#160;C#)
Cette rubrique présente deux façons différentes de créer une requête qui organise les données sources en groupes, puis effectue une sous\-requête sur chaque groupe individuellement.  La technique de base dans chaque exemple est de grouper les éléments source en utilisant une *continuation* nommée `newGroup`, puis de générer ensuite une nouvelle sous\-requête sur `newGroup`.  Cette sous\-requête est exécutée sur chaque nouveau groupe créé par la requête externe.  Notez que dans cet exemple particulier, la sortie définitive n'est pas un groupe mais une séquence en deux dimensions de types anonymes.  
  
 Pour plus d'informations sur la manière de grouper, consultez [group, clause](../../../csharp/language-reference/keywords/group-clause.md).  
  
 Pour plus d'informations sur les continuations, consultez [into](../../../csharp/language-reference/keywords/into.md).  L'exemple suivant utilise une structure de données en mémoire comme source de données, mais les mêmes principes s'appliquent à tout type de source de données [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)].  
  
## Exemple  
 [!code-cs[csProgGuideLINQ#23](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#23)]  
  
## Compilation du code  
 Cet exemple contient des références aux objets définis dans l'exemple d'application dans [Comment : interroger une collection d'objets](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md).  Pour compiler et exécuter cette méthode, collez\-la dans la classe `StudentClass` de cette application et ajoutez\-lui un appel de la méthode `Main`.  
  
 Lorsque vous adaptez cette méthode à votre propre application, souvenez\-vous que LINQ requiert la version 3.5 du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] et que le projet doit contenir une référence à System.Core.dll et une directive using pour System.Linq.  Les types LINQ to SQL, LINQ to XML et LINQ to DataSet requièrent des utilisations et des références supplémentaires.  Pour plus d'informations, consultez [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)