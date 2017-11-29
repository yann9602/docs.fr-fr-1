---
title: "Guide pratique pour exécuter le code de nettoyage à l'aide de finally (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 682a40bfde47a33dd192d525037ed38f59edf107
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Guide pratique pour exécuter le code de nettoyage à l'aide de finally (Guide de programmation C#)
L’objectif d’une instruction `finally` est de vérifier que le nettoyage nécessaire des objets, généralement ceux contenant des ressources externes, se produit immédiatement, même si une exception est levée. Un exemple de nettoyage de ce type est l’appel à <xref:System.IO.Stream.Close%2A> sur un <xref:System.IO.FileStream> immédiatement après son utilisation au lieu d’attendre que l’objet soit récupéré par garbage collection par le Common Language Runtime, comme suit :  
  
 [!code-csharp[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## <a name="example"></a>Exemple  
 Pour transformer le code précédent en instruction `try-catch-finally`, le code de nettoyage est séparé du code actif comme suit.  
  
 [!code-csharp[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 Comme une exception peut se produire à tout moment dans le bloc `try` avant l’appel à `OpenWrite()`, ou comme l’appel `OpenWrite()` lui-même peut échouer, nous n’avons aucune garantie que le fichier est ouvert quand nous essayons de le fermer. Le bloc `finally` ajoute un contrôle pour garantir que l’objet <xref:System.IO.FileStream> n’est pas `null` avant d’appeler la méthode <xref:System.IO.Stream.Close%2A>. Sans le contrôle `null`, le bloc `finally` pourrait lever sa propre <xref:System.NullReferenceException>, mais la levée d’exceptions dans des blocs `finally` doit être évitée, dans la mesure du possible.  
  
 Une connexion de base de données est également susceptible d’être fermée dans un bloc `finally`. Le nombre de connexions à un serveur de base de données étant parfois limité, vous devez fermer les connexions de base de données le plus rapidement possible. Si une exception est levée avant que vous puissiez fermer votre connexion, c’est un autre cas où il vaut mieux utiliser le bloc `finally` qu’attendre le nettoyage de la mémoire.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/index.md)  
 [Gestion des exceptions](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [using, instruction](../../../csharp/language-reference/keywords/using-statement.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
