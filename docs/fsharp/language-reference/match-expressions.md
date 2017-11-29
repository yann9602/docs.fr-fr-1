---
title: Expressions match (F#)
description: "Découvrez comment l’expression de correspondance F # fournit le contrôle de branchement basé sur la comparaison d’une expression avec un jeu de modèles."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8854b713-255a-408d-942a-e80ab52fd2a4
ms.openlocfilehash: c8b9be744cfa7bc76f0d663b12abd66f8757fc56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="match-expressions"></a><span data-ttu-id="4bd39-104">Expressions match</span><span class="sxs-lookup"><span data-stu-id="4bd39-104">Match Expressions</span></span>

<span data-ttu-id="4bd39-105">Le `match` expression fournit le contrôle de branchement basé sur la comparaison d’une expression avec un jeu de modèles.</span><span class="sxs-lookup"><span data-stu-id="4bd39-105">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="4bd39-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bd39-106">Syntax</span></span>

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a><span data-ttu-id="4bd39-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="4bd39-107">Remarks</span></span>

<span data-ttu-id="4bd39-108">Les expressions de critères spéciaux autorisent des branchements complexes basés sur la comparaison d’une expression de test avec un jeu de modèles.</span><span class="sxs-lookup"><span data-stu-id="4bd39-108">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="4bd39-109">Dans le `match` expression, le *test-expression* est comparé à chaque modèle à son tour, lorsqu’une correspondance est trouvée, correspondant *expression de résultat* est évaluée et la valeur résultante est retourné en tant que la valeur de l’expression de correspondance.</span><span class="sxs-lookup"><span data-stu-id="4bd39-109">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="4bd39-110">La fonction présentée dans la syntaxe précédente mise en correspondance est une expression lambda dans le modèle de recherche est effectuée immédiatement sur l’argument.</span><span class="sxs-lookup"><span data-stu-id="4bd39-110">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="4bd39-111">Les critères spéciaux de fonction présentée dans la syntaxe précédente est équivalente à la suivante.</span><span class="sxs-lookup"><span data-stu-id="4bd39-111">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```    

<span data-ttu-id="4bd39-112">Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda : le `fun` mot clé](functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="4bd39-112">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="4bd39-113">L’ensemble de modèles doit couvrir toutes les correspondances possibles de la variable d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4bd39-113">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="4bd39-114">Souvent, vous utilisez le modèle de caractère générique (`_`) comme dernier modèle pour faire correspondre les valeurs d’entrée précédemment sans correspondance.</span><span class="sxs-lookup"><span data-stu-id="4bd39-114">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="4bd39-115">Le code suivant illustre quelques-unes des façons d’utiliser le `match` expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="4bd39-115">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="4bd39-116">Pour une référence et des exemples de tous les modèles qui peuvent être utilisés, consultez [recherche de correspondance](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="4bd39-116">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="4bd39-117">Gardes sur des modèles</span><span class="sxs-lookup"><span data-stu-id="4bd39-117">Guards on Patterns</span></span>

<span data-ttu-id="4bd39-118">Vous pouvez utiliser un `when` clause pour spécifier une condition supplémentaire répondant à la variable doit correspondre à un modèle.</span><span class="sxs-lookup"><span data-stu-id="4bd39-118">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="4bd39-119">Une telle clause est appelée un *protection*.</span><span class="sxs-lookup"><span data-stu-id="4bd39-119">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="4bd39-120">L’expression qui suit le `when` mot clé n’est pas évaluée, sauf si une correspondance est établie pour le modèle associé à ce garde.</span><span class="sxs-lookup"><span data-stu-id="4bd39-120">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="4bd39-121">L’exemple suivant illustre l’utilisation d’un garde pour spécifier une plage numérique pour un modèle de variable.</span><span class="sxs-lookup"><span data-stu-id="4bd39-121">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="4bd39-122">Notez que plusieurs conditions sont combinées à l’aide d’opérateurs booléens.</span><span class="sxs-lookup"><span data-stu-id="4bd39-122">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="4bd39-123">Notez qu’étant donné que les valeurs autres que des littéraux ne peut pas être utilisés dans le modèle, vous devez utiliser un `when` clause si vous devez comparer une partie de l’entrée à une valeur.</span><span class="sxs-lookup"><span data-stu-id="4bd39-123">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="4bd39-124">Ceci est illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="4bd39-124">This is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

## <a name="see-also"></a><span data-ttu-id="4bd39-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bd39-125">See Also</span></span>

[<span data-ttu-id="4bd39-126">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="4bd39-126">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="4bd39-127">Modèles actifs</span><span class="sxs-lookup"><span data-stu-id="4bd39-127">Active Patterns</span></span>](active-patterns.md)

[<span data-ttu-id="4bd39-128">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="4bd39-128">Pattern Matching</span></span>](pattern-matching.md)
