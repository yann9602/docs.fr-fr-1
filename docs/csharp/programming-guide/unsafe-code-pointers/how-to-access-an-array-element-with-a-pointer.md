---
title: "Comment : accéder à un élément de tableau à l'aide d'un pointeur (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 737c1d7fc0bc0a739de5c0a6cbc5dc09f813133e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>Comment : accéder à un élément de tableau à l'aide d'un pointeur (Guide de programmation C#)
Dans un contexte unsafe, vous pouvez accéder à un élément en mémoire en utilisant l’accès à un élément de pointeur, comme illustré dans l’exemple suivant :  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 L’expression entre crochets doit être implicitement convertible en `int`, `uint`, `long` ou `ulong`. L’opération p[e] équivaut à *(p+e). Comme C et C++, l’accès à un élément de pointeur ne recherche pas les erreurs de dépassement des limites.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, 123 emplacements de mémoire sont alloués à un tableau de caractères, `charPointer`. Le tableau est utilisé pour afficher les lettres minuscules et les lettres majuscules dans deux boucles [for](../../../csharp/language-reference/keywords/for.md).  
  
 Remarquez que l’expression `charPointer[i]` équivaut à l’expression `*(charPointer + i)`, et vous pouvez obtenir le même résultat en utilisant l’une ou l’autre expression.  
  
 [!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]  
  
 **Lettres majuscules :**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**Lettres minuscules :**  
**abcdefghijklmnopqrstuvwxyz**   
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Types de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Types](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
