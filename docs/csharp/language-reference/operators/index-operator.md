---
title: "[], opérateur (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '[]_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: 20
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4eaecd5cd70c396a62856087a7b37f38e02d2383
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-c-reference"></a>[], opérateur (référence C#)
Les crochets (`[]`) sont utilisés pour les tableaux, les indexeurs et les attributs. Ils peuvent également être utilisés avec les pointeurs.  
  
## <a name="remarks"></a>Remarques  
 Un type tableau est un type suivi de `[]` :  
  
 [!code-cs[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 Pour accéder à un élément d’un tableau, vous devez placer l’index de l’élément souhaité entre crochets :  
  
 [!code-cs[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 Une exception est levée si un index de tableau est hors portée.  
  
 L’opérateur d’indexation de tableau ne peut pas être surchargé. Toutefois, les types peuvent définir les indexeurs, ainsi que les propriétés qui acceptent un ou plusieurs paramètres. Les paramètres d’indexeur sont placés entre crochets, comme les index de tableau, mais ils peuvent être déclarés comme étant de tout type, contrairement aux index de tableau, qui doivent être intégraux.  
  
 Par exemple, le .NET Framework définit un type `Hashtable` qui associe des clés et des valeurs de type arbitraire :  
  
 [!code-cs[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 Les crochets sont également utilisés pour spécifier des [attributs](../../../csharp/programming-guide/concepts/attributes/index.md) :  
  
 [!code-cs[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 Vous pouvez utiliser des crochets pour indexer un pointeur :  
  
 [!code-cs[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 Aucune vérification des limites n’est effectuée.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Indexeurs](../../../csharp/programming-guide/indexers/index.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)

