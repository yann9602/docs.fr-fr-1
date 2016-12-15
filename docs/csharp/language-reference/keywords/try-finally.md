---
title: "try-finally (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "finally"
  - "finally_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "finally (mot clé C#)"
  - "try-finally (instruction C#)"
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# try-finally (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

En utilisant un bloc `finally`, vous pouvez nettoyer toutes les ressources qui sont allouées dans un bloc [try](../../../csharp/language-reference/keywords/try-catch.md), et vous pouvez exécuter le code même si une exception est levée dans le bloc `try`.  En général, les instructions d'un bloc `finally` s'exécutent quand le contrôle quitte une instruction `try`.  Le transfert du contrôle peut se produire suite à une exécution normale, à l'exécution d'une instruction `break`, `continue`, `goto` ou `return`, ou à la propagation d'une exception lors de l'instruction `try`.  
  
 Dans une exception gérée, l'exécution du bloc associé `finally` est garantie.  Toutefois, si l'exception n'est pas gérée, l'exécution du bloc `finally` dépend de la façon dont l'opération de déroulement d'exception est levée.  Cela dépend ensuite de la façon dont votre ordinateur est configuré.  Pour plus d'informations, consultez [Traitement d'exceptions non gérées dans le CLR](http://go.microsoft.com/fwlink/?LinkId=128371).  
  
 Généralement, lorsqu'une exception non gérée termine une application, peu importe que le bloc `finally` soit en cours d'exécution ou pas.  Toutefois, si vous avez des instructions dans un bloc `finally` qui doivent être exécutées même dans ce cas, la solution consiste à ajouter un bloc `catch` à l'instruction `try`\-`finally`.  Vous pouvez aussi intercepter l'exception qui peut être levée dans le bloc `try` d'une instruction `try`\-`finally` plus haut dans la pile des appels.  En d'autres termes, vous pouvez intercepter l'exception dans la méthode qui appelle la méthode contenant l'instruction `try`\-`finally`, ou dans la méthode qui appelle cette méthode, ou dans n'importe quelle méthode de la pile des appels.  Si l'exception n'est pas interceptée, l'exécution du bloc `finally` varie selon que le système d'exploitation choisit de déclencher une opération de déroulement d'exception.  
  
## Exemple  
 Dans l'exemple suivant, une instruction de conversion non valide entraîne la levée d'une exception `System.InvalidCastException`.  L'exception est non gérée.  
  
 [!code-cs[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 Dans l'exemple suivant, une exception de la méthode `TryCast` est interceptée dans une méthode située plus haut dans la pile des appels.  
  
 [!code-cs[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 Pour plus d'informations sur `finally`, consultez [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
 C\# contient également l'[instruction Using](../../../csharp/language-reference/keywords/using-statement.md), qui fournit des fonctionnalités similaires pour les objets <xref:System.IDisposable> dans une syntaxe pratique.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Instructions try, throw et catch \(C\+\+\)](/visual-cpp/cpp/try-throw-and-catch-statements-cpp)   
 [Instructions de gestion des exceptions](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [Comment : lever explicitement des exceptions](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)