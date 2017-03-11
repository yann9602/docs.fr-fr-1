---
title: "#define (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#define"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#define (directive C#)"
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# #define (r&#233;f&#233;rence C#)
Utilisez `#define` pour définir un symbole.  Lorsque vous utilisez ce symbole comme expression passée à la directive [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), l'expression prend la valeur `true`, comme le montre l'exemple suivant :  
  
 `#`  `define`   `DEBUG`  
  
## Notes  
  
> [!NOTE]
>  La directive `#define` ne peut pas être utilisée pour déclarer des valeurs de constante comme c'est généralement le cas dans C et C\+\+.  Il vaut mieux définir les constantes C\# comme membres statiques d'une classe ou d'un struct.  Si vous avez plusieurs constantes de ce type, envisagez de créer une classe « Constants » distincte pour les stocker.  
  
 Les symboles peuvent être utilisés pour indiquer des conditions de compilation.  Vous pouvez tester un symbole à l'aide de [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ou [\#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).  Vous pouvez également utiliser l'attribut `conditional` pour effectuer une compilation conditionnelle.  
  
 Vous pouvez définir un symbole, mais ne pouvez pas assigner une valeur à un symbole.  La directive `#define` doit apparaître dans le fichier avant d'utiliser des instructions qui ne sont pas également des directives de préprocesseur.  
  
 Vous pouvez également définir un symbole à l'aide de l'option de compilation [\/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md).  Vous pouvez annuler la définition d'un symbole à l'aide de [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Un symbole que vous définissez à l'aide de `/define` ou de `#define` ne crée pas de conflit avec une variable du même nom.  En conséquence, le nom d'une variable ne doit pas être passé à une directive de préprocesseur et un symbole peut être seulement évalué par une directive de préprocesseur.  
  
 La portée d'un symbole qui a été créé à l'aide de `#define` correspond au fichier dans lequel le symbole a été défini.  
  
 Comme le montre l'exemple suivant, vous devez placer la directive `#define` en haut du fichier.  
  
```c#  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 Pour obtenir un exemple sur la manière d'annuler la définition d'un symbole, consultez [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C\#](../../../csharp/language-reference/preprocessor-directives/index.md)   
 [const](../../../csharp/language-reference/keywords/const.md)   
 [How to: Compile Conditionally with Trace and Debug](../Topic/How%20to:%20Compile%20Conditionally%20with%20Trace%20and%20Debug.md)   
 [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)   
 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)