---
title: "Passage de tableaux en tant qu’arguments (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f152173b747a171052ab99f261ed91ced9465fdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Passage de tableaux en tant qu’arguments (Guide de programmation C#)
Les tableaux peuvent être passés en tant qu’arguments à des paramètres de méthode. Comme les tableaux sont des types référence, la méthode peut modifier la valeur des éléments.  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a>Passage de tableaux unidimensionnels en tant qu’arguments  
 Vous pouvez passer un tableau unidimensionnel initialisé à une méthode. Par exemple, l’instruction suivante envoie un tableau à une méthode Print.  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 Le code suivant illustre une implémentation partielle de la méthode Print.  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant.  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Dans l’exemple suivant, un tableau de chaînes est initialisé et passé en tant qu’argument à une méthode `PrintArray` pour des chaînes. La méthode affiche les éléments du tableau. Ensuite, les méthodes `ChangeArray` et `ChangeArrayElement` sont appelées pour montrer que l’envoi d’un argument de tableau par valeur n’empêche pas les modifications au niveau des éléments du tableau.  
  
### <a name="code"></a>Code  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a>Passage de tableaux multidimensionnels en tant qu’arguments  
 Vous pouvez passer un tableau multidimensionnel initialisé à une méthode de la même manière que vous passez un tableau unidimensionnel.  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 Le code suivant illustre une déclaration partielle d’une méthode Print qui accepte un tableau à deux dimensions en tant qu’argument.  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Dans l’exemple suivant, un tableau à deux dimensions d’entiers est initialisé et passé à la méthode `Print2DArray`. La méthode affiche les éléments du tableau.  
  
### <a name="code"></a>Code  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)  
 [Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Tableaux en escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md)
