---
redirect_url: /dotnet/articles/csharp/linq/return-a-query-from-a-method
caps.handback.revision: 11
---
# Comment&#160;: retourner une requ&#234;te &#224; partir d&#39;une m&#233;thode (Guide de programmation&#160;C#)
Cet exemple indique comment retourner une requête à partir d'une méthode comme valeur de retour et en tant que paramètre `out`.  
  
 Toute requête doit avoir un type de <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, ou un type dérivé tel que <xref:System.Linq.IQueryable%601>.  Par conséquent, toute valeur de retour ou paramètre `out` d'une méthode qui retourne une requête doit également avoir ce type.  Si une méthode matérialise une requête dans un type <xref:System.Collections.Generic.List%601> concret ou un type <xref:System.Array>, il est considéré comme retournant les résultats de la requête au lieu de la requête elle\-même.  Une variable de requête retournée à partir d'une méthode peut néanmoins être composée ou modifiée.  
  
## Exemple  
 Dans l'exemple suivant, la première méthode retourne une requête comme valeur de retour et la seconde méthode retourne une requête comme paramètre `out` .  Notez que dans les deux cas, c'est une requête qui est retournée, et non des résultats de requête.  
  
 [!code-cs[csProgGuideLINQ#80](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#80)]  
  
## Compilation du code  
  
-   Créez un projet [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] qui cible la version 3.5 ou une version ultérieure de .NET Framework.  Par défaut, le projet possède une référence à System.Core.dll et une directive `using` pour l'espace de noms System.Linq.  
  
-   Remplacez la classe par le code dans l'exemple.  
  
-   Appuyez sur F5 pour compiler et exécuter le programme.  
  
-   Appuyez sur une touche pour quitter la fenêtre de console.  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)