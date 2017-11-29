---
title: "&gt;&gt;=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6bd0a61860c35a485d61585a90ba297f75d8cf1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;=, opérateur (référence C#)
Opérateur d’assignation de décalage vers la droite.  
  
## <a name="remarks"></a>Remarques  
 Une expression sous la forme  
  
```  
x >>= y  
```  
  
 est évaluée comme étant  
  
```  
x = x >> y  
```  
  
 sauf que `x` n’est évalué qu’une seule fois. L’[opérateur >>](../../../csharp/language-reference/operators/right-shift-operator.md) décale `x` vers la droite de la valeur spécifiée par `y`.  
  
 L’opérateur >>= ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur >>](../../../csharp/language-reference/operators/right-shift-operator.md) (voir [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
