---
title: "^=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: 16
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
ms.openlocfilehash: 33b0dccf5031809bb4fcb73d0f7d6a344accdea3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>^=, opérateur (référence C#)
Opérateur d’assignation OR exclusif.  
  
## <a name="remarks"></a>Remarques  
 Une expression de la forme  
  
```  
x ^= y  
```  
  
 est évaluée comme  
  
```  
x = x ^ y  
```  
  
 sauf que `x` n’est évalué qu’une seule fois. L’[opérateur ^](../../../csharp/language-reference/operators/xor-operator.md) effectue une opération de bits OR exclusif sur les opérandes de type intégral et une opération OR exclusif logique sur les opérandes de type [bool](../../../csharp/language-reference/keywords/bool.md).  
  
 L’opérateur ^= ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur ^](../../../csharp/language-reference/operators/xor-operator.md) (voir [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)

