---
title: "#undef (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#undef"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#undef (directive C#)"
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #undef (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#undef` vous permet d'annuler la définition d'un symbole, de sorte qu'en utilisant le symbole en tant qu'expression dans une directive [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), l'expression corresponde à `false`.  
  
 Un symbole peut être défini à l'aide de la directive [\#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) ou de l'option de compilation [\/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md).  La directive `#undef` doit apparaître dans le fichier avant que vous utilisiez des instructions qui ne soient pas non plus des directives.  
  
## Exemple  
  
```  
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass   
{  
    static void Main()   
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```  
  
  **Le DÉBOGAGE n'est pas défini**   
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C\#](../../../csharp/language-reference/preprocessor-directives/index.md)