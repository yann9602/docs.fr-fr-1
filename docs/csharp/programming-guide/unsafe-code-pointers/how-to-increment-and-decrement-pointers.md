---
title: "Guide pratique pour incrémenter et décrémenter des pointeurs (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: 20
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
ms.openlocfilehash: b474249ed9f7778e44981b292d51f29f46bc420d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>Guide pratique pour incrémenter et décrémenter des pointeurs (Guide de programmation C#)
Utilisez les opérateurs d’incrémentation et de décrémentation, `++` et `--`, pour changer l’emplacement du pointeur de [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) pour un pointeur de type pointer-type*. Les expressions d’incrémentation et de décrémentation prennent la forme suivante :  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 Les opérateurs d’incrémentation et de décrémentation peuvent être appliqués aux pointeurs de tout type à l’exception du type `void*`.  
  
 L’application de l’opérateur d’incrémentation à un pointeur de type `pointer-type` a pour effet d’ajouter [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) à l’adresse contenue dans la variable pointeur.  
  
 L’application de l’opérateur de décrémentation à un pointeur de type `pointer-type` a pour effet de soustraire `sizeof` (`pointer-type`) à l’adresse contenue dans la variable pointeur.  
  
 Aucune exception n’est générée si l’opération produit un dépassement de capacité sur le domaine du pointeur, et le résultat dépend de l’implémentation.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, vous parcourez un tableau en incrémentant le pointeur de la taille de `int`. À chaque étape, vous affichez l’adresse et le contenu de l’élément de tableau.  
  
 [!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-cs[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
 **Valeur : 0 @ Adresse : 12860272**  
**Valeur : 1 @ Adresse : 12860276**  
**Valeur : 2 @ Adresse : 12860280**  
**Valeur : 3 @ Adresse : 12860284**  
**Valeur : 4 @ Adresse : 12860288**   
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)   
 [Manipulation de pointeurs](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)   
 [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)

