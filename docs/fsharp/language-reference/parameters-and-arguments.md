---
title: "Paramètres et arguments (F#)"
description: "En savoir plus sur F # prise en charge linguistique pour la définition de paramètres et de passer des arguments aux fonctions, des méthodes et propriétés."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9b37a5c4-9263-4513-822a-fbb0d1004254
ms.openlocfilehash: 50f54bacd9ba7ec20a7151794734f93200df9f2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="4e6bd-104">Paramètres et arguments</span><span class="sxs-lookup"><span data-stu-id="4e6bd-104">Parameters and Arguments</span></span>

<span data-ttu-id="4e6bd-105">Cette rubrique décrit la prise en charge de langage de définition de paramètres et de passer des arguments aux fonctions, des méthodes et propriétés.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-105">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="4e6bd-106">Il inclut des informations sur le passage par référence et comment définir et utiliser des méthodes qui peuvent prendre un nombre variable d’arguments.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-106">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>


## <a name="parameters-and-arguments"></a><span data-ttu-id="4e6bd-107">Paramètres et arguments</span><span class="sxs-lookup"><span data-stu-id="4e6bd-107">Parameters and Arguments</span></span>
<span data-ttu-id="4e6bd-108">Le terme *paramètre* est utilisé pour décrire les noms des valeurs qui sont censées être fournies.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-108">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="4e6bd-109">Le terme *argument* est utilisé pour les valeurs fournies pour chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-109">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="4e6bd-110">Paramètres peuvent être spécifiés sous forme de tuple ou curryfiés, ou dans une combinaison des deux.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-110">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="4e6bd-111">Vous pouvez passer des arguments à l’aide d’un nom de paramètre explicite.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-111">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="4e6bd-112">Les paramètres des méthodes peuvent être spécifiés comme étant facultatifs et une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-112">Parameters of methods can be specified as optional and given a default value.</span></span>


## <a name="parameter-patterns"></a><span data-ttu-id="4e6bd-113">Modèles de paramètre</span><span class="sxs-lookup"><span data-stu-id="4e6bd-113">Parameter Patterns</span></span>
<span data-ttu-id="4e6bd-114">En règle générale, les paramètres fournis à des fonctions et méthodes sont des modèles séparés par des espaces.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-114">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="4e6bd-115">Cela signifie que, en principe, les modèles décrits dans [Expressions de correspondance](match-expressions.md) peut être utilisé dans une liste de paramètres pour une fonction ou un membre.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-115">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="4e6bd-116">Les méthodes utilisent généralement la forme de tuple de passage d’arguments.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-116">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="4e6bd-117">Cela permet d’obtenir un résultat plus clair de la perspective d’autres langages .NET, car la forme de tuple correspond à la façon d’arguments sont passés dans les méthodes .NET.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-117">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="4e6bd-118">Le formulaire curryfié est souvent utilisé avec des fonctions créées à l’aide de `let` liaisons.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-118">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="4e6bd-119">Le pseudo-code suivant montre des exemples de tuple et d’arguments curryfiés.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-119">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="4e6bd-120">Combiner les formes sont possibles lorsque certains arguments sont dans des tuples et que certains ne sont pas.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-120">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="4e6bd-121">Autres modèles peuvent également servir dans les listes de paramètres, mais si le modèle de paramètre ne correspond pas à toutes les entrées possibles, il peut être une correspondance incomplète au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-121">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="4e6bd-122">L’exception `MatchFailureException` est généré lorsque la valeur d’un argument ne correspond pas les modèles spécifiés dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-122">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="4e6bd-123">Le compilateur émet un avertissement lorsqu’un modèle de paramètre accepte des correspondances incomplètes.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-123">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="4e6bd-124">Au moins un autre modèle est souvent utile pour les listes de paramètres, et qui est le modèle de caractère générique.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-124">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="4e6bd-125">Vous utilisez le modèle de caractère générique dans une liste de paramètres lorsque vous souhaitez simplement ignorer tous les arguments sont fournis.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-125">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="4e6bd-126">Le code suivant illustre l’utilisation du modèle de caractère générique dans une liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-126">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="4e6bd-127">Le modèle de caractère générique peut être utile chaque fois que vous n’avez pas besoin des arguments transmis, comme dans le point d’entrée principal à un programme, lorsque vous n’êtes pas intéressé par les arguments de ligne de commande fournis normalement en tant que tableau de chaînes, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-127">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="4e6bd-128">Autres modèles sont parfois utilisées dans les arguments sont les `as` modèle et les modèles d’identificateur associés aux unions discriminées et les modèles actifs.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-128">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="4e6bd-129">Vous pouvez utiliser le modèle d’union discriminée seul cas comme suit.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-129">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="4e6bd-130">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-130">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="4e6bd-131">Modèles actifs peuvent être utiles en tant que paramètres, par exemple, lors de la transformation d’un argument en un format de votre choix, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4e6bd-131">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="4e6bd-132">Vous pouvez utiliser la `as` modèle pour stocker une valeur correspondante comme valeur locale, comme indiqué dans la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-132">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="4e6bd-133">Un autre modèle utilisé parfois est une fonction qui laisse le dernier argument sans nom en fournissant, en tant que le corps de la fonction, une expression lambda qui exécute immédiatement une correspondance de modèle sur l’argument implicite.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-133">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="4e6bd-134">Ceci est la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-134">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="4e6bd-135">Ce code définit une fonction qui accepte une liste générique et retourne `true` si la liste est vide, et `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-135">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="4e6bd-136">L’utilisation de ces techniques permettre rendre le code plus difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-136">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="4e6bd-137">Parfois, les modèles qui impliquent des correspondances incomplètes sont utiles, par exemple, si vous savez que les listes dans votre programme ont uniquement trois éléments, vous pouvez utiliser un modèle semblable à la suivante dans une liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-137">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="4e6bd-138">L’utilisation de modèles qui ont des correspondances incomplètes est mieux réservée pour une création rapide de prototypes et d’autres utilisations temporaires.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-138">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="4e6bd-139">Le compilateur émet un avertissement pour ce code.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-139">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="4e6bd-140">Ces modèles ne peuvent pas couvrir le cas général de toutes les entrées possibles et par conséquent ne conviennent pas aux API de composant.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-140">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="4e6bd-141">Arguments nommés</span><span class="sxs-lookup"><span data-stu-id="4e6bd-141">Named Arguments</span></span>
<span data-ttu-id="4e6bd-142">Les arguments de méthodes peuvent être spécifiés par position dans une liste d’arguments séparée par des virgules, ou passés explicitement à une méthode en fournissant le nom, suivi par un signe égal et la valeur à passer dans.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-142">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="4e6bd-143">S’il est spécifié en fournissant le nom, ils peuvent apparaître dans un ordre différent de celui utilisé dans la déclaration.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-143">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="4e6bd-144">Arguments nommés peuvent rendre le code plus lisible et plus adaptable à certains types de modifications dans l’API, telles que la réorganisation des paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-144">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="4e6bd-145">Arguments nommés sont autorisés uniquement pour les méthodes, pas pour `let`-lié des fonctions, des valeurs de fonction ou des expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-145">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="4e6bd-146">L’exemple de code suivant illustre l’utilisation d’arguments nommés.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-146">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="4e6bd-147">Dans un appel à un constructeur de classe, vous pouvez définir les valeurs des propriétés de la classe à l’aide d’une syntaxe similaire à celle des arguments nommés.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-147">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="4e6bd-148">L’exemple suivant illustre cette syntaxe.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-148">The following example shows this syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="4e6bd-149">Pour plus d’informations, consultez [constructeurs (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="4e6bd-149">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="4e6bd-150">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="4e6bd-150">Optional Parameters</span></span>
<span data-ttu-id="4e6bd-151">Vous pouvez spécifier un paramètre facultatif pour une méthode à l’aide d’un point d’interrogation devant le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-151">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="4e6bd-152">Paramètres facultatifs sont interprétés comme le type d’option F #, vous pouvez les interroger normalement que les types d’options sont interrogées à l’aide un `match` expression avec `Some` et `None`.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-152">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="4e6bd-153">Paramètres facultatifs sont autorisés uniquement sur les membres, et non sur les fonctions créées à l’aide de `let` liaisons.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-153">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="4e6bd-154">Vous pouvez également utiliser une fonction `defaultArg`, qui définit une valeur par défaut d’un argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-154">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="4e6bd-155">Le `defaultArg` fonction prend le paramètre facultatif comme premier argument et la valeur par défaut en tant que la seconde.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-155">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="4e6bd-156">L’exemple suivant illustre l’utilisation des paramètres optionnels.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-156">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="4e6bd-157">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-157">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a><span data-ttu-id="4e6bd-158">Le passage par référence</span><span class="sxs-lookup"><span data-stu-id="4e6bd-158">Passing by Reference</span></span>
<span data-ttu-id="4e6bd-159">F # prend en charge le `byref` mot clé, qui spécifie qu’un paramètre est passé par référence.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-159">F# supports the `byref` keyword, which specifies that a parameter is passed by reference.</span></span> <span data-ttu-id="4e6bd-160">Cela signifie que toute modification apportée à la valeur est conservées après l’exécution de la fonction.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-160">This means that any changes to the value are retained after the execution of the function.</span></span> <span data-ttu-id="4e6bd-161">Les valeurs fournies pour un `byref` paramètre doit être mutable.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-161">Values provided to a `byref` parameter must be mutable.</span></span> <span data-ttu-id="4e6bd-162">Vous pouvez également passer des cellules de référence du type approprié.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-162">Alternatively, you can pass reference cells of the appropriate type.</span></span>

<span data-ttu-id="4e6bd-163">Passage par référence dans les langages .NET est devenu un moyen de retourner plusieurs valeurs à partir d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-163">Passing by reference in .NET languages evolved as a way to return more than one value from a function.</span></span> <span data-ttu-id="4e6bd-164">En F #, vous pouvez retourner un tuple à cette fin, ou utiliser une cellule de référence mutable en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-164">In F#, you can return a tuple for this purpose, or use a mutable reference cell as a parameter.</span></span> <span data-ttu-id="4e6bd-165">Le `byref` paramètre est fourni principalement pour l’interopérabilité avec les bibliothèques .NET.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-165">The `byref` parameter is mainly provided for interoperability with .NET libraries.</span></span>

<span data-ttu-id="4e6bd-166">Les exemples suivants illustrent l’utilisation de la `byref` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="4e6bd-166">The following examples illustrate the use of the `byref` keyword.</span></span> <span data-ttu-id="4e6bd-167">Notez que lorsque vous utilisez une cellule de référence en tant que paramètre, vous devez créer une cellule de référence comme valeur nommée et utiliser comme paramètre, non seulement ajouter la `ref` opérateur, comme indiqué dans le premier appel à `Increment` dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-167">Note that when you use a reference cell as a parameter, you must create a reference cell as a named value and use that as the parameter, not just add the `ref` operator as shown in the first call to `Increment` in the following code.</span></span> <span data-ttu-id="4e6bd-168">Étant donné que la création d’une cellule de référence crée une copie de la valeur sous-jacente, le premier appel incrémente simplement une valeur temporaire.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-168">Because creating a reference cell creates a copy of the underlying value, the first call just increments a temporary value.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

<span data-ttu-id="4e6bd-169">Vous pouvez utiliser un tuple comme valeur de retour pour stocker les `out` paramètres dans les méthodes de bibliothèque .NET.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-169">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="4e6bd-170">Vous pouvez également traiter les `out` paramètre comme un `byref` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-170">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="4e6bd-171">L’exemple de code suivant illustre deux façons.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-171">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="4e6bd-172">Tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="4e6bd-172">Parameter Arrays</span></span>
<span data-ttu-id="4e6bd-173">Il est parfois nécessaire de définir une fonction qui accepte un nombre arbitraire de paramètres de type hétérogène.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-173">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="4e6bd-174">Il ne serait pas pratique de créer toutes les méthodes surchargées possibles pour prendre en compte pour tous les types qui peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-174">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="4e6bd-175">Les implémentations .NET prennent en charge ces méthodes via la fonctionnalité de tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-175">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="4e6bd-176">Une méthode qui prend un tableau de paramètres dans sa signature peut être fournie avec un nombre arbitraire de paramètres.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-176">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="4e6bd-177">Les paramètres sont placés dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-177">The parameters are put into an array.</span></span> <span data-ttu-id="4e6bd-178">Le type des éléments du tableau détermine les types de paramètres qui peuvent être passés à la fonction.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-178">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="4e6bd-179">Si vous définissez le tableau de paramètres avec `System.Object` comme type d’élément, puis le code client peut passer des valeurs de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-179">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="4e6bd-180">En F #, les tableaux de paramètres peuvent uniquement être définies dans les méthodes.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-180">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="4e6bd-181">Ils ne peut pas être utilisés dans des fonctions autonomes ou des fonctions qui sont définies dans des modules.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-181">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="4e6bd-182">Vous définissez un tableau de paramètres à l’aide de la `ParamArray` attribut.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-182">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="4e6bd-183">Le `ParamArray` attribut ne peut être appliqué qu’au dernier paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-183">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="4e6bd-184">Le code suivant illustre l’appel à une méthode .NET qui prend un tableau de paramètres et de la définition d’un type en F # qui a une méthode qui prend un tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="4e6bd-184">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="4e6bd-185">Lors de l’exécution dans un projet, la sortie du code précédent est comme suit :</span><span class="sxs-lookup"><span data-stu-id="4e6bd-185">When run in a project, the output of the previous code is as follows:</span></span>

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="4e6bd-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e6bd-186">See Also</span></span>
[<span data-ttu-id="4e6bd-187">Membres</span><span class="sxs-lookup"><span data-stu-id="4e6bd-187">Members</span></span>](members/index.md)
