---
title: "#<a name=\"define-c-reference\"></a>define (informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#define'
helpviewer_keywords: '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae72a1b6c19421c51348a0d93691ba3fe29a191c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="define-c-reference"></a>#define (référence C#)
Vous utilisez `#define` pour définir un symbole. Quand vous utilisez le symbole sous forme d’expression passée à la directive [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), l’expression donne la valeur `true`, comme illustré dans l’exemple suivant :  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
>  La directive `#define` ne peut pas être utilisée pour déclarer des valeurs constantes comme c’est le cas en général en C et C++. Les constantes en C# sont définies plutôt comme des membres statiques d’une classe ou d’un struct. Si vous avez plusieurs constantes de ce type, créez une classe « Constantes » distincte pour les stocker.  
  
 Les symboles peuvent être utilisés pour spécifier des conditions de compilation. Vous pouvez tester le symbole avec [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ou [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md). Vous pouvez également utiliser l’attribut `conditional` pour effectuer une compilation conditionnelle.  
  
 Vous pouvez définir un symbole, mais vous ne pouvez pas attribuer de valeur à un symbole. La directive `#define` doit apparaître dans le fichier avant l’utilisation d’instructions qui ne sont pas également des directives de préprocesseur.  
  
 Vous pouvez également définir un symbole avec l’option de compilateur [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md). Vous pouvez annuler la définition d’un symbole avec [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Un symbole que vous définissez avec `/define` ou `#define` n’est pas en conflit avec une variable du même nom. Autrement dit, un nom de variable ne doit pas être passé à une directive de préprocesseur et un symbole ne peut être évalué que par une directive de préprocesseur.  
  
 La portée d’un symbole qui a été créé à l’aide de `#define` est le fichier dans lequel le symbole a été défini.  
  
 Comme le montre l’exemple suivant, vous devez placer les directives `#define` en haut du fichier.  
  
```csharp  
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
  
 Pour obtenir un exemple montrant comment annuler la définition d’un symbole, consultez [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [const](../../../csharp/language-reference/keywords/const.md)  
 [Comment : effectuer une compilation conditionnelle avec Trace et Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
