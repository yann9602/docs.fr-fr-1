---
title: "&gt;&gt;=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>>=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
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
ms.openlocfilehash: 64f387e475681ffc76f113435ba090b40780dda3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;=, opérateur (référence C#)
Opérateur d’assignation de décalage vers la droite.  
  
## <a name="remarks"></a>Remarques  
 Une expression de la forme  
  
```  
x >>= y  
```  
  
 est évaluée comme  
  
```  
x = x >> y  
```  
  
 sauf que `x` n’est évalué qu’une seule fois. L’[opérateur >>](../../../csharp/language-reference/operators/right-shift-operator.md) décale `x` vers la droite de la valeur spécifiée par `y`.  
  
 L’opérateur >>= ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur >>](../../../csharp/language-reference/operators/right-shift-operator.md) (voir [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)

