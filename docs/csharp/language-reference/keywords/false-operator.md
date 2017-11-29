---
title: "false, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f9761fb49e2c7f6e4a7615e64cec9fed88318c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="e24e4-102">false, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="e24e4-102">false Operator (C# Reference)</span></span>
<span data-ttu-id="e24e4-103">Retourne la valeur [bool](../../../csharp/language-reference/keywords/bool.md) `true` pour indiquer qu’un opérande est `false`. Sinon, retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="e24e4-103">Returns the [bool](../../../csharp/language-reference/keywords/bool.md) value `true` to indicate that an operand is `false` and returns `false` otherwise.</span></span>  
  
 <span data-ttu-id="e24e4-104">Avant C# 2.0, les opérateurs `true` et `false` étaient utilisés pour créer des types valeur Nullable définis par l’utilisateur qui étaient compatibles avec les types tels que `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="e24e4-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="e24e4-105">Maintenant, ce langage offre la prise en charge intégrée des types valeur Nullable. Lorsque cela vous est possible, vous devez utiliser ces types au lieu de surcharger les opérateurs `true` et `false`.</span><span class="sxs-lookup"><span data-stu-id="e24e4-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="e24e4-106">Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="e24e4-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="e24e4-107">Avec les valeurs booléennes Nullables, l’expression `a != b` n’est pas nécessairement égale à `!(a == b)`, car l’une ou l’autre de ces valeurs (voire les deux) peuvent être Null.</span><span class="sxs-lookup"><span data-stu-id="e24e4-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="e24e4-108">Vous devez surcharger les opérateurs `true` et `false` séparément pour gérer correctement les valeurs Null de l’expression.</span><span class="sxs-lookup"><span data-stu-id="e24e4-108">You have to overload both the `true` and `false` operators separately to correctly handle the null values in the expression.</span></span> <span data-ttu-id="e24e4-109">L’exemple suivant montre comment surcharger et utiliser les opérateurs `true` et `false`.</span><span class="sxs-lookup"><span data-stu-id="e24e4-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]  
  
 <span data-ttu-id="e24e4-110">Un type qui surcharge les opérateurs `true` et `false` peut être utilisé pour l’expression de contrôle des instructions [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md) et [for](../../../csharp/language-reference/keywords/for.md), et des [expressions conditionnelles](../../../csharp/language-reference/operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e24e4-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), and [for](../../../csharp/language-reference/keywords/for.md) statements and in [conditional expressions](../../../csharp/language-reference/operators/conditional-operator.md).</span></span>  
  
 <span data-ttu-id="e24e4-111">Si un type définit l’opérateur `false`, il doit aussi définir l’opérateur [true](../../../csharp/language-reference/keywords/true.md).</span><span class="sxs-lookup"><span data-stu-id="e24e4-111">If a type defines operator `false`, it must also define operator [true](../../../csharp/language-reference/keywords/true.md).</span></span>  
  
 <span data-ttu-id="e24e4-112">Un type ne peut pas surcharger directement les opérateurs logiques conditionnels [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) et [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md). Toutefois, vous pouvez obtenir un effet équivalent en surchargeant les opérateurs logiques habituels et les opérateurs `true` et `false`.</span><span class="sxs-lookup"><span data-stu-id="e24e4-112">A type cannot directly overload the conditional logical operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e24e4-113">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e24e4-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e24e4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e24e4-114">See Also</span></span>  
 [<span data-ttu-id="e24e4-115">Référence C#</span><span class="sxs-lookup"><span data-stu-id="e24e4-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e24e4-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e24e4-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e24e4-117">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="e24e4-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e24e4-118">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="e24e4-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="e24e4-119">true</span><span class="sxs-lookup"><span data-stu-id="e24e4-119">true</span></span>](../../../csharp/language-reference/keywords/true.md)
