---
title: Tableaux en tant qu'objets (guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: 17
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
ms.openlocfilehash: 396d0df9196b7331e94127730b83782ffc8ea593
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="arrays-as-objects-c-programming-guide"></a>Tableaux en tant qu'objets (guide de programmation C#)
En C#, les tableaux sont en fait des objets, et pas simplement des zones adressables de mémoire contiguë comme en C et C++. <xref:System.Array> est le type de base abstrait de tous les types de tableau. Vous pouvez utiliser les propriétés et les autres membres de classe de ce type <xref:System.Array>. Vous pourriez, par exemple, utiliser la propriété <xref:System.Array.Length%2A> pour obtenir la longueur d’un tableau. Le code suivant affecte la longueur du tableau `numbers`, c’est-à-dire la valeur `5`, à une variable appelée `lengthOfNumbers` :  
  
 [!code-cs[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 La classe <xref:System.Array> fournit beaucoup d’autres méthodes et propriétés utiles pour trier, rechercher et copier des tableaux.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la propriété <xref:System.Array.Rank%2A> pour afficher le nombre de dimensions d’un tableau.  
  
 [!code-cs[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [Tableaux en escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md)

