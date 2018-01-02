---
title: Exceptions et gestion des exceptions (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 458f6770a89f28dce1e441cd38ec9a56a1c58bc1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Exceptions et gestion des exceptions (Guide de programmation C#)
Les fonctionnalités de gestion des exceptions du langage C# vous aident à gérer les situations inattendues ou exceptionnelles qui se produisent lorsqu’un programme est en cours d’exécution. La gestion des exceptions utilise les mots clés `try`, `catch` et `finally` pour tenter des actions susceptibles de ne pas réussir, pour gérer les défaillances lorsque vous pensez que c’est justifié et pour nettoyer ensuite les ressources. Les exceptions peuvent être générées par le common language runtime (CLR), par .NET Framework ou des bibliothèques tierces, ou par le code de l’application. Les exceptions sont créées avec le mot clé `throw`.  
  
 Dans de nombreux cas, une exception peut être levée non pas par une méthode appelée directement par votre code, mais par une autre méthode plus loin dans la pile des appels. Dans ce cas, le CLR déroule la pile à la recherche d’une méthode avec un bloc `catch` pour le type d’exception concerné et exécute le premier bloc `catch` de ce type qu’il trouve. S’il ne trouve pas de bloc `catch` dans la pile des appels, il termine le processus et affiche un message à l’utilisateur.  
  
 Dans cet exemple, une méthode teste la division par zéro et intercepte l’erreur. Sans la gestion des exceptions, ce programme se terminerait avec une erreur **DivideByZeroException non gérée**.  
  
 [!code-csharp[csProgGuideExceptions#18](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exceptions-and-exception-handling_1.cs)]  
  
## <a name="exceptions-overview"></a>Vue d’ensemble des exceptions  
 Les exceptions ont les propriétés suivantes :  
  
-   Les exceptions sont des types qui dérivent tous en définitive de `System.Exception`.  
  
-   Utilisez un bloc `try` autour des instructions qui peuvent lever des exceptions.  
  
-   Dès qu’une exception se produit dans le bloc `try`, le flux de contrôle passe immédiatement au premier gestionnaire d’exceptions associé présent dans la pile des appels. En C#, le mot clé `catch` est utilisé pour définir un gestionnaire d’exceptions.  
  
-   Si aucun gestionnaire d’exceptions n’est présent pour une exception donnée, le programme s’arrête avec un message d’erreur.  
  
-   N’interceptez pas d’exception si vous ne pouvez pas la gérer tout en laissant l’application dans un état connu. Si vous interceptez `System.Exception`, levez-la de nouveau avec le mot clé `throw` à la fin du bloc `catch`.  
  
-   Si un bloc `catch` définit une variable d’exception, vous pouvez l’utiliser pour obtenir plus d’informations sur le type d’exception qui s’est produit.  
  
-   Les exceptions peuvent être générées explicitement par un programme avec le mot clé `throw`.  
  
-   Les objets Exception contiennent des informations détaillées sur l'erreur, telles que l'état de la pile des appels et une description du texte de l'erreur.  
  
-   Le code qui se trouve dans un bloc `finally` est exécuté même si une exception est levée. Utilisez un bloc `finally` pour libérer des ressources, par exemple pour fermer tous les flux ou fichiers qui ont été ouverts dans le bloc `try`.  
  
-   Les exceptions gérées dans .NET Framework sont implémentées au-dessus du mécanisme de gestion structurée des exceptions de Win32. Pour plus d’informations, consultez les pages [Gestion structurée des exceptions (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) et [Cours intensif sur la gestion structurée des exceptions de Win32](http://go.microsoft.com/fwlink/?LinkId=119654).  
  
## <a name="related-sections"></a>Rubriques connexes  
 Consultez les rubriques suivantes pour plus d’informations sur les exceptions et la gestion des exceptions :  
  
-   [Utilisation d’exceptions](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [Gestion des exceptions](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [Création et levée d’exceptions](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [Exceptions générées par le compilateur](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [Guide pratique : gérer une exception à l’aide de try/catch (Guide de programmation C#)](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
-   [Comment : exécuter le code de nettoyage à l’aide de finally](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.SystemException>  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [throw](../../../csharp/language-reference/keywords/throw.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)  
 [Exceptions](../../../standard/exceptions/index.md)  
 [Hiérarchie des exceptions](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)  
 [Écriture de code .NET fiable](http://go.microsoft.com/fwlink/?LinkId=112400)  
 [Minidumps pour exceptions spécifiques](http://go.microsoft.com/fwlink/?LinkId=112408)
