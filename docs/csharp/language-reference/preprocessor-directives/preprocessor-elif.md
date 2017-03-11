---
title: "#elif (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#elif"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#elif (directive C#)"
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# #elif (r&#233;f&#233;rence C#)
`#elif` vous permet de créer une directive conditionnelle composée.  L'expression `#elif` est évaluée si aucune des expressions précédentes [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), ni aucune des directives précédentes `#elif` facultatives ne correspond à `true`.  Si une expression `#elif` correspond à `true`, le compilateur évalue l'ensemble du code compris entre `#elif` et la directive conditionnelle suivante.  Par exemple :  
  
```  
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 Vous pouvez utiliser les opérateurs `==` \(égalité\), `!=` \(inégalité\), `&&` \(et\) et `||` \(ou\) pour évaluer plusieurs symboles.  Vous pouvez aussi grouper des symboles et des opérateurs à l'aide de parenthèses.  
  
## Notes  
 `#elif` équivaut à utiliser :  
  
```  
#else  
#if  
```  
  
 `#elif` est plus simple à utiliser, car chaque directive `#if` requiert une directive [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), tandis que `#elif` peut être utilisé sans `#endif`.  
  
 Pour obtenir un exemple d'utilisation de `#elif`, consultez [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C\#](../../../csharp/language-reference/preprocessor-directives/index.md)