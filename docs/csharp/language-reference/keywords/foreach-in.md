---
title: "foreach, in (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- foreach
- foreach_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: 29
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
ms.sourcegitcommit: 81117b1419c2a9c3babd6a7429052e2b23e08a70
ms.openlocfilehash: 1c873dfdf001f7efc3340637d210e5fdf42a2852
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="foreach-in-c-reference"></a>foreach, in (référence C#)
L’instruction `foreach` répète un groupe d’instructions incorporées pour chaque élément d’un tableau ou d’une collection d’objets qui implémente l’interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. L’instruction `foreach` est utilisée pour itérer la collection dans le but d’obtenir les informations dont vous avez besoin. Elle ne peut pas être utilisée pour ajouter ou supprimer des éléments de la collection source pour éviter des effets secondaires imprévisibles. Si vous avez besoin d’ajouter ou de supprimer des éléments de la collection source, utilisez une boucle [for](../../../csharp/language-reference/keywords/for.md).  
  
 Les instructions incorporées continuent de s’exécuter pour chaque élément de la collection ou du tableau. Une fois l’itération terminée pour tous les éléments de la collection, le contrôle est transféré à l’instruction qui suit le bloc `foreach`.  
  
 Vous pouvez quitter la boucle à n’importe quel endroit du bloc `foreach` à l’aide du mot clé [break](../../../csharp/language-reference/keywords/break.md), ou passer à l’itération suivante de la boucle à l’aide du mot clé [continue](../../../csharp/language-reference/keywords/continue.md).  
  
 Une boucle `foreach` peut également être quittée à l’aide des instructions [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).  
  
 Pour plus d’informations sur le mot clé `foreach` et sur les exemples de code, consultez les rubriques suivantes :  
  
 [Utilisation de foreach avec des tableaux](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
 [Guide pratique pour accéder à une classe de collection à l’aide de foreach](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  
  
## <a name="example"></a>Exemple  
 Le code suivant montre trois exemples :  
  
-   Une boucle `foreach` typique qui affiche le contenu d’un tableau d’entiers  
  
-   Une boucle [for](../../../csharp/language-reference/keywords/for.md) qui fait la même chose  
  
-   Une boucle `foreach` qui compte le nombre d’éléments du tableau  
  
 [!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/foreach-in_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Instructions d’itération](../../../csharp/language-reference/keywords/iteration-statements.md)   
 [for](../../../csharp/language-reference/keywords/for.md)

