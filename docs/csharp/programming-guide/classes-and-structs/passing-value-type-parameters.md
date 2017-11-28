---
title: "Passage de paramètres de type valeur (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 08a336e9aa34ac3ce5bb8848df533caa563972f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Passage de paramètres de type valeur (Guide de programmation C#)
Une variable de [type valeur](../../../csharp/language-reference/keywords/value-types.md) contient ses données directement, par opposition à une variable de [type référence](../../../csharp/language-reference/keywords/reference-types.md), qui contient une référence à ses données. Passer une variable de type valeur à une méthode par valeur signifie passer une copie de la variable à la méthode. Les modifications du paramètre qui interviennent à l’intérieur de la méthode n’ont aucune incidence sur les données d’origine stockées dans la variable d’argument. Si vous souhaitez que la méthode appelée change la valeur du paramètre, vous devez la passer par référence, à l’aide du mot clé [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md). Pour des raisons de simplicité, les exemples suivants utilisent `ref`.  
  
## <a name="passing-value-types-by-value"></a>Passage de types valeur par valeur  
 L’exemple suivant illustre le passage de paramètres de type valeur par valeur. La variable `n` est passée par valeur à la méthode `SquareIt`. Les modifications qui interviennent à l’intérieur de la méthode n’ont aucune incidence sur la valeur d’origine de la variable.  
  
 [!code-csharp[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]  
  
 La variable `n` est un type valeur. Elle contient ses données, la valeur `5`. Quand `SquareIt` est appelée, le contenu de `n` est copié dans le paramètre `x`, qui est mis au carré à l’intérieur de la méthode. Dans `Main`, toutefois, la valeur de `n` est identique avant et après l’appel de la méthode `SquareIt`. La modification qui intervient à l’intérieur de la méthode affecte uniquement la variable locale `x`.  
  
## <a name="passing-value-types-by-reference"></a>Passage de types valeur par référence  
 L’exemple suivant est identique au précédent, sauf que l’argument est passé en tant que paramètre `ref`. La valeur de l’argument sous-jacent, `n`, est modifiée quand `x` est modifiée dans la méthode.  
  
 [!code-csharp[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]  
  
 Dans cet exemple, ce n’est pas la valeur de `n` qui est passée, mais plutôt une référence à `n`. Le paramètre `x` n’est pas un [int](../../../csharp/language-reference/keywords/int.md) ; il s’agit d’une référence à un `int`, dans le cas présent une référence à `n`. Ainsi, quand `x` est mis au carré à l’intérieur de la méthode, ce qui est réellement mis au carré est ce à quoi `x` fait référence, c’est-à-dire `n`.  
  
## <a name="swapping-value-types"></a>Permutation de types valeur  
 L’un des exemples courants de changement de valeurs d’arguments est une méthode de permutation, où vous passez deux variables à la méthode et celle-ci permute leur contenu. Vous devez passer les arguments à la méthode de permutation par référence. Sinon, vous permutez des copies locales des paramètres à l’intérieur de la méthode, et aucune modification n’intervient dans la méthode d’appel. L’exemple suivant permute des valeurs d’entier.  
  
 [!code-csharp[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]  
  
 Quand vous appelez la méthode `SwapByRef`, utilisez le mot-clé `ref` dans l’appel, comme illustré dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Passage de paramètres](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Passage de paramètres de type référence](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)
