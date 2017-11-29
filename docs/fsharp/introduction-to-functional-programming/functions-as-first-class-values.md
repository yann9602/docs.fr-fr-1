---
title: "Fonctions comme valeurs de première classe (F#)"
description: "Découvrez comment les fonctions sont élevées à l’état de première classe dans le langage de programmation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6b76b93b-a141-40f4-976c-7f0c558d6d09
ms.openlocfilehash: bca0e09edbe0aa86f0db746282acd4f4b3237a03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="functions-as-first-class-values"></a><span data-ttu-id="86598-104">Fonctions comme valeurs de première classe</span><span class="sxs-lookup"><span data-stu-id="86598-104">Functions as First-Class Values</span></span>

<span data-ttu-id="86598-105">Une caractéristique essentielle de langages de programmation fonctionnelle est l’élévation des fonctions à l’état de première classe.</span><span class="sxs-lookup"><span data-stu-id="86598-105">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="86598-106">Vous devez être en mesure de faire avec une fonction tout ce que vous pouvez faire avec les valeurs des autres types intégrés et être en mesure de le faire avec un degré comparable d’effort.</span><span class="sxs-lookup"><span data-stu-id="86598-106">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="86598-107">Les mesures courantes de l’état de première classe sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="86598-107">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="86598-108">Vous liez des fonctions à des identificateurs ?</span><span class="sxs-lookup"><span data-stu-id="86598-108">Can you bind functions to identifiers?</span></span> <span data-ttu-id="86598-109">Autrement dit, pouvez vous donner les noms ?</span><span class="sxs-lookup"><span data-stu-id="86598-109">That is, can you give them names?</span></span>

- <span data-ttu-id="86598-110">Peut stocker les fonctions dans les structures de données, comme dans une liste ?</span><span class="sxs-lookup"><span data-stu-id="86598-110">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="86598-111">Vous passez une fonction en tant qu’argument dans un appel de fonction ?</span><span class="sxs-lookup"><span data-stu-id="86598-111">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="86598-112">Peut retourner d’une fonction à partir d’un appel de fonction ?</span><span class="sxs-lookup"><span data-stu-id="86598-112">Can you return a function from a function call?</span></span>

<span data-ttu-id="86598-113">Les deux dernières mesures définissent ce que l'on appelle *opérations d’ordre supérieur* ou *fonctions d’ordre supérieur*.</span><span class="sxs-lookup"><span data-stu-id="86598-113">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="86598-114">Fonctions d’ordre supérieur acceptent des fonctions en tant qu’arguments et retournent des fonctions en tant que la valeur d’appels de fonction.</span><span class="sxs-lookup"><span data-stu-id="86598-114">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="86598-115">Ces opérations prennent en charge ces éléments de la programmation fonctionnelle que le mappage des fonctions et la composition de fonctions.</span><span class="sxs-lookup"><span data-stu-id="86598-115">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>


## <a name="give-the-value-a-name"></a><span data-ttu-id="86598-116">Donnez un nom à la valeur</span><span class="sxs-lookup"><span data-stu-id="86598-116">Give the Value a Name</span></span>

<span data-ttu-id="86598-117">Si une fonction est une valeur de première classe, vous devez être en mesure de nom, tout comme vous pouvez nommer les entiers, chaînes et autres types intégrés.</span><span class="sxs-lookup"><span data-stu-id="86598-117">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="86598-118">Il s’agit de programmation fonctionnelle comme un identificateur de liaison à une valeur.</span><span class="sxs-lookup"><span data-stu-id="86598-118">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="86598-119">F # utilise [ `let` liaisons](../language-reference/functions/let-bindings.md) pour lier des noms à des valeurs : `let <identifier> = <value>`.</span><span class="sxs-lookup"><span data-stu-id="86598-119">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="86598-120">Le code suivant montre deux exemples.</span><span class="sxs-lookup"><span data-stu-id="86598-120">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="86598-121">Vous pouvez nommer une fonction aussi facilement.</span><span class="sxs-lookup"><span data-stu-id="86598-121">You can name a function just as easily.</span></span> <span data-ttu-id="86598-122">L’exemple suivant définit une fonction nommée `squareIt` par l’identificateur de liaison `squareIt` à la [expression lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="86598-122">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="86598-123">Fonction `squareIt` possède un paramètre, `n`, et elle retourne le carré de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="86598-123">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="86598-124">F # fournit une syntaxe plus concise pour obtenir le même résultat avec moins de saisie.</span><span class="sxs-lookup"><span data-stu-id="86598-124">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="86598-125">Les exemples qui suivent généralement utilisent le premier style `let <function-name> = <lambda-expression>`, mettre en évidence les similitudes entre la déclaration de fonctions et la déclaration d’autres types de valeurs.</span><span class="sxs-lookup"><span data-stu-id="86598-125">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="86598-126">Toutefois, toutes les fonctions nommées peuvent également être écrites avec la syntaxe concise.</span><span class="sxs-lookup"><span data-stu-id="86598-126">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="86598-127">Certains exemples sont écrits dans les deux sens.</span><span class="sxs-lookup"><span data-stu-id="86598-127">Some of the examples are written in both ways.</span></span>


## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="86598-128">Stockez la valeur dans une Structure de données</span><span class="sxs-lookup"><span data-stu-id="86598-128">Store the Value in a Data Structure</span></span>

<span data-ttu-id="86598-129">Une valeur de première classe peut être stockée dans une structure de données.</span><span class="sxs-lookup"><span data-stu-id="86598-129">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="86598-130">Le code suivant présente des exemples qui stockent des valeurs dans les listes et des tuples.</span><span class="sxs-lookup"><span data-stu-id="86598-130">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="86598-131">Pour vérifier qu’un nom de fonction stocké dans un tuple a en fait la valeur d’une fonction, l’exemple suivant utilise le `fst` et `snd` opérateurs pour extraire les éléments de la première et deuxième tuple `funAndArgTuple`.</span><span class="sxs-lookup"><span data-stu-id="86598-131">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="86598-132">Le premier élément dans le tuple est `squareIt` et le deuxième élément est `num`.</span><span class="sxs-lookup"><span data-stu-id="86598-132">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="86598-133">Identificateur `num` est lié dans un précédent exemple à l’entier 10, un argument valide pour le `squareIt` (fonction).</span><span class="sxs-lookup"><span data-stu-id="86598-133">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="86598-134">La deuxième expression applique le premier élément dans le tuple au deuxième élément dans le tuple : `squareIt num`.</span><span class="sxs-lookup"><span data-stu-id="86598-134">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="86598-135">Tout comme l’identificateur `num` et de la valeur entière 10 peut être utilisés indifféremment, peuvent également identificateur `squareIt` et une expression lambda `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="86598-135">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="86598-136">Passez la valeur en tant qu’Argument</span><span class="sxs-lookup"><span data-stu-id="86598-136">Pass the Value as an Argument</span></span>

<span data-ttu-id="86598-137">Si une valeur a un état de première classe dans une langue, vous pouvez le passer en tant qu’argument à une fonction.</span><span class="sxs-lookup"><span data-stu-id="86598-137">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="86598-138">Par exemple, il est fréquent de passer des entiers et des chaînes en tant qu’arguments.</span><span class="sxs-lookup"><span data-stu-id="86598-138">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="86598-139">Le code suivant montre des entiers et les chaînes passées comme arguments en F #.</span><span class="sxs-lookup"><span data-stu-id="86598-139">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="86598-140">Si les fonctions ont l’état de première classe, vous devez être en mesure de les passer en tant qu’arguments de la même façon.</span><span class="sxs-lookup"><span data-stu-id="86598-140">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="86598-141">N’oubliez pas qu’il s’agit de la première caractéristique des fonctions d’ordre supérieur.</span><span class="sxs-lookup"><span data-stu-id="86598-141">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="86598-142">Dans l’exemple suivant, la fonction `applyIt` possède deux paramètres, `op` et `arg`.</span><span class="sxs-lookup"><span data-stu-id="86598-142">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="86598-143">Si vous envoyez une fonction qui a un paramètre pour `op` et un argument approprié pour la fonction `arg`, la fonction retourne le résultat de l’application `op` à `arg`.</span><span class="sxs-lookup"><span data-stu-id="86598-143">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="86598-144">Dans l’exemple suivant, l’argument de fonction et l’argument entier sont envoyées de la même manière, à l’aide de leurs noms.</span><span class="sxs-lookup"><span data-stu-id="86598-144">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="86598-145">La capacité d’envoyer une fonction en tant qu’argument à une autre fonction sous-jacente abstractions communes dans les langages de programmation fonctionnelle, telles que les opérations de mappage ou de filtrage.</span><span class="sxs-lookup"><span data-stu-id="86598-145">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="86598-146">Une opération de mappage, par exemple, est une fonction d’ordre supérieur qui capture le calcul partagé par les fonctions dans une liste, effectuer une opération sur chaque élément, puis retournent une liste des résultats.</span><span class="sxs-lookup"><span data-stu-id="86598-146">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="86598-147">Vous pourriez modifier chaque élément d’une liste de chaînes en majuscules pour incrémenter chaque élément dans une liste d’entiers ou au carré chaque élément.</span><span class="sxs-lookup"><span data-stu-id="86598-147">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="86598-148">La partie erreurs du calcul est le processus récursive qui parcourt la liste et génère la liste des résultats à retourner.</span><span class="sxs-lookup"><span data-stu-id="86598-148">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="86598-149">Cette partie est capturée dans la fonction de mappage.</span><span class="sxs-lookup"><span data-stu-id="86598-149">That part is captured in the mapping function.</span></span> <span data-ttu-id="86598-150">Il vous suffit d’écrire pour une application particulière est la fonction que vous souhaitez appliquer individuellement à chaque élément de liste (ajout, mise au carré, de changement de casse).</span><span class="sxs-lookup"><span data-stu-id="86598-150">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="86598-151">Cette fonction est envoyée en tant qu’argument à la fonction de mappage, tout comme `squareIt` est envoyé à `applyIt` dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="86598-151">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="86598-152">F # fournit des méthodes de mappage pour la plupart des types de collection, notamment [répertorie](../language-reference/lists.md), [tableaux](../language-reference/arrays.md), et [séquences](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="86598-152">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="86598-153">Les exemples suivants utilisent des listes.</span><span class="sxs-lookup"><span data-stu-id="86598-153">The following examples use lists.</span></span> <span data-ttu-id="86598-154">La syntaxe est `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="86598-154">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="86598-155">Pour plus d’informations, consultez [répertorie](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="86598-155">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="86598-156">Retourner la valeur d’un appel de fonction</span><span class="sxs-lookup"><span data-stu-id="86598-156">Return the Value from a Function Call</span></span>

<span data-ttu-id="86598-157">Enfin, si une fonction a un état de première classe dans une langue, vous devez être en mesure de renvoyer la valeur d’un appel de fonction, tout comme vous retournez d’autres types, tels que les entiers et les chaînes.</span><span class="sxs-lookup"><span data-stu-id="86598-157">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="86598-158">Les appels de fonction suivants retournent des entiers et les affichent.</span><span class="sxs-lookup"><span data-stu-id="86598-158">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="86598-159">L’appel de fonction suivant retourne une chaîne.</span><span class="sxs-lookup"><span data-stu-id="86598-159">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="86598-160">L’appel de fonction suivant, déclaré inline, retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="86598-160">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="86598-161">La valeur affichée est `True`.</span><span class="sxs-lookup"><span data-stu-id="86598-161">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="86598-162">La possibilité de retourner une fonction en tant que la valeur d’un appel de fonction est la deuxième caractéristique des fonctions d’ordre supérieur.</span><span class="sxs-lookup"><span data-stu-id="86598-162">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="86598-163">Dans l’exemple suivant, `checkFor` est défini comme une fonction qui accepte un seul argument, `item`et retourne une nouvelle fonction en tant que sa valeur.</span><span class="sxs-lookup"><span data-stu-id="86598-163">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="86598-164">La fonction retournée prend une liste comme argument, `lst`et recherche `item` dans `lst`.</span><span class="sxs-lookup"><span data-stu-id="86598-164">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="86598-165">Si `item` est présent, la fonction retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="86598-165">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="86598-166">Si `item` n’est pas présent, la fonction retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="86598-166">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="86598-167">Comme dans la section précédente, le code suivant utilise une fonction de la liste fournie, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), pour rechercher dans la liste.</span><span class="sxs-lookup"><span data-stu-id="86598-167">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="86598-168">Le code suivant utilise `checkFor` pour créer une nouvelle fonction qui accepte un seul argument, une liste et recherche 7 dans la liste.</span><span class="sxs-lookup"><span data-stu-id="86598-168">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="86598-169">L’exemple suivant utilise l’état de première classe de fonctions en F # pour déclarer une fonction, `compose`, qui retourne une composition de deux arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="86598-169">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
<span data-ttu-id="86598-170">Pour obtenir une version encore plus courte, consultez la section suivante, « Fonctions curryfiées. »</span><span class="sxs-lookup"><span data-stu-id="86598-170">For an even shorter version, see the following section, "Curried Functions."</span></span>


<span data-ttu-id="86598-171">Le code suivant envoie deux fonctions en tant qu’arguments à `compose`, à la fois de qui acceptent un argument unique du même type.</span><span class="sxs-lookup"><span data-stu-id="86598-171">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="86598-172">La valeur de retour est une nouvelle fonction qui est une composition de deux arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="86598-172">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
<span data-ttu-id="86598-173">F # fournit deux opérateurs, `<<` et `>>`, qui composent les fonctions.</span><span class="sxs-lookup"><span data-stu-id="86598-173">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="86598-174">Par exemple, `let squareAndDouble2 = doubleIt << squareIt` est équivalente à `let squareAndDouble = compose doubleIt squareIt` dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="86598-174">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="86598-175">L’exemple de retour d’une fonction en tant que la valeur d’un appel de fonction suivant crée un jeu d’estimation simple.</span><span class="sxs-lookup"><span data-stu-id="86598-175">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="86598-176">Pour créer un jeu, appelez `makeGame` avec la valeur que vous voulez que quelqu'un deviner envoyé pour `target`.</span><span class="sxs-lookup"><span data-stu-id="86598-176">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="86598-177">La valeur de retour de fonction `makeGame` est une fonction qui prend un argument (l’estimation) et indique si l’estimation est correcte.</span><span class="sxs-lookup"><span data-stu-id="86598-177">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="86598-178">Le code suivant appelle `makeGame`, envoi de la valeur `7` pour `target`.</span><span class="sxs-lookup"><span data-stu-id="86598-178">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="86598-179">Identificateur `playGame` est lié à l’expression lambda retournée.</span><span class="sxs-lookup"><span data-stu-id="86598-179">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="86598-180">Par conséquent, `playGame` est une fonction qui prend comme argument une seule valeur pour `guess`.</span><span class="sxs-lookup"><span data-stu-id="86598-180">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a><span data-ttu-id="86598-181">Fonctions curryfiées</span><span class="sxs-lookup"><span data-stu-id="86598-181">Curried Functions</span></span>

<span data-ttu-id="86598-182">La plupart des exemples dans la section précédente peuvent être écrites plus concise en tirant parti des implicite *curryfication* dans les déclarations de fonction F #.</span><span class="sxs-lookup"><span data-stu-id="86598-182">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="86598-183">Curryfication est un processus qui transforme une fonction qui a plusieurs paramètres dans une série de fonctions intégrées, chacune ayant un seul paramètre.</span><span class="sxs-lookup"><span data-stu-id="86598-183">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="86598-184">En F #, les fonctions qui ont plusieurs paramètres sont intrinsèquement curryfiées.</span><span class="sxs-lookup"><span data-stu-id="86598-184">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="86598-185">Par exemple, `compose` à partir de la section précédente peut être écrit comme indiqué dans le style concis suivant, avec trois paramètres.</span><span class="sxs-lookup"><span data-stu-id="86598-185">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="86598-186">Toutefois, le résultat est une fonction d’un paramètre qui retourne une fonction d’un paramètre, qui à son tour retourne une autre fonction d’un paramètre, comme indiqué dans `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="86598-186">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="86598-187">Vous pouvez accéder à cette fonction de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="86598-187">You can access this function in several ways.</span></span> <span data-ttu-id="86598-188">Chacun des exemples suivants retourne et affiche 18.</span><span class="sxs-lookup"><span data-stu-id="86598-188">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="86598-189">Vous pouvez remplacer `compose4` avec `compose4curried` dans chacun des exemples.</span><span class="sxs-lookup"><span data-stu-id="86598-189">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="86598-190">Pour vérifier que la fonction continue à fonctionner comme avant, réessayez les cas de test d’origine.</span><span class="sxs-lookup"><span data-stu-id="86598-190">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
<span data-ttu-id="86598-191">Vous pouvez limiter la curryfication en englobant les paramètres dans les tuples.</span><span class="sxs-lookup"><span data-stu-id="86598-191">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="86598-192">Pour plus d’informations, consultez « Paramètre modèles » dans [paramètres et Arguments](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="86598-192">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="86598-193">L’exemple suivant utilise la curryfication implicite pour écrire une version plus courte de `makeGame`.</span><span class="sxs-lookup"><span data-stu-id="86598-193">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="86598-194">Les détails de `makeGame` construit et retourne le `game` (fonction) sont moins explicite dans ce format, mais vous pouvez vérifier à l’aide de cas de test d’origine que le résultat est le même.</span><span class="sxs-lookup"><span data-stu-id="86598-194">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="86598-195">Pour plus d’informations sur la curryfication, consultez « Application partielle d’Arguments » dans [fonctions](../language-reference/functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="86598-195">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>


## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="86598-196">Identificateur et la définition de fonction sont interchangeables</span><span class="sxs-lookup"><span data-stu-id="86598-196">Identifier and Function Definition Are Interchangeable</span></span>
<span data-ttu-id="86598-197">Le nom de variable `num` dans les précédents exemples a la valeur entière 10 et il n’est pas surprenant dans laquelle `num` est valide, 10 est également valide.</span><span class="sxs-lookup"><span data-stu-id="86598-197">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="86598-198">Est de même des identificateurs de fonction et leurs valeurs : partout où le nom de la fonction peut être utilisé, l’expression lambda à laquelle il est lié peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="86598-198">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="86598-199">L’exemple suivant définit un `Boolean` fonction appelée `isNegative`et utilise ensuite le nom de la fonction et la définition de la fonction de manière interchangeable.</span><span class="sxs-lookup"><span data-stu-id="86598-199">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="86598-200">Les trois exemples suivants retournent et affichent tous `False`.</span><span class="sxs-lookup"><span data-stu-id="86598-200">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="86598-201">Pour mettre une étape supplémentaire, la valeur de remplacement qui `applyIt` lié à pour `applyIt`.</span><span class="sxs-lookup"><span data-stu-id="86598-201">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="86598-202">Les fonctions sont des valeurs de première classe en F #</span><span class="sxs-lookup"><span data-stu-id="86598-202">Functions Are First-Class Values in F#</span></span> #

<span data-ttu-id="86598-203">Les exemples dans les sections précédentes montrent que les fonctions F # satisfont les critères de valeurs de première classe en F #:</span><span class="sxs-lookup"><span data-stu-id="86598-203">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="86598-204">Vous pouvez lier un identificateur à une définition de fonction.</span><span class="sxs-lookup"><span data-stu-id="86598-204">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="86598-205">Vous pouvez stocker une fonction dans une structure de données.</span><span class="sxs-lookup"><span data-stu-id="86598-205">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="86598-206">Vous pouvez passer une fonction en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="86598-206">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="86598-207">Vous pouvez retourner une fonction en tant que la valeur d’un appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="86598-207">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="86598-208">Pour plus d’informations sur F #, consultez le [référence du langage F #](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="86598-208">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="86598-209">Exemple</span><span class="sxs-lookup"><span data-stu-id="86598-209">Example</span></span>

### <a name="description"></a><span data-ttu-id="86598-210">Description</span><span class="sxs-lookup"><span data-stu-id="86598-210">Description</span></span>

<span data-ttu-id="86598-211">Le code suivant contient tous les exemples dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="86598-211">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="86598-212">Code</span><span class="sxs-lookup"><span data-stu-id="86598-212">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a><span data-ttu-id="86598-213">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86598-213">See Also</span></span>

[<span data-ttu-id="86598-214">Listes</span><span class="sxs-lookup"><span data-stu-id="86598-214">Lists</span></span>](../language-reference/lists.md)

[<span data-ttu-id="86598-215">Tuples</span><span class="sxs-lookup"><span data-stu-id="86598-215">Tuples</span></span>](../language-reference/tuples.md)

[<span data-ttu-id="86598-216">Fonctions</span><span class="sxs-lookup"><span data-stu-id="86598-216">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="86598-217">`let`Liaisons</span><span class="sxs-lookup"><span data-stu-id="86598-217">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)

[<span data-ttu-id="86598-218">Expressions lambda : Le `fun` (mot clé)</span><span class="sxs-lookup"><span data-stu-id="86598-218">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
