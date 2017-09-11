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
ms.lasthandoff: 07/28/2017

---
# <a name="false-operator-c-reference"></a><span data-ttu-id="eb745-102">false, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="eb745-102">false Operator (C# Reference)</span></span>
<span data-ttu-id="eb745-103">Retourne la valeur [bool](../../../csharp/language-reference/keywords/bool.md) `true` pour indiquer qu’un opérande est `false`. Sinon, retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="eb745-103">Returns the [bool](../../../csharp/language-reference/keywords/bool.md) value `true` to indicate that an operand is `false` and returns `false` otherwise.</span></span>  
  
 <span data-ttu-id="eb745-104">Avant C# 2.0, les opérateurs `true` et `false` étaient utilisés pour créer des types valeur Nullable définis par l’utilisateur qui étaient compatibles avec les types tels que `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="eb745-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="eb745-105">Maintenant, ce langage offre la prise en charge intégrée des types valeur Nullable. Lorsque cela vous est possible, vous devez utiliser ces types au lieu de surcharger les opérateurs `true` et `false`.</span><span class="sxs-lookup"><span data-stu-id="eb745-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="eb745-106">Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb745-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="eb745-107">Avec les valeurs booléennes Nullables, l’expression `a != b` n’est pas nécessairement égale à `!(a == b)`, car l’une ou l’autre de ces valeurs (voire les deux) peuvent être Null.</span><span class="sxs-lookup"><span data-stu-id="eb745-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="eb745-108">Vous devez surcharger les opérateurs `true` et `false` séparément pour gérer correctement les valeurs Null de l’expression.</span><span class="sxs-lookup"><span data-stu-id="eb745-108">You have to overload both the `true` and `false` operators separately to correctly handle the null values in the expression.</span></span> <span data-ttu-id="eb745-109">L'exemple suivant montre comment surcharger et utiliser les opérateurs `true` et `false`.</span><span class="sxs-lookup"><span data-stu-id="eb745-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>  
  
 <span data-ttu-id="eb745-110">[!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="eb745-110">[!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="eb745-111">Vous pouvez utiliser un type qui surcharge les opérateurs `true` et `false` pour l’expression de contrôle des instructions [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md) et [for](../../../csharp/language-reference/keywords/for.md), ainsi que dans les [expressions conditionnelles](../../../csharp/language-reference/operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="eb745-111">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), and [for](../../../csharp/language-reference/keywords/for.md) statements and in [conditional expressions](../../../csharp/language-reference/operators/conditional-operator.md).</span></span>  
  
 <span data-ttu-id="eb745-112">Si un type définit l’opérateur `false`, il doit aussi définir l’opérateur [true](../../../csharp/language-reference/keywords/true.md).</span><span class="sxs-lookup"><span data-stu-id="eb745-112">If a type defines operator `false`, it must also define operator [true](../../../csharp/language-reference/keywords/true.md).</span></span>  
  
 <span data-ttu-id="eb745-113">Un type ne peut pas surcharger directement les opérateurs logiques conditionnels [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) et [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md). Toutefois, vous pouvez obtenir un effet équivalent en surchargeant les opérateurs logiques habituels et les opérateurs `true` et `false`.</span><span class="sxs-lookup"><span data-stu-id="eb745-113">A type cannot directly overload the conditional logical operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="eb745-114">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="eb745-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eb745-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb745-115">See Also</span></span>  
 <span data-ttu-id="eb745-116">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="eb745-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="eb745-117">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="eb745-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="eb745-118">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="eb745-118">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="eb745-119">[Opérateurs C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="eb745-119">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 [<span data-ttu-id="eb745-120">true</span><span class="sxs-lookup"><span data-stu-id="eb745-120">true</span></span>](../../../csharp/language-reference/keywords/true.md)

