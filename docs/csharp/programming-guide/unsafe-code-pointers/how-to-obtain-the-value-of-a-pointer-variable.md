---
title: "Comment : obtenir la valeur d'une variable de pointeur (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8065c10bec737789f13dcbafe147b50eedb9da36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Comment : obtenir la valeur d'une variable de pointeur (Guide de programmation C#)
Utilisez l’opérateur d’indirection de pointeur pour obtenir la variable à l’emplacement désigné par un pointeur. L’expression prend la forme suivante, `p` étant un type de pointeur :  
  
```  
*p;  
```  
  
 Vous ne pouvez pas utiliser l’opérateur d’indirection unaire sur une expression d’un autre type que le type de pointeur. Par ailleurs, vous ne pouvez pas l’appliquer à un pointeur [void](../../../csharp/language-reference/keywords/void.md).  
  
 Quand vous appliquez l’opérateur d’indirection à un pointeur [null](../../../csharp/language-reference/keywords/null.md), le résultat dépend de l’implémentation.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, une variable de type `char` est accessible via des pointeurs de types différents. Notez que l’adresse de `theChar` peut varier d’une exécution à l’autre, car l’adresse physique allouée à une variable peut changer.  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 **Valeur de theChar = Z**  
**Address of theChar = 12F718**  
**Value of pChar = Z**   
**Value of pInt = 90**    
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Types de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Types](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
