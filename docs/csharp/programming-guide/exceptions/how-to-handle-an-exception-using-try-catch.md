---
title: "Comment&#160;: g&#233;rer une exception &#224; l&#39;aide de try/catch (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "gestion d'exceptions (C#), try/catch (blocs)"
  - "exceptions (C#), try/catch (blocs)"
  - "try/catch (blocs C#)"
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# Comment&#160;: g&#233;rer une exception &#224; l&#39;aide de try/catch (Guide de programmation C#)
Le but d'un bloc [try\-catch](../../../csharp/language-reference/keywords/try-catch.md) est d'intercepter et de gérer une exception générée par un code actif.  Certaines exceptions peuvent être gérées dans un bloc `catch` et le problème résolu sans que l'exception soit levée à nouveau. Toutefois, le plus souvent, la seule chose que vous pouvez faire est de veiller à ce que l'exception appropriée soit levée.  
  
## Exemple  
 Dans cet exemple, <xref:System.IndexOutOfRangeException> n'est pas l'exception la plus appropriée : <xref:System.ArgumentOutOfRangeException> a de plus de sens pour la méthode parce que l'erreur est provoquée par l'argument `index` passé par l'appelant.  
  
 [!code-cs[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/csharp/how-to-handle-an-excepti_1.cs)]  
  
## Commentaires  
 Le code qui provoque une exception est joint dans le bloc `try`.  Une instruction `catch` est ajoutée immédiatement après pour gérer `IndexOutOfRangeException`, si elle se produit.  Le bloc `catch` gère l'`IndexOutOfRangeException` et lève à la place l'exception plus appropriée `ArgumentOutOfRangeException`.  Pour fournir à l'appelant autant d'informations que possible, pensez à spécifier l'exception d'origine comme <xref:System.Exception.InnerException%2A> de la nouvelle exception.  Comme la propriété <xref:System.Exception.InnerException%2A> a pour valeur [readonly](../../../csharp/language-reference/keywords/readonly.md), vous devez l'assigner dans le constructeur de la nouvelle exception.  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [Gestion des exceptions](../../../csharp/programming-guide/exceptions/exception-handling.md)