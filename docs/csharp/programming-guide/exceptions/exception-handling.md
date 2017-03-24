---
title: "Gestion des exceptions (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "gestion d'exceptions (C#), à propos de la gestion d'exceptions"
  - "exceptions (C#), gérer"
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# Gestion des exceptions (Guide de programmation C#)
Un bloc [try](../../../csharp/language-reference/keywords/try-catch.md) est utilisé par les programmeurs en C\# pour partitionner un code susceptible d'être affecté par une exception.  Les blocs [catch](../../../csharp/language-reference/keywords/try-catch.md) associés sont utilisés pour gérer toutes les exceptions obtenues.  Un bloc [finally](../../../csharp/language-reference/keywords/try-finally.md) contient du code exécuté, qu'une exception soit lancée ou non dans le bloc `try`, par exemple la libération de ressources allouées dans le bloc `try`.  Un bloc `try` requiert un ou plusieurs blocs `catch` ou un bloc `finally`, ou bien les deux.  
  
 Les exemples suivants montrent une instruction `try-catch`, une instruction `try-finally` et une instruction `try-catch-finally`.  
  
 [!code-cs[csProgGuideExceptions#6](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_1.cs)]  
  
 [!code-cs[csProgGuideExceptions#7](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_2.cs)]  
  
 [!code-cs[csProgGuideExceptions#8](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_3.cs)]  
  
 Un bloc `try` sans bloc `catch` ou `finally` entraîne une erreur de compilateur.  
  
## Blocs Catch  
 Un bloc `catch` peut spécifier un type d'exception à intercepter.  La spécification de type est appelée *filtre d'exception*.  Le type d'exception doit être dérivé de <xref:System.Exception>.  En règle générale, ne spécifiez pas <xref:System.Exception> en tant que filtre d'exceptions, à moins que vous ne sachiez gérer toutes les exceptions qui peuvent être levées dans le bloc `try` ou que vous n'ayez inclus une instruction [throw](../../../csharp/language-reference/keywords/throw.md) à la fin du bloc `catch`.  
  
 Plusieurs blocs `catch` avec les filtres d'exception différents peuvent être enchaînés.  Les blocs `catch` sont évalués de haut en bas dans votre code, mais un seul bloc `catch` est exécuté pour chaque exception qui est levée.  Le premier bloc `catch` qui spécifie le type exact ou une classe de base de l'exception levée sera exécutée.  Si aucun bloc `catch` ne spécifie de filtre d'exception correspondant, un bloc `catch` sans filtre est sélectionné, s'il en existe un dans l'instruction.  Il est important de placer les blocs `catch` avec les types d'exception les plus spécifiques, c'est\-à\-dire les plus dérivées en premier.  
  
 Vous devez intercepter des exceptions lorsque les conditions suivantes sont remplies :  
  
-   Vous avez une bonne compréhension de la raison pour laquelle l'exception peut être levée, et vous pouvez implémenter une récupération spécifique, par exemple inviter l'utilisateur à entrer un nouveau nom de fichier lorsque vous interceptez un objet <xref:System.IO.FileNotFoundException>.  
  
-   Vous pouvez créer et lever une exception nouvelle, plus spécifique.  
  
     [!code-cs[csProgGuideExceptions#9](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_4.cs)]  
  
-   Vous voulez traiter partiellement une exception avant de la transmettre en vue d'un traitement supplémentaire.  Dans l'exemple suivant, un bloc `catch` est utilisé pour ajouter une entrée à un journal d'erreurs avant de lever à nouveau une exception.  
  
     [!code-cs[csProgGuideExceptions#10](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_5.cs)]  
  
## Blocs Finally  
 Un bloc `finally` vous permet de nettoyer les actions exécutées dans un bloc `try`.  S'il est présent, le bloc `finally` s'exécute en dernier, après le bloc `try` et tout bloc `catch` correspondant.  Un bloc `finally` est toujours exécuté, indépendamment de si une exception est levée ou si un bloc `catch` correspondant au type d'exception est trouvé.  
  
 Le bloc `finally` permet de libérer les ressources telles que flux fichier, connexions de bases de données et handles graphiques, sans attendre le garbage collector dans le runtime pour finaliser les objets.  Consultez [using, instruction](../../../csharp/language-reference/keywords/using-statement.md) pour plus d'informations.  
  
 Dans l'exemple suivant, le bloc `finally` est utilisé pour fermer un fichier ouvert dans le bloc `try`.  Remarquez que l'état du handle de fichier est vérifié avant que le fichier soit fermé.  Si le bloc `try` ne peut pas ouvrir le fichier, le handle de fichier a encore la valeur `null` et le bloc `finally` ne tente pas de le fermer.  Ou bien, si le fichier est ouvert avec succès dans le bloc `try`, le bloc `finally` ferme le fichier ouvert.  
  
 [!code-cs[csProgGuideExceptions#11](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_6.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)   
 [using, instruction](../../../csharp/language-reference/keywords/using-statement.md)