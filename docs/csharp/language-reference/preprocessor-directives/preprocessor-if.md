---
title: "#if (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "#if"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#if (directive C#)"
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #if (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Lorsque le compilateur C\# rencontre une directive  `#if`, éventuellement suivie d'une directive [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), il compilera uniquement le code entre les directives si le symbole spécifié est défini.  Contrairement à C et C\+\+, vous ne pouvez pas assigner de valeur numérique à un symbole ; l'instruction \#if est Boolean en C\# et teste uniquement si le symbole a été défini ou non.  Par exemple :  
  
```  
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 Vous pouvez utiliser les opérateurs [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) \(égalité\) [\! \=](../../../csharp/language-reference/operators/not-equal-operator.md) \(inégalité\) pour tester uniquement [true](../../../csharp/language-reference/keywords/true.md) ou [false](../../../csharp/language-reference/keywords/false.md).  True signifie que le symbole est défini.  L'instruction `#if DEBUG` a la même signification que `#if (DEBUG == true)`.  Vous pouvez utiliser les opérateurs &&\(et\), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) \(ou\), et [\!](../../../csharp/language-reference/operators/logical-negation-operator.md) \(pas\) pour évaluer si plusieurs symboles définis.  Vous pouvez aussi grouper des symboles et des opérateurs à l'aide de parenthèses.  
  
## Notes  
 `#if`, ainsi que les directives[\#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [\#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [\#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) et [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md), vous permettent d'inclure ou d'exclure du code, en fonction de l'existence d'un ou plusieurs symboles.  Cela peut s'avérer utile lorsque vous compilez du code pour une version Debug ou pour une configuration spécifique.  
  
 Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`.  
  
 `#define` vous permet de définir un symbole. Si vous utilisez ce symbole comme expression passée à la directive `#if`, l'expression est évaluée `true`.  
  
 Vous pouvez également définir un symbole à l'aide de l'option de compilation [\/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md).  Vous pouvez annuler la définition d'un symbole à l'aide de [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Un symbole que vous définissez à l'aide de `/define` ou de `#define` ne crée pas de conflit avec une variable du même nom.  En conséquence, le nom d'une variable ne doit pas être passé à une directive de préprocesseur et un symbole peut être seulement évalué par une directive de préprocesseur.  
  
 La portée d'un symbole créé à l'aide de `#define` correspond au fichier dans lequel il a été défini.  
  
## Exemple  
  
```  
// preprocessor_if.cs  
#define DEBUG #define MYTEST  
using System;  
public class MyClass   
{  
    static void Main()   
    {  
#if (DEBUG && !MYTEST)  
        Console.WriteLine("DEBUG is defined");  
#elif (!DEBUG && MYTEST)  
        Console.WriteLine("MYTEST is defined");  
#elif (DEBUG && MYTEST)  
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else  
        Console.WriteLine("DEBUG and MYTEST are not defined");  
#endif  
    }  
}  
```  
  
  **Le DÉBOGAGE et les MYTEST sont définis**   
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C\#](../../../csharp/language-reference/preprocessor-directives/index.md)