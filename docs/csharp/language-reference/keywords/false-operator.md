---
title: "false, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
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
ms.openlocfilehash: e12de403ca31952837913fdaaa8b221986f0e5fe
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="false-operator-c-reference"></a>false, opérateur (référence C#)
Retourne la valeur [bool](../../../csharp/language-reference/keywords/bool.md) `true` pour indiquer qu’un opérande est `false`. Sinon, retourne `false`.  
  
 Avant C# 2.0, les opérateurs `true` et `false` étaient utilisés pour créer des types valeur Nullable définis par l’utilisateur qui étaient compatibles avec les types tels que `SqlBool`. Maintenant, ce langage offre la prise en charge intégrée des types valeur Nullable. Lorsque cela vous est possible, vous devez utiliser ces types au lieu de surcharger les opérateurs `true` et `false`. Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Avec les valeurs booléennes Nullables, l’expression `a != b` n’est pas nécessairement égale à `!(a == b)`, car l’une ou l’autre de ces valeurs (voire les deux) peuvent être Null. Vous devez surcharger les opérateurs `true` et `false` séparément pour gérer correctement les valeurs Null de l’expression. L’exemple suivant montre comment surcharger et utiliser les opérateurs `true` et `false`.  
  
 [!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]  
  
 Un type qui surcharge les opérateurs `true` et `false` peut être utilisé pour l’expression de contrôle des instructions [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md) et [for](../../../csharp/language-reference/keywords/for.md), et des [expressions conditionnelles](../../../csharp/language-reference/operators/conditional-operator.md).  
  
 Si un type définit l’opérateur `false`, il doit aussi définir l’opérateur [true](../../../csharp/language-reference/keywords/true.md).  
  
 Un type ne peut pas surcharger directement les opérateurs logiques conditionnels [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) et [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md). Toutefois, vous pouvez obtenir un effet équivalent en surchargeant les opérateurs logiques habituels et les opérateurs `true` et `false`.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)   
 [true](../../../csharp/language-reference/keywords/true.md)

