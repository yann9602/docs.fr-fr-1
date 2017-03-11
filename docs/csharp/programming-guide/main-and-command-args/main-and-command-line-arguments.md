---
redirect_url: /dotnet/articles/csharp/programming-guide/main-and-command-args/
caps.handback.revision: 30
---
# Main() et arguments de ligne de commande (Guide de programmation&#160;C#)
La méthode `Main` est le point d'entrée d'une application Windows ou d'une application console C\#.  \(Les bibliothèques et les services ne requièrent pas de méthode `Main` comme point d'entrée.\)  Une fois l'application lancée, la méthode `Main` est la première appelée.  
  
 Il ne peut y avoir qu'un seul point d'entrée dans un programme C\#.  Si plusieurs classes comportent une méthode `Main`, vous devez compiler votre programme avec l'option de compilateur **\/main** pour spécifier la méthode `Main` à utiliser comme point d'entrée.  Pour plus d'informations, consultez [\/main \(Specify Location of Main Method\)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).  
  
 [!code-cs[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/main-and-command-line-ar_1.cs)]  
  
## Vue d'ensemble  
  
-   La méthode `Main` représente le point d'entrée d'un programme .exe ; il s'agit de l'endroit où le contrôle du programme commence et se termine.  
  
-   La méthode `Main` est déclarée dans une classe ou un struct.  `Main` doit être [statique](../../../csharp/language-reference/keywords/static.md) et il ne doit pas être [public](../../../csharp/language-reference/keywords/public.md).  \(Dans l'exemple précédent, il reçoit l'accès par défaut : l'accès [privé](../../../csharp/language-reference/keywords/private.md).\) La classe ou le struct englobant n'a pas besoin d'être statique.  
  
-   `Main` peut avoir un retour de type `void` ou `int`.  
  
-   La méthode `Main` peut être déclarée avec ou sans paramètre `string[]` contenant des arguments de ligne de commande.  Lorsque vous utilisez [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] pour créer des applications Windows Forms, vous pouvez ajouter le paramètre manuellement ou utiliser la classe <xref:System.Environment> pour obtenir les arguments de ligne de commande.  Les paramètres sont lus comme arguments de ligne de commande nulle indexés. Contrairement à C et de C\+\+, le nom du programme n'est pas traité comme premier argument de ligne de commande.  
  
## Dans cette section  
  
-   [Arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
  
-   [Comment : afficher les arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
  
-   [Comment : accéder à des arguments de ligne de commande à l'aide de foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
  
-   [Valeurs de retour Main\(\)](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [À l'intérieur d'un programme C\#](../../../csharp/programming-guide/inside-a-program/index.md)   
 [\<paveover\>C\# Sample Applications](http://msdn.microsoft.com/fr-fr/9a9d7aaa-51d3-4224-b564-95409b0f3e15)