---
title: "Expressions conditionnelles : if... then...else (F#)"
description: "Découvrez comment écrire des expressions conditionnelles en F # pour exécuter les différentes branches de code."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e1871c-4d4d-4691-9ab2-bd2c6f65589a
ms.openlocfilehash: 3531a112eb53657d5e9102d5e5f3be988360b76e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="298e4-104">Expressions conditionnelles :`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="298e4-104">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="298e4-105">Le `if...then...else` expression exécute différentes branches de code et prend une valeur différente selon l’expression booléenne donnée.</span><span class="sxs-lookup"><span data-stu-id="298e4-105">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="298e4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="298e4-106">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="298e4-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="298e4-107">Remarks</span></span>
<span data-ttu-id="298e4-108">Dans la syntaxe précédente, *expression1* s’exécute lorsque l’expression booléenne renvoie `true`; sinon, *expression2* s’exécute.</span><span class="sxs-lookup"><span data-stu-id="298e4-108">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="298e4-109">Contrairement à d’autres langages, les `if...then...else` construction est une expression, pas une instruction.</span><span class="sxs-lookup"><span data-stu-id="298e4-109">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="298e4-110">Cela signifie qu’il génère une valeur, ce qui est la valeur de la dernière expression dans la branche qui s’exécute.</span><span class="sxs-lookup"><span data-stu-id="298e4-110">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="298e4-111">Les types des valeurs produites dans chaque branche doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="298e4-111">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="298e4-112">S’il existe n’explicite `else` , son type est `unit`.</span><span class="sxs-lookup"><span data-stu-id="298e4-112">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="298e4-113">Par conséquent, si le type de la `then` branche est d’un type autre que `unit`, il doit y avoir un `else` branche avec le même type de retour.</span><span class="sxs-lookup"><span data-stu-id="298e4-113">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="298e4-114">Lors du chaînage `if...then...else` expressions ensemble, vous pouvez utiliser le mot clé `elif` au lieu de `else if`; ils sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="298e4-114">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="298e4-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="298e4-115">Example</span></span>
<span data-ttu-id="298e4-116">L’exemple suivant illustre comment utiliser le `if...then...else` expression.</span><span class="sxs-lookup"><span data-stu-id="298e4-116">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
John
910 is less than 20
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="298e4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="298e4-117">See Also</span></span>
[<span data-ttu-id="298e4-118">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="298e4-118">F# Language Reference</span></span>](index.md)

