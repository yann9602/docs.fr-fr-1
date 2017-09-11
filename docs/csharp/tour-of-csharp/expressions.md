---
title: "Expressions C# - Visite guidée du langage C#"
description: "Les expressions, opérandes et opérateurs sont des blocs de construction du langage C#"
keywords: ".NET, csharp, expression, opérateur, opérande"
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 155804dd212d8eda8d81ce7e296a9fe308e9c69b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="expressions"></a><span data-ttu-id="8e0f3-104">Expressions</span><span class="sxs-lookup"><span data-stu-id="8e0f3-104">Expressions</span></span>

<span data-ttu-id="8e0f3-105">Les *expressions* sont construites à partir de *d’opérandes* et *d’opérateurs*.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-105">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="8e0f3-106">Les opérateurs d’une expression indiquent les opérations à appliquer aux opérandes.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-106">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="8e0f3-107">Parmi les exemples d’opérateurs figurent `+`, `-`, `*`, `/` et `new`.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-107">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="8e0f3-108">Les littéraux, les champs, les variables locales et les expressions sont des exemples d’opérandes.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-108">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="8e0f3-109">Quand une expression contient plusieurs opérateurs, la *priorité* des opérateurs contrôle l'ordre dans lequel les opérateurs individuels sont évalués.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-109">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="8e0f3-110">Par exemple, l’expression `x + y * z` est évaluée comme `x + (y * z)`, car l’opérateur `*` a une priorité plus élevée que `+`.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-110">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="8e0f3-111">Lorsqu’un opérande se produit entre deux opérateurs de même priorité, *l’associativité* des opérateurs détermine l’ordre dans lequel les opérations sont effectuées :</span><span class="sxs-lookup"><span data-stu-id="8e0f3-111">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

*   <span data-ttu-id="8e0f3-112">À l’exception des opérateurs d’assignation, tous les opérateurs binaires sont *associatifs sur leur gauche*, ce qui signifie que les opérations sont effectuées de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-112">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="8e0f3-113">Par exemple, `x + y + z` est évalué comme étant `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-113">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
*   <span data-ttu-id="8e0f3-114">Les opérateurs d’assignation et l’opérateur conditionnel (`?:`) sont *associatifs sur leur droite*, ce qui signifie que les opérations sont effectuées de droite à gauche.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-114">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="8e0f3-115">Par exemple, `x = y = z` est évalué comme étant `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-115">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="8e0f3-116">La priorité et l’associativité peuvent être contrôlées à l’aide de parenthèses.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-116">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="8e0f3-117">Par exemple, `x + y * z` multiplie d’abord `y` par `z`, puis ajoute le résultat à `x`, mais `(x + y) * z` ajoute d’abord `x` et `y`, puis multiplie le résultat par `z`.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-117">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="8e0f3-118">La plupart des opérateurs peuvent être *surchargés*.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-118">Most operators can be *overloaded*.</span></span> <span data-ttu-id="8e0f3-119">La surcharge d’opérateur autorise la spécification d’implémentations d’opérateurs définies par l’utilisateur pour les opérations où l’un des deux opérandes ou les deux sont d’un type classe ou struct défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-119">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="8e0f3-120">Voici un résumé des opérateurs de C# répertoriant les catégories d’opérateurs dans l’ordre de priorité, de la plus élevée à la plus basse.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-120">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="8e0f3-121">Les opérateurs de la même catégorie ont la même priorité.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-121">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="8e0f3-122">Sous chaque catégorie se trouve une liste d’expressions dans cette catégorie, ainsi que la description de ce type d’expression.</span><span class="sxs-lookup"><span data-stu-id="8e0f3-122">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="8e0f3-123">Principale</span><span class="sxs-lookup"><span data-stu-id="8e0f3-123">Primary</span></span>
    - <span data-ttu-id="8e0f3-124">`x.m` : Accès au membre</span><span class="sxs-lookup"><span data-stu-id="8e0f3-124">`x.m`: Member access</span></span>
    - <span data-ttu-id="8e0f3-125">`x(...)` : Méthode et appel de délégué</span><span class="sxs-lookup"><span data-stu-id="8e0f3-125">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="8e0f3-126">`x[...]` : Tableau et accès d'indexeur</span><span class="sxs-lookup"><span data-stu-id="8e0f3-126">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="8e0f3-127">`x++` : Post-incrémentation</span><span class="sxs-lookup"><span data-stu-id="8e0f3-127">`x++`: Post-increment</span></span>
    - <span data-ttu-id="8e0f3-128">`x--` : Post-décrémentation</span><span class="sxs-lookup"><span data-stu-id="8e0f3-128">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="8e0f3-129">`new T(...)` : Création d'objet et de délégué</span><span class="sxs-lookup"><span data-stu-id="8e0f3-129">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="8e0f3-130">`new T(...){...}` : Création d'objet avec l'initialiseur</span><span class="sxs-lookup"><span data-stu-id="8e0f3-130">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="8e0f3-131">`new {...}` : Initialiseur d'objet anonyme</span><span class="sxs-lookup"><span data-stu-id="8e0f3-131">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="8e0f3-132">`new T[...]` : Création de tableau</span><span class="sxs-lookup"><span data-stu-id="8e0f3-132">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="8e0f3-133">`typeof(T)` : Permet d’obtenir l’objet @System.Type pour `T`</span><span class="sxs-lookup"><span data-stu-id="8e0f3-133">`typeof(T)`: Obtain @System.Type object for `T`</span></span>
    - <span data-ttu-id="8e0f3-134">`checked(x)` : Évaluer l'expression dans le contexte vérifié (checked)</span><span class="sxs-lookup"><span data-stu-id="8e0f3-134">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="8e0f3-135">`unchecked(x)` : Évaluer l'expression dans le contexte non vérifié (unchecked)</span><span class="sxs-lookup"><span data-stu-id="8e0f3-135">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="8e0f3-136">`default(T)` : Obtenir la valeur par défaut de type `T`</span><span class="sxs-lookup"><span data-stu-id="8e0f3-136">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="8e0f3-137">`delegate {...}` : Fonction anonyme (méthode anonyme)</span><span class="sxs-lookup"><span data-stu-id="8e0f3-137">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="8e0f3-138">Unaire</span><span class="sxs-lookup"><span data-stu-id="8e0f3-138">Unary</span></span>
    - <span data-ttu-id="8e0f3-139">`+x` : Identité</span><span class="sxs-lookup"><span data-stu-id="8e0f3-139">`+x`: Identity</span></span>
    - <span data-ttu-id="8e0f3-140">`-x` : Négation</span><span class="sxs-lookup"><span data-stu-id="8e0f3-140">`-x`: Negation</span></span>
    - <span data-ttu-id="8e0f3-141">`!x` : Négation logique</span><span class="sxs-lookup"><span data-stu-id="8e0f3-141">`!x`: Logical negation</span></span>
    - <span data-ttu-id="8e0f3-142">`~x` : Négation d'opération de bits</span><span class="sxs-lookup"><span data-stu-id="8e0f3-142">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="8e0f3-143">`++x` : Pré-incrémentation</span><span class="sxs-lookup"><span data-stu-id="8e0f3-143">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="8e0f3-144">`--x` : Pré-décrémentation</span><span class="sxs-lookup"><span data-stu-id="8e0f3-144">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="8e0f3-145">`(T)x` : Convertir explicitement `x` en type `T`</span><span class="sxs-lookup"><span data-stu-id="8e0f3-145">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="8e0f3-146">`await x` : Attendre de façon asynchrone la fin de `x`</span><span class="sxs-lookup"><span data-stu-id="8e0f3-146">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="8e0f3-147">Multiplication</span><span class="sxs-lookup"><span data-stu-id="8e0f3-147">Multiplicative</span></span>
    - <span data-ttu-id="8e0f3-148">`x * y` : Multiplication</span><span class="sxs-lookup"><span data-stu-id="8e0f3-148">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="8e0f3-149">`x / y` : Division</span><span class="sxs-lookup"><span data-stu-id="8e0f3-149">`x / y`: Division</span></span>
    - <span data-ttu-id="8e0f3-150">`x % y` : Reste</span><span class="sxs-lookup"><span data-stu-id="8e0f3-150">`x % y`: Remainder</span></span>
* <span data-ttu-id="8e0f3-151">Addition</span><span class="sxs-lookup"><span data-stu-id="8e0f3-151">Additive</span></span>
    - <span data-ttu-id="8e0f3-152">`x + y` : Addition, concaténation de chaînes, combinaison de délégués</span><span class="sxs-lookup"><span data-stu-id="8e0f3-152">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="8e0f3-153">`x – y` : Soustraction, suppression de délégué</span><span class="sxs-lookup"><span data-stu-id="8e0f3-153">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="8e0f3-154">Shift</span><span class="sxs-lookup"><span data-stu-id="8e0f3-154">Shift</span></span>
    - <span data-ttu-id="8e0f3-155">`x << y` : Décalage à gauche</span><span class="sxs-lookup"><span data-stu-id="8e0f3-155">`x << y`: Shift left</span></span>
    - <span data-ttu-id="8e0f3-156">`x >> y` : Décalage à droite</span><span class="sxs-lookup"><span data-stu-id="8e0f3-156">`x >> y`: Shift right</span></span>
* <span data-ttu-id="8e0f3-157">Relations et test de type</span><span class="sxs-lookup"><span data-stu-id="8e0f3-157">Relational and type testing</span></span>
    - <span data-ttu-id="8e0f3-158">`x < y` : Inférieur à</span><span class="sxs-lookup"><span data-stu-id="8e0f3-158">`x < y`: Less than</span></span>
    - <span data-ttu-id="8e0f3-159">`x > y` : Supérieur à</span><span class="sxs-lookup"><span data-stu-id="8e0f3-159">`x > y`: Greater than</span></span>
    - <span data-ttu-id="8e0f3-160">`x <= y` : Inférieur ou égal</span><span class="sxs-lookup"><span data-stu-id="8e0f3-160">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="8e0f3-161">`x >= y` : Supérieur ou égal</span><span class="sxs-lookup"><span data-stu-id="8e0f3-161">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="8e0f3-162">`x is T` : Renvoie `true` si `x` est un `T`, `false` dans le cas contraire</span><span class="sxs-lookup"><span data-stu-id="8e0f3-162">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="8e0f3-163">`x as T` : Renvoie `x` de type `T`, ou `null` si `x` n’est pas un `T`</span><span class="sxs-lookup"><span data-stu-id="8e0f3-163">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="8e0f3-164">Égalité</span><span class="sxs-lookup"><span data-stu-id="8e0f3-164">Equality</span></span>
    - <span data-ttu-id="8e0f3-165">`x == y` : Égal</span><span class="sxs-lookup"><span data-stu-id="8e0f3-165">`x == y`: Equal</span></span>
    - <span data-ttu-id="8e0f3-166">`x != y` : Différent de</span><span class="sxs-lookup"><span data-stu-id="8e0f3-166">`x != y`: Not equal</span></span>
* <span data-ttu-id="8e0f3-167">AND logique</span><span class="sxs-lookup"><span data-stu-id="8e0f3-167">Logical AND</span></span>
    - <span data-ttu-id="8e0f3-168">`x & y` : Opération de bits entière AND, Boolean logique AND</span><span class="sxs-lookup"><span data-stu-id="8e0f3-168">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="8e0f3-169">XOR logique</span><span class="sxs-lookup"><span data-stu-id="8e0f3-169">Logical XOR</span></span>
    - <span data-ttu-id="8e0f3-170">`x ^ y` : Opération de bits entière XOR, Boolean logique XOR</span><span class="sxs-lookup"><span data-stu-id="8e0f3-170">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="8e0f3-171">OR logique</span><span class="sxs-lookup"><span data-stu-id="8e0f3-171">Logical OR</span></span>
    - <span data-ttu-id="8e0f3-172">`x | y` ; Opération de bits entière OR, Boolean logique OR</span><span class="sxs-lookup"><span data-stu-id="8e0f3-172">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="8e0f3-173">AND conditionnel</span><span class="sxs-lookup"><span data-stu-id="8e0f3-173">Conditional AND</span></span>
    - <span data-ttu-id="8e0f3-174">`x && y` : Prend la valeur `y` uniquement si `x` n’est pas `false`</span><span class="sxs-lookup"><span data-stu-id="8e0f3-174">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="8e0f3-175">OR conditionnel</span><span class="sxs-lookup"><span data-stu-id="8e0f3-175">Conditional OR</span></span>
    - <span data-ttu-id="8e0f3-176">`x || y` : Prend la valeur `y` uniquement si `x` n’est pas `true`</span><span class="sxs-lookup"><span data-stu-id="8e0f3-176">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="8e0f3-177">Fusion de Null</span><span class="sxs-lookup"><span data-stu-id="8e0f3-177">Null coalescing</span></span>
    - <span data-ttu-id="8e0f3-178">`x ?? y`: Prend la valeur `y` si `x` est null, `x` dans le cas contraire</span><span class="sxs-lookup"><span data-stu-id="8e0f3-178">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="8e0f3-179">Conditionnel</span><span class="sxs-lookup"><span data-stu-id="8e0f3-179">Conditional</span></span>
    - <span data-ttu-id="8e0f3-180">`x ? y : z` : Évalue `y` so `x` est `true`, `z` si `x` est `false`</span><span class="sxs-lookup"><span data-stu-id="8e0f3-180">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="8e0f3-181">Attribution ou fonction anonyme</span><span class="sxs-lookup"><span data-stu-id="8e0f3-181">Assignment or anonymous function</span></span>
    - <span data-ttu-id="8e0f3-182">`x = y` : Attribution</span><span class="sxs-lookup"><span data-stu-id="8e0f3-182">`x = y`: Assignment</span></span>
    - <span data-ttu-id="8e0f3-183">`x op= y` : Assignation composée ; les opérateurs pris en charge sont</span><span class="sxs-lookup"><span data-stu-id="8e0f3-183">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="8e0f3-184">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="8e0f3-184">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="8e0f3-185">`(T x) => y` : Fonction anonyme (expression lambda)</span><span class="sxs-lookup"><span data-stu-id="8e0f3-185">`(T x) => y`: Anonymous function (lambda expression)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="8e0f3-186">[Précédent](types-and-variables.md)
[Suivant](statements.md)</span><span class="sxs-lookup"><span data-stu-id="8e0f3-186">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>

