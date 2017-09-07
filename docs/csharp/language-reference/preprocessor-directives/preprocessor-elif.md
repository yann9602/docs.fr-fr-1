---
title: "#<a name=\"elif-c-reference\"></a>elif (informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#elif'
dev_langs:
- CSharp
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: 14
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
ms.openlocfilehash: 7635365222621101253ecb2a3676701c2e6a2b88
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="elif-c-reference"></a>#elif (informations de référence sur C#)
`#elif` vous permet de créer une directive conditionnelle composée. L’expression `#elif` est évaluée si ni l’expression [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) précédente ni une expression de directive `#elif` facultative précédente n’est évaluée à `true`. Si une expression `#elif` est évaluée à `true`, le compilateur évalue l’ensemble du code situé entre `#elif` et la directive conditionnelle suivante. Exemple :  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 Vous pouvez utiliser les opérateurs `==` (égalité), `!=` (inégalité) `&&` (et) et `||` (ou) pour évaluer plusieurs symboles. Vous pouvez également regrouper des symboles et des opérateurs à l’aide de parenthèses.  
  
## <a name="remarks"></a>Remarques  
 `#elif` revient à utiliser :  
  
```csharp
#else  
#if  
```  
  
 `#elif` est plus simple à utiliser, car chaque expression `#if` a besoin d’une expression [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), alors qu’une expression `#elif` peut être utilisée sans expression `#endif` correspondante.  
  
 Pour obtenir un exemple sur la façon d’utiliser `#elif`, consultez [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md)

