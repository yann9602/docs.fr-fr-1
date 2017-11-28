---
title: "#<a name=\"if-c-reference\"></a>if (informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#if'
helpviewer_keywords: '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4e3b79f64f5190d48d7248726ecdf031ad685e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="if-c-reference"></a>#if (référence C#)
Quand le compilateur C# rencontre une directive `#if`, suivie éventuellement d’une directive [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), il compile le code entre les directives uniquement si le symbole spécifié est défini.  Contrairement à C et C++, vous ne pouvez pas attribuer une valeur numérique à un symbole ; l’instruction #if en C# est booléenne et vérifie uniquement si le symbole a été défini ou non. Par exemple :  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 Vous pouvez utiliser les opérateurs [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (égalité), [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (inégalité) uniquement pour tester la valeur [true](../../../csharp/language-reference/keywords/true.md) ou [false](../../../csharp/language-reference/keywords/false.md). True signifie que le symbole est défini. L’instruction `#if DEBUG` a la même signification que `#if (DEBUG == true)`. Vous pouvez utiliser les opérateurs [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (et), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (or) et [!](../../../csharp/language-reference/operators/logical-negation-operator.md) (not) pour vérifier si plusieurs symboles ont été définis. Vous pouvez également regrouper des symboles et des opérateurs à l’aide de parenthèses.  
  
## <a name="remarks"></a>Remarques  
 `#if`, ainsi que les directives [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) et [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md), vous permettent d’inclure ou d’exclure du code en fonction de l’existence d’un ou plusieurs symboles. Cela peut être utile lors de la compilation du code pour une version Debug ou lors de la compilation d’une configuration spécifique.  
  
 Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`.  
  
 `#define` vous permet de définir un symbole de telle sorte que, en utilisant le symbole comme expression passée à la directive `#if`, l’expression corresponde à `true`.  
  
 Vous pouvez également définir un symbole avec l’option du compilateur [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md). Vous pouvez annuler la définition d’un symbole avec [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Un symbole que vous définissez avec `/define` ou `#define` n’est pas en conflit avec une variable du même nom. Autrement dit, un nom de variable ne doit pas être passé à une directive de préprocesseur et un symbole ne peut être évalué que par une directive de préprocesseur.  
  
 La portée d’un symbole créé avec `#define` est le fichier dans lequel il a été défini.  
  
## <a name="example"></a>Exemple  
  
```csharp
// preprocessor_if.cs  
#define DEBUG
#define MYTEST  
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
  
 **DEBUG et MYTEST sont définis**  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md)
