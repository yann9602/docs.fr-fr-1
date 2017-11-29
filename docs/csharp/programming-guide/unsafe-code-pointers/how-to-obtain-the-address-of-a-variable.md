---
title: "Comment : obtenir l'adresse d'une variable (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Comment : obtenir l'adresse d'une variable (Guide de programmation C#)
Pour obtenir l’adresse d’une expression unaire, qui est évaluée en tant que variable fixe, utilisez l’opérateur address-of :  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 L’opérateur address-of peut être appliqué à une seule variable uniquement. Si la variable peut être déplacée, vous pouvez utiliser l’[instruction fixed](../../../csharp/language-reference/keywords/fixed-statement.md) pour fixer temporairement la variable avant d’obtenir son adresse.  
  
 Il vous appartient de vérifier que la variable est initialisée. Le compilateur ne génère pas de message d’erreur si la variable n’est pas initialisée.  
  
 Vous ne pouvez pas obtenir l’adresse d’une constante ou d’une valeur.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, un pointeur désignant `int`, `p`, est déclaré et se voit assigner l’adresse d’une variable entière, `number`. La variable `number` est initialisée à la suite de l’assignation à *p. Si vous assortissez cette instruction d’assignation d’un commentaire, l’initialisation de la variable `number` est supprimée, mais aucune erreur n’est émise au moment de la compilation. Notez l’utilisation de l’opérateur d’[accès de membre](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) `->` pour obtenir et afficher l’adresse stockée dans le pointeur.  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Types de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Types](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
