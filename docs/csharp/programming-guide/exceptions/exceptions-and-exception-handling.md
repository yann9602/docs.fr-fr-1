---
redirect_url: /dotnet/articles/csharp/programming-guide/exceptions/
caps.handback.revision: 33
---
# Exceptions et gestion des exceptions (Guide de programmation&#160;C#)
Les fonctionnalités de gestion des exceptions du langage C\# vous aident à gérer les situations inattendues ou exceptionnelles qui surviennent pendant l'exécution d'un programme.  La gestion des exceptions utilise les mots clés `try`, `catch` et `finally` pour tenter des actions susceptibles de ne pas réussir, pour gérer les défaillances lorsque vous pensez que c'est justifié et pour nettoyer les ressources après.  Les exceptions peuvent être générées par le Common Language Runtime \(CLR\), par le .NET Framework ou des bibliothèques tierces ou par le code d'application.  Les exceptions sont créées à l'aide du mot clé `throw`.  
  
 Dans de nombreux cas, une exception peut être levée non par une méthode que votre code a appelée directement, mais par une autre méthode plus bas dans la pile des appels.  Lorsque cela arrive, le CLR déroule la pile à la recherche d'une méthode comportant un bloc `catch` pour le type d'exception spécifique et il exécute le premier bloc `catch` qu'il trouve.  S'il ne trouve aucun bloc `catch` approprié dans la pile des appels, il arrête le processus et affiche un message destiné à l'utilisateur.  
  
 Dans cet exemple, une méthode teste une division par zéro et intercepte l'erreur.  Sans la gestion des exceptions, ce programme se terminerait sur une erreur **L'exception DivideByZeroException n'a pas été gérée**.  
  
 [!code-cs[csProgGuideExceptions#18](../../../csharp/programming-guide/exceptions/codesnippet/csharp/exceptions-and-exception_1.cs)]  
  
## Vue d'ensemble des exceptions  
 Les exceptions ont les propriétés suivantes :  
  
-   Les exceptions sont des types qui dérivent en définitive tous de `System.Exception`.  
  
-   Délimitez toute instruction susceptible de lever des exceptions par un bloc `try`.  
  
-   Lorsqu'une exception se produit dans le bloc `try`, le flux de contrôle est immédiatement transmis au premier gestionnaire d'exceptions associé présent dans la pile des appels.  En C\#, le mot clé `catch` est utilisé pour définir un gestionnaire d'exceptions.  
  
-   Si aucun gestionnaire d'exceptions pour une exception donnée n'est présent, le programme cesse de s'exécuter avec un message d'erreur.  
  
-   Interceptez uniquement les exceptions que vous pouvez gérer tout en laissant l'application dans un état connu.  Si vous interceptez une `System.Exception`, levez\-la de nouveau à l'aide du mot clé `throw` à la fin du bloc `catch`.  
  
-   Si un bloc `catch` définit une variable d'exception, vous pouvez l'utiliser pour obtenir plus d'informations sur le type d'exception qui s'est produit.  
  
-   Les exceptions peuvent être générées explicitement par un programme à l'aide du mot clé `throw`.  
  
-   Les objets Exception contiennent des informations détaillées à propos de l'erreur, telles que l'état de la pile des appels et une description du texte de l'erreur.  
  
-   Le code figurant dans les blocs `finally` est exécuté même si une exception est levée.  Utilisez un bloc `finally` pour libérer des ressources, notamment pour fermer tous les flux ou fichiers qui ont été ouverts dans le bloc `try`.  
  
-   Les exceptions managées dans le .NET Framework sont implémentées par dessus le mécanisme de gestion structurée des exceptions Win32.  Pour plus d'informations, consultez [Gestion structurée des exceptions](/visual-cpp/cpp/structured-exception-handling-c-cpp) et [A Crash Course on the Depths of Win32 Structured Exception Handling](http://go.microsoft.com/fwlink/?LinkId=119654).  
  
## Rubriques connexes  
 Consultez les rubriques suivantes pour plus d'informations sur les exceptions et la gestion des exceptions :  
  
-   [Utilisation d'exceptions](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [Gestion des exceptions](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [Création et levée d'exceptions](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [Exceptions générées par le compilateur](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [Comment : gérer une exception à l'aide de try\/catch](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
-   [Comment : exécuter le code de nettoyage à l'aide de finally](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 <xref:System.SystemException>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)   
 [Exceptions](../Topic/Handling%20and%20Throwing%20Exceptions.md)   
 [Hiérarchie des exceptions](../Topic/Exception%20Hierarchy.md)   
 [Écriture de code fiable .NET](http://go.microsoft.com/fwlink/?LinkId=112400)   
 [Minidumps pour des exceptions spécifiques](http://go.microsoft.com/fwlink/?LinkId=112408)