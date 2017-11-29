---
title: Utilisation de foreach avec des tableaux (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 797cb9a63a5e1009b170b2afda8634bd21a50035
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Utilisation de foreach avec des tableaux (Guide de programmation C#)
C# fournit également l’instruction [foreach](../../../csharp/language-reference/keywords/foreach-in.md). Cette instruction offre une méthode simple et appropriée pour itérer au sein des éléments d’un tableau ou de toute collection énumérable. L'instruction `foreach` traite les éléments dans l'ordre retourné par la tableau ou l'énumérateur du type de collection, en général, du 0e élément au dernier. Par exemple, le code suivant crée un tableau intitulé `numbers` et itère au sein de ce dernier avec l'instruction `foreach` :  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 Dans le cas de tableaux multidimensionnels, il est possible d'utiliser la même méthode pour itérer au sein de tous les éléments, par exemple :  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 Cependant, dans le cas de tableaux multidimensionnels, l’utilisation d’une boucle [for](../../../csharp/language-reference/keywords/for.md) imbriquée vous permet de mieux contrôler les éléments du tableau.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Array>  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)  
 [Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Tableaux en escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md)
