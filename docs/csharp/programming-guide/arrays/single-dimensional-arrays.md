---
title: Tableaux unidimensionnels (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fed9042ba37164927bb8073bc669fafeb5d40598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tableaux unidimensionnels (Guide de programmation C#)
Vous pouvez déclarer un tableau unidimensionnel de cinq entiers comme indiqué dans l’exemple suivant :  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 Ce tableau contient les éléments de `array[0]` à `array[4]`. L’opérateur [new](../../../csharp/language-reference/keywords/new.md) est utilisé pour créer le tableau et initialiser ses éléments à leurs valeurs par défaut. Dans cet exemple, tous les éléments du tableau sont initialisés à zéro.  
  
 Un tableau qui stocke des éléments de type chaîne peut être déclaré de la même façon. Exemple :  
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Initialisation du tableau  
 Il est possible d’initialiser un tableau lors de sa déclaration, auquel cas le spécificateur de rang n’est pas nécessaire, car il est déjà fourni par le nombre d’éléments figurant dans la liste d’initialisation. Exemple :  
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 Un tableau de chaînes peut être initialisé de la même manière. Voici une déclaration d’un tableau de chaînes où chaque élément du tableau est initialisé par un nom de jour de la semaine :  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 Quand vous initialisez un tableau lors de sa déclaration, vous pouvez utiliser les raccourcis suivants :  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 Il est possible de déclarer une variable de tableau sans initialisation, mais vous devez alors utiliser l’opérateur `new` quand vous affectez un tableau à cette variable. Exemple :  
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 C# 3.0 introduit les tableaux implicitement typés. Pour plus d’informations, consultez [Tableaux implicitement typés](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Tableaux de types valeur et de types référence  
 Considérons la déclaration de tableau suivante :  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 Le résultat de cette instruction varie selon que `SomeType` est un type valeur ou un type référence. S’il s’agit d’un type de valeur, l’instruction crée un tableau de 10 éléments, chacun ayant le type `SomeType`. Si `SomeType` est un type référence, l’instruction crée un tableau de 10 éléments dont chacun est initialisé avec une référence null.  
  
 Pour plus d’informations sur les types valeur et les types références, consultez [Types](../../../csharp/language-reference/keywords/types.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Array>  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)  
 [Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Tableaux en escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md)
