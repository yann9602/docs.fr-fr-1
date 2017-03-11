---
redirect_url: /dotnet/articles/csharp/linq/order-the-results-of-a-join-clause
caps.handback.revision: 6
---
# Comment&#160;: classer les r&#233;sultats d&#39;une clause Join (Guide de programmation&#160;C#)
Cet exemple indique comment classer les résultats d'une opération de jointure.  Notez que le classement est exécuté après la jointure.  Bien que vous puissiez utiliser une clause `orderby` avec l'une ou plusieurs des séquences sources avant la jointure, nous ne le recommandons généralement pas.  Certains fournisseurs [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] ne peuvent pas conserver ce classement après la jointure.  
  
## Exemple  
 Cette requête crée une jointure de groupe, puis classe les groupes selon l'élément de catégorie, qui est encore dans la portée.  À l'intérieur de l'initialiseur de type anonyme, une sous\-requête classe tous les éléments correspondants à partir de la séquence de produits.  
  
 [!code-cs[csProgGuideLINQ#81](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#81)]  
  
## Compilation du code  
  
-   Créez un projet [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] qui cible la version 3.5 du .NET Framework.  Par défaut, le projet possède une référence à System.Core.dll et une directive `using` pour l'espace de noms System.Linq.  
  
-   Copiez le code dans votre projet.  
  
-   Appuyez sur F5 pour compiler et exécuter le programme.  
  
-   Appuyez sur une touche pour quitter la fenêtre de console.  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [orderby, clause](../../../csharp/language-reference/keywords/orderby-clause.md)   
 [join, clause](../../../csharp/language-reference/keywords/join-clause.md)   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)