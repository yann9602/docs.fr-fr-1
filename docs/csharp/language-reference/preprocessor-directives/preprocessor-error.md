---
title: "#error (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#error"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#error (directive C#)"
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
caps.latest.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 10
---
# #error (r&#233;f&#233;rence C#)
`#error` vous permet de générer une erreur à partir d'un point spécifique de votre code.  Par exemple :  
  
```  
#error Deprecated code in this method.  
```  
  
## Notes  
 `#error` est couramment utilisé dans les directives conditionnelles.  
  
 Il est également possible de générer un avertissement défini par l'utilisateur à l'aide de [\#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).  
  
## Exemple  
  
```  
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C\#](../../../csharp/language-reference/preprocessor-directives/index.md)