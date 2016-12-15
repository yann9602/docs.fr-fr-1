---
title: "Comment&#160;: ex&#233;cuter le code de nettoyage &#224; l&#39;aide de finally (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "gestion d'exceptions (C#), try/finally (bloc)"
  - "exceptions (C#), try/finally (bloc)"
  - "try/finally (blocs C#)"
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: ex&#233;cuter le code de nettoyage &#224; l&#39;aide de finally (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'objectif d'une instruction `finally` est de garantir que le nettoyage nécessaire d'objets, généralement d'objets qui contiennent des ressources externes, se produise immédiatement, même en cas de levée d'exception.  Un exemple de nettoyage de ce type est d'appeler <xref:System.IO.Stream.Close%2A> sur un <xref:System.IO.FileStream> immédiatement après utilisation au lieu d'attendre que l'objet soit récupéré par garbage collection par le common language runtime, comme suit :  
  
 [!code-cs[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## Exemple  
 Pour transformer le code précédent en instruction `try-catch-finally`, le code de nettoyage est séparé du code actif, comme suit.  
  
 [!code-cs[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 Une exception pouvant arriver n'importe quand dans le bloc `try` avant l'appel à `OpenWrite()` ou l'appel `OpenWrite()` lui\-même pouvant échouer, nous n'avons aucune garantie que le fichier est ouvert lorsque nous essayons de le fermer.  Le bloc `finally` ajoute un contrôle pour s'assurer que l'objet <xref:System.IO.FileStream> n'est pas `null` avant d'appeler la méthode <xref:System.IO.Stream.Close%2A>.  Sans le contrôle `null`, le bloc `finally` peut lever sa propre <xref:System.NullReferenceException>, mais la levée d'exceptions dans des blocs `finally` doit être évitée si possible.  
  
 Une connexion à une base de données est également susceptible d'être fermée dans un bloc `finally`.  Le nombre de connexions autorisé à un serveur de base de données étant quelquefois limité, vous devez fermer les connexions de base de données aussi rapidement comme possible.  Si une exception est levée avant que vous puissiez fermer votre connexion, il est préférable d'utiliser le bloc `finally` plutôt que d'attendre le garbage collection.  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [Gestion des exceptions](../../../csharp/programming-guide/exceptions/exception-handling.md)   
 [using, instruction](../../../csharp/language-reference/keywords/using-statement.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)