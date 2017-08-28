---
title: "Passage de tableaux à l'aide de paramètres ref et out (guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
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
ms.openlocfilehash: 58fc359881295a9e6627ac1269ef17aa298009c7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a>Passage de tableaux à l'aide de paramètres ref et out (guide de programmation C#)
Comme tous les paramètres [out](../../../csharp/language-reference/keywords/out.md), un paramètre `out` d’un type tableau doit être assigné avant d’être utilisé ; c’est-à-dire qu’il doit être assigné par l’appelé. Exemple :  
  
 [!code-cs[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 Comme tous les paramètres [ref](../../../csharp/language-reference/keywords/ref.md), un paramètre `ref` d’un type tableau doit absolument être assigné par l’appelant. Par conséquent, il n'a pas besoin d'être assigné par l'appelé. Un paramètre `ref` d'un type tableau peut être modifié à la suite de l'appel. Par exemple, la valeur [null](../../../csharp/language-reference/keywords/null.md) peut être assignée au tableau ou ce dernier peut être initialisé sur un tableau différent. Exemple :  
  
 [!code-cs[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 Les deux exemples suivants illustrent la différence entre les paramètres `out` et `ref` lorsqu'ils sont utilisés pour le passage de tableaux à des méthodes.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, le tableau `theArray` est déclaré dans l'appelant (la méthode `Main`) et initialisé dans la méthode `FillArray`. Ensuite, les éléments du tableau sont retournés à l'appelant puis affichés.  
  
 [!code-cs[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, le tableau `theArray` est initialisé dans l'appelant (la méthode `Main`) et passé à la méthode `FillArray` à l'aide du paramètre `ref`. Certains des éléments du tableau sont mis à jour dans la méthode `FillArray`. Ensuite, les éléments du tableau sont retournés à l'appelant puis affichés.  
  
 [!code-cs[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [ref](../../../csharp/language-reference/keywords/ref.md)   
 [out, modificateur de paramètre](../../../csharp/language-reference/keywords/out-parameter-modifier.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [Tableaux en escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md)

