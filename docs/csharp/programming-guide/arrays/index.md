---
title: Tableaux (guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d395bcb179650fe29ab0918e7f91f3c8b6197b5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="arrays-c-programming-guide"></a>Tableaux (guide de programmation C#)
Vous pouvez stocker plusieurs variables du même type dans une structure de données de type tableau. Vous déclarez un tableau en spécifiant le type de ses éléments.  
  
 `type[] arrayName;`  
  
 Les exemples suivants créent des tableaux unidimensionnels, multidimensionnels et en escalier :  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a>Vue d’ensemble du tableau  
 Un tableau possède les propriétés suivantes :  
  
-   Un tableau peut être [unidimensionnel](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [multidimensionnel](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) ou [en escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md).  
  
-   Le nombre de dimensions et la longueur de chaque dimension sont établis lors de la création de l’instance de tableau. Ces valeurs ne peuvent pas être modifiées pendant la durée de vie de l’instance.  
  
-   Les valeurs par défaut des éléments de tableau numériques sont définies sur zéro et les éléments de référence sont définis sur Null.  
  
-   Un tableau en escalier est un tableau de tableaux, et par conséquent ses éléments sont des types référence et sont initialisés sur `null`.  
  
-   Les tableaux sont indexés sur zéro : un tableau avec `n` éléments est indexée de `0` à `n-1`.  
  
-   Les éléments de tableau peuvent être de n’importe quel type, y compris un type tableau.  
  
-   Les types tableau sont des [types référence](../../../csharp/language-reference/keywords/reference-types.md) dérivés du type de base abstrait <xref:System.Array>. Étant donné que ce type implémente <xref:System.Collections.IEnumerable> et <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez utiliser l’itération [foreach](../../../csharp/language-reference/keywords/foreach-in.md) sur tous les tableaux en C#.  
  
## <a name="related-sections"></a>Rubriques connexes  
  
-   [Tableaux comme objets](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [Utilisation de foreach avec des tableaux](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [Passage de tableaux en tant qu’arguments](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [Passage de tableaux à l’aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [Type de collection Array](http://msdn.microsoft.com/library/8a9964de-8941-47b1-a3cf-a01bc88db9e8)
