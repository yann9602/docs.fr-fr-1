---
title: Boxing et unboxing (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.boxing
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
caps.latest.revision: 34
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c783ac60735ba25db2736bd9469063c0897be22f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Boxing et unboxing (Guide de programmation C#)
Le boxing est la conversion d’un [type valeur](../../../csharp/language-reference/keywords/value-types.md) en type `object` ou en un type interface implémenté par ce type valeur. Lorsque le CLR exécute un boxing d’un type valeur, il inclut la valeur dans un wrapper, à l’intérieur d’un System.Object, et la stocke sur le tas managé. L'unboxing extrait le type valeur de l'objet. La conversion boxing est implicite ; la conversion unboxing est explicite. Le concept de boxing et de unboxing repose sur la vue unifiée par C# du système de type, dans lequel une valeur de n'importe quel type peut être traitée en tant qu'objet.  
  
 Dans l’exemple suivant, la variable de type entier `i` est convertie (*boxed*) et assignée à l’objet `o`.  
  
 [!code-cs[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]  
  
 L’objet `o` peut ensuite être unboxed et assigné à la variable de type entier `i` :  
  
 [!code-cs[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]  
  
 Les exemples suivants montrent comment le boxing est utilisé dans C#.  
  
 [!code-cs[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]  
  
## <a name="performance"></a>Performances  
 Par rapport aux assignations simples, le boxing et l'unboxing sont des processus qui coûtent cher en calcul. Lorsqu'un type valeur est boxed, un nouvel objet doit être alloué et construit. À un degré moindre, le cast requis pour l'unboxing coûte également cher en calcul. Pour plus d’informations, consultez [Performances](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).  
  
## <a name="boxing"></a>Boxing  
 Le boxing est utilisé pour stocker des types valeur dans le tas rassemblé par garbage collection. Le boxing est une conversion implicite d’un [type valeur](../../../csharp/language-reference/keywords/value-types.md) en type `object` ou en un type interface implémenté par ce type valeur. Le boxing d'un type valeur alloue une instance d'objet sur le tas et copie la valeur dans le nouvel objet.  
  
 Dans l'exemple suivant, une variable de type valeur est déclarée :  
  
 [!code-cs[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]  
  
 L'instruction ci-dessous réalise implicitement une opération de boxing sur la variable `i` :  
  
 [!code-cs[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]  
  
 Le résultat de cette instruction crée, sur la pile, un objet `o` qui fait référence à une valeur de type `int` sur le tas. Cette valeur est une copie de la valeur de type valeur qui a été assignée à la variable `i`. La différence entre les deux variables, `i` et `o`, est illustrée dans la figure ci-dessous.  
  
 ![Graphique d’une conversion boxing](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")  
Conversion boxing  
  
 Il est également possible, mais jamais obligatoire, d'effectuer un boxing explicite comme dans l'exemple suivant :  
  
 [!code-cs[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]  
  
## <a name="description"></a>Description  
 Cet exemple utilise le boxing pour convertir une variable `i` (entier) en un objet `o`. Ensuite, la valeur `i` stockée dans la variable `123` est remplacée par la valeur `456`. L'exemple montre que le type valeur d'origine et que l'objet boxed utilisent des emplacements de mémoire distincts et peuvent, par conséquent, stocker des valeurs différentes.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]  
  
## <a name="unboxing"></a>Unboxing  
 L’unboxing est une conversion explicite du type `object` en un [type valeur](../../../csharp/language-reference/keywords/value-types.md), ou d’un type interface en un type valeur qui implémente l’interface. Une opération d'unboxing comprend les étapes suivantes :  
  
-   Vérification de l'instance de l'objet pour s'assurer qu'il s'agit bien d'une valeur boxed du type valeur spécifié.  
  
-   Copie de la valeur de l'instance dans la variable de type valeur.  
  
 Les instructions suivantes expliquent les opérations de boxing et d'unboxing :  
  
 [!code-cs[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]  
  
 Le résultat de ces instructions est illustré dans la figure ci-dessous.  
  
 ![Graphique de conversion unboxing](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")  
Conversion unboxing  
  
 Pour que l'unboxing de types valeur réussisse au moment de l'exécution, l'élément qui est unboxed doit être une référence à un objet précédemment créé par boxing d'une instance de ce type valeur. La tentative d'extraction de `null` provoque un <xref:System.NullReferenceException>. La tentative d'extraction d'une référence vers un type de valeur incompatible provoque un <xref:System.InvalidCastException>.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre un cas d'unboxing non valide et l'`InvalidCastException` qui en résulte. Avec `try` et `catch`, un message d'erreur est affiché lorsque l'erreur se produit.  
  
 [!code-cs[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]  
  
 Sortie de ce programme :  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 Si vous modifiez l'instruction :  
  
```  
int j = (short) o;  
```  
  
 en :  
  
```  
int j = (int) o;  
```  
  
 la conversion sera réalisée, avec le résultat suivant :  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d'informations :  
  
-   [Types référence](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Types valeur](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)

