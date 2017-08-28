---
title: "Guide pratique pour obtenir l’adresse d’une variable (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: 19
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
ms.openlocfilehash: 169f68cc80b7a27427a9987942e66e0ba9ed1a02
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Guide pratique pour obtenir l’adresse d’une variable (Guide de programmation C#)
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
  
 [!code-cs[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-cs[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)

