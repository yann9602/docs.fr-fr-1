---
title: "throw (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-03-02"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "throw"
  - "throw_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "throw (mot clé C#)"
  - "throw (instruction C#)"
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
caps.handback.revision: 22
---
# throw (r&#233;f&#233;rence C#)
L'instruction `throw` sert à signaler la présence d'une situation anormale \(exception\) pendant l'exécution du programme.  
  
## Notes  
 L'exception levée est un objet dont la classe est dérivée de <xref:System.Exception?displayProperty=fullName>, comme illustré dans l'exemple suivant.  
  
```  
class MyException : System.Exception {}  
// ...  
throw new MyException();  
```  
  
 L'instruction `throw` est généralement utilisée avec des instructions `try-catch` ou `try-finally`.  Une instruction [throw](../../../csharp/language-reference/keywords/throw.md) peut être utilisée dans un bloc `catch` pour lever une nouvelle fois l'exception interceptée par le bloc `catch`.  Dans ce cas, l'instruction [throw](../../../csharp/language-reference/keywords/throw.md) ne prend pas d'opérande d'exception.  Pour plus d'informations et d'exemples, consultez [try\-catch](../../../csharp/language-reference/keywords/try-catch.md) et [Comment : lever explicitement des exceptions](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md).  
  
## Exemple  
 Cet exemple illustre la méthode de levée d'une exception avec l'instruction `throw`.  
  
 [!code-cs[csrefKeywordsExceptions#5](../../../csharp/language-reference/keywords/codesnippet/csharp/throw_1.cs)]  
  
## Exemple de code  
 Consultez les exemples dans [try\-catch](../../../csharp/language-reference/keywords/try-catch.md) et [Comment : lever explicitement des exceptions](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [Les instructions try, catch et throw en C\+\+](../../../csharp/language-reference/keywords/try-catch.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Instructions de gestion des exceptions](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [Comment : lever explicitement des exceptions](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)