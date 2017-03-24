---
title: "#endif (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#endif"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#endif (directive C#)"
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
caps.latest.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 9
---
# #endif (r&#233;f&#233;rence C#)
`#endif` indique la fin d'une directive conditionnelle commencée par la directive [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).  Par exemple :  
  
```  
  
      #define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## Notes  
 Une directive conditionnelle commençant par une directive `#if` doit être terminée explicitement à l'aide d'une directive `#endif`.  Pour obtenir un exemple d'utilisation de `#endif`, consultez [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C\#](../../../csharp/language-reference/preprocessor-directives/index.md)