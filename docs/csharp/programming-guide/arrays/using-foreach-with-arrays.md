---
title: Utilisation de foreach avec des tableaux (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: 14
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
ms.openlocfilehash: a1d0b704233b110b5f499b8186a4a901f9b5408f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Utilisation de foreach avec des tableaux (Guide de programmation C#)
C# fournit également l’instruction [foreach](../../../csharp/language-reference/keywords/foreach-in.md). Cette instruction offre une méthode simple et appropriée pour itérer au sein des éléments d’un tableau ou de toute collection énumérable. L'instruction `foreach` traite les éléments dans l'ordre retourné par le tableau ou l'énumérateur du type de collection, en général, du 0e élément au dernier. Par exemple, le code suivant crée un tableau intitulé `numbers` et itère au sein de ce dernier avec l'instruction `foreach` :  
  
 [!code-cs[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 Dans le cas de tableaux multidimensionnels, il est possible d'utiliser la même méthode pour itérer au sein de tous les éléments, par exemple :  
  
 [!code-cs[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 Cependant, dans le cas de tableaux multidimensionnels, l’utilisation d’une boucle [for](../../../csharp/language-reference/keywords/for.md) imbriquée vous permet de mieux contrôler les éléments du tableau.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Array>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [Tableaux en escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md)

