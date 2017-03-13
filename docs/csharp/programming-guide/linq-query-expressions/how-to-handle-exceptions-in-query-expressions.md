---
redirect_url: /dotnet/articles/csharp/linq/handle-exceptions-in-query-expressions
caps.handback.revision: 15
---
# Comment&#160;: g&#233;rer des exceptions dans des expressions de requ&#234;te (Guide de programmation&#160;C#)
Il est possible d'appeler n'importe quelle méthode dans le contexte d'une expression de requête.  Toutefois, nous vous recommandons d'éviter d'appeler n'importe quelle méthode dans une expression de requête qui peut créer un effet secondaire comme la modification du contenu de la source de données ou la levée d'une exception.  Cet exemple indique comment éviter de lever des exceptions lorsque vous appelez des méthodes dans une expression de requête sans violer les indications générales du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] sur la gestion des exceptions.  Ces indications déclarent qu'il est acceptable d'intercepter une exception spécifique lorsque vous comprenez pourquoi elle sera levée dans un contexte donné.  Pour plus d'informations, consultez [Meilleures pratiques pour les exceptions](../Topic/Best%20Practices%20for%20Exceptions.md).  
  
 Le dernier exemple indique comment gérer ces cas lorsque vous devez lever une exception pendant l'exécution d'une requête.  
  
## Exemple  
 L'exemple suivant indique comment déplacer le code de gestion des exceptions à l'extérieur d'une expression de requête.  C'est possible uniquement lorsque la méthode ne dépend d'aucune variable locale de la requête.  
  
 [!code-cs[csProgGuideLINQ#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## Exemple  
 Dans certains cas, la meilleure réponse à une exception levée depuis l'intérieur d'une requête peut être d'arrêter immédiatement l'exécution de la requête.  L'exemple suivant indique comment gérer des exceptions qui peuvent être levées depuis l'intérieur d'un corps de requête.  Supposez que `SomeMethodThatMightThrow` peut potentiellement lever une exception qui requiert l'arrêt de l'exécution de la requête.  
  
 Notez que le bloc `try` englobe la boucle `foreach` et pas la requête elle\-même.  Cela est dû au fait que la boucle `foreach` est le point auquel la requête est réellement exécutée.  Pour plus d'informations, consultez [Introduction to LINQ Queries \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!code-cs[csProgGuideLINQ#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  
## Compilation du code  
  
-   Créez un projet [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] qui cible la version 3.5 du .NET Framework.  Par défaut, le projet possède une référence à System.Core.dll et une directive `using` pour l'espace de noms System.Linq.  
  
-   Copiez le code dans votre projet.  
  
-   Appuyez sur F5 pour compiler et exécuter le programme.  
  
 Appuyez sur une touche pour quitter la fenêtre de console.  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)