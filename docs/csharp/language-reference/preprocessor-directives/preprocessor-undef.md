---
title: "#<a name=\"undef-c-reference\"></a>undef (informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#undef'
dev_langs:
- CSharp
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: acdd043535ef319f2af40c809e7fe4af612cb17d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="undef-c-reference"></a>#undef (informations de référence sur C#)
`#undef` vous permet d’annuler la définition d’un symbole de telle sorte qu’en utilisant le symbole comme expression dans une directive [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), l’expression correspond à `false`.  
  
 Un symbole peut être défini avec la directive [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) ou l’option du compilateur [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md). La directive `#undef` doit figurer dans le fichier préalablement à l’utilisation d’instructions qui ne sont pas aussi des directives.  
  
## <a name="example"></a>Exemple  
  
```csharp
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
  
 **DEBUG n’est pas défini**   
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md)

