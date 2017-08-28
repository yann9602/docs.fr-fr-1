---
title: "#<a name=\"endif-c-reference\"></a>endif (informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#endif'
dev_langs:
- CSharp
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
caps.latest.revision: 9
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
ms.openlocfilehash: e4c37657a1ca81b7e5403e58123cf630a224b8ec
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="endif-c-reference"></a>#endif (informations de référence sur C#)
`#endif` spécifie la fin d’une directive conditionnelle, qui a commencé avec la directive [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md). Par exemple :  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Remarques  
 Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`. Consultez [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) pour obtenir un exemple d’utilisation de `#endif`.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md)

