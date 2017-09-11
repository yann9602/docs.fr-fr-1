---
title: "?:, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 23
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
ms.openlocfilehash: 794ff53fe471ef23163503f59599b528df127e2e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="cc176-102">?:, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="cc176-102">?: Operator (C# Reference)</span></span>
<span data-ttu-id="cc176-103">L'opérateur conditionnel (`?:`) retourne l'une de deux valeurs selon la valeur d'une expression booléenne.</span><span class="sxs-lookup"><span data-stu-id="cc176-103">The conditional operator (`?:`) returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="cc176-104">Voici la syntaxe de l'opérateur conditionnel.</span><span class="sxs-lookup"><span data-stu-id="cc176-104">Following is the syntax for the conditional operator.</span></span>  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a><span data-ttu-id="cc176-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="cc176-105">Remarks</span></span>  
 <span data-ttu-id="cc176-106">La `condition` est évaluée entre `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="cc176-106">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="cc176-107">Si `condition` est `true`, `first_expression` est évaluée et devient le résultat.</span><span class="sxs-lookup"><span data-stu-id="cc176-107">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="cc176-108">Si `condition` est `false`, `second_expression` est évaluée et devient le résultat.</span><span class="sxs-lookup"><span data-stu-id="cc176-108">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="cc176-109">Seule une des deux expressions peut être évaluée.</span><span class="sxs-lookup"><span data-stu-id="cc176-109">Only one of the two expressions is evaluated.</span></span>  
  
 <span data-ttu-id="cc176-110">Soit le type de `first_expression` et `second_expression` doivent être identiques, soit une conversion implicite doit exister d'un type à un autre.</span><span class="sxs-lookup"><span data-stu-id="cc176-110">Either the type of `first_expression` and `second_expression` must be the same, or an implicit conversion must exist from one type to the other.</span></span>  
  
 <span data-ttu-id="cc176-111">Vous pouvez exprimer des calculs qui pourraient sinon requérir une construction `if-else` plus concise en utilisant l'opérateur conditionnel.</span><span class="sxs-lookup"><span data-stu-id="cc176-111">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="cc176-112">Par exemple, le code suivant utilise en premier lieu une instruction `if`, puis un opérateur conditionnel pour classifier un entier positif ou négatif.</span><span class="sxs-lookup"><span data-stu-id="cc176-112">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>  
  
```  
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 <span data-ttu-id="cc176-113">L'opérateur conditionnel est associatif sur sa droite.</span><span class="sxs-lookup"><span data-stu-id="cc176-113">The conditional operator is right-associative.</span></span> <span data-ttu-id="cc176-114">L'expression `a ? b : c ? d : e` est évaluée comme `a ? b : (c ? d : e)`, et non pas sous la forme `(a ? b : c) ? d : e`.</span><span class="sxs-lookup"><span data-stu-id="cc176-114">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
 <span data-ttu-id="cc176-115">L'opérateur conditionnel ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="cc176-115">The conditional operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc176-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="cc176-116">Example</span></span>  
 <span data-ttu-id="cc176-117">[!code-cs[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="cc176-117">[!code-cs[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc176-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc176-118">See Also</span></span>  
 <span data-ttu-id="cc176-119">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="cc176-119">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="cc176-120">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="cc176-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="cc176-121">[Opérateurs C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="cc176-121">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="cc176-122">[if-else](../../../csharp/language-reference/keywords/if-else.md) </span><span class="sxs-lookup"><span data-stu-id="cc176-122">[if-else](../../../csharp/language-reference/keywords/if-else.md) </span></span>  
 <span data-ttu-id="cc176-123">[Opérateurs ?. et ?](../../../csharp/language-reference/operators/null-conditional-operators.md) </span><span class="sxs-lookup"><span data-stu-id="cc176-123">[?. and ?Operators](../../../csharp/language-reference/operators/null-conditional-operators.md) </span></span>  
 [<span data-ttu-id="cc176-124">?? Opérateur</span><span class="sxs-lookup"><span data-stu-id="cc176-124">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)

