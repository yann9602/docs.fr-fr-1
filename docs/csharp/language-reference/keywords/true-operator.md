---
title: "true, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 96ab7679862959f3c99e31beac0bd5514228bd8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="true-operator-c-reference"></a>true, opérateur (référence C#)
Retourne la valeur [bool](../../../csharp/language-reference/keywords/bool.md) `true` pour indiquer qu’un opérande est vrai. Sinon, il retourne `false`.  
  
 Avant C# 2.0, les opérateurs `true` et `false` étaient utilisés pour créer des types valeur Nullable définis par l’utilisateur qui étaient compatibles avec les types tels que `SqlBool`. Maintenant, ce langage offre la prise en charge intégrée des types valeur Nullable. Lorsque cela vous est possible, vous devez utiliser ces types au lieu de surcharger les opérateurs `true` et `false`. Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Avec les valeurs booléennes Nullable, l’expression `a != b` n’est pas nécessairement égale à `!(a == b)`, car l’une ou l’autre de ces valeurs (voire les deux) peuvent être Null. Vous devez surcharger les opérateurs `true` et `false` séparément pour identifier correctement les valeurs Null de l’expression. L’exemple suivant montre comment surcharger et utiliser les opérateurs `true` et `false`.  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]  
  
 Un type qui surcharge les opérateurs `true` et `false` peut être utilisé pour l’expression de contrôle des instructions [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md) et [for](../../../csharp/language-reference/keywords/for.md), et des [expressions conditionnelles](../../../csharp/language-reference/operators/conditional-operator.md).  
  
 Si un type définit l’opérateur `true`, il doit aussi définir l’opérateur [false](../../../csharp/language-reference/keywords/false.md).  
  
 Un type ne peut pas surcharger directement les opérateurs logiques conditionnels ([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) et [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)). Toutefois, un effet équivalent peut être obtenu en surchargeant les opérateurs logiques habituels et les opérateurs `true` et `false`.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)  
 [false](../../../csharp/language-reference/keywords/false.md)
