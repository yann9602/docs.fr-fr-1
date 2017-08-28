---
title: "Passage de tableaux en tant qu’arguments (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: 21
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
ms.openlocfilehash: 5e83c0c119bc1448be76f83416098158c7f5d684
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Passage de tableaux en tant qu’arguments (Guide de programmation C#)
Les tableaux peuvent être passés en tant qu’arguments à des paramètres de méthode. Comme les tableaux sont des types référence, la méthode peut modifier la valeur des éléments.  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a>Passage de tableaux unidimensionnels en tant qu’arguments  
 Vous pouvez passer un tableau unidimensionnel initialisé à une méthode. Par exemple, l’instruction suivante envoie un tableau à une méthode Print.  
  
 [!code-cs[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 Le code suivant illustre une implémentation partielle de la méthode Print.  
  
 [!code-cs[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant.  
  
 [!code-cs[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Dans l’exemple suivant, un tableau de chaînes est initialisé et passé en tant qu’argument à une méthode `PrintArray` pour des chaînes. La méthode affiche les éléments du tableau. Ensuite, les méthodes `ChangeArray` et `ChangeArrayElement` sont appelées pour montrer que l’envoi d’un argument de tableau par valeur n’empêche pas les modifications au niveau des éléments du tableau.  
  
### <a name="code"></a>Code  
 [!code-cs[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a>Passage de tableaux multidimensionnels en tant qu’arguments  
 Vous pouvez passer un tableau multidimensionnel initialisé à une méthode de la même manière que vous passez un tableau unidimensionnel.  
  
 [!code-cs[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 Le code suivant illustre une déclaration partielle d’une méthode Print qui accepte un tableau à deux dimensions en tant qu’argument.  
  
 [!code-cs[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant.  
  
 [!code-cs[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Dans l’exemple suivant, un tableau à deux dimensions d’entiers est initialisé et passé à la méthode `Print2DArray`. La méthode affiche les éléments du tableau.  
  
### <a name="code"></a>Code  
 [!code-cs[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [Tableaux en escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md)

