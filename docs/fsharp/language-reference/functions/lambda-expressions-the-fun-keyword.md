---
title: "Expressions lambda : mot clé fun (F#)"
description: "Découvrez comment utiliser le mot clé F # 'fun' pour définir une expression lambda, qui est une fonction anonyme."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e5d3565c-d7cc-433f-a619-886ed92523a7
ms.openlocfilehash: 09f1c1787bbb4b86ec40f9e973e08104919631aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="1a815-104">Expressions lambda : mot clé fun (F#)</span><span class="sxs-lookup"><span data-stu-id="1a815-104">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="1a815-105">Le `fun` est utilisé pour définir une expression lambda, autrement dit, une fonction anonyme.</span><span class="sxs-lookup"><span data-stu-id="1a815-105">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>


## <a name="syntax"></a><span data-ttu-id="1a815-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a815-106">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="1a815-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="1a815-107">Remarks</span></span>
<span data-ttu-id="1a815-108">Le *la liste des paramètres* se compose généralement de noms et, éventuellement, de types de paramètres.</span><span class="sxs-lookup"><span data-stu-id="1a815-108">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="1a815-109">En règle générale, les *la liste des paramètres* peuvent être composées de n’importe quel modèle F #.</span><span class="sxs-lookup"><span data-stu-id="1a815-109">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="1a815-110">Pour obtenir une liste complète des modèles possibles, consultez [recherche de correspondance](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="1a815-110">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="1a815-111">Les listes de paramètres valides incluent les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="1a815-111">Lists of valid parameters include the following examples.</span></span>

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

<span data-ttu-id="1a815-112">Le *expression* est le corps de la fonction, la dernière expression qui génère une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="1a815-112">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="1a815-113">Exemples d’expressions lambda valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1a815-113">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a><span data-ttu-id="1a815-114">Utilisation d’expressions lambda</span><span class="sxs-lookup"><span data-stu-id="1a815-114">Using Lambda Expressions</span></span>
<span data-ttu-id="1a815-115">Expressions lambda sont particulièrement utiles lorsque vous souhaitez effectuer des opérations sur une liste ou un autre regroupement et souhaitez éviter la définition d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="1a815-115">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="1a815-116">De nombreuses fonctions de bibliothèque F # prennent les valeurs de fonction en tant qu’arguments, et il peut être particulièrement pratique d’utiliser une expression lambda dans ces cas.</span><span class="sxs-lookup"><span data-stu-id="1a815-116">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="1a815-117">Le code suivant applique une expression lambda aux éléments d’une liste.</span><span class="sxs-lookup"><span data-stu-id="1a815-117">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="1a815-118">Dans ce cas, la fonction anonyme ajoute 1 à chaque élément d’une liste.</span><span class="sxs-lookup"><span data-stu-id="1a815-118">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="1a815-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a815-119">See Also</span></span>
[<span data-ttu-id="1a815-120">Fonctions</span><span class="sxs-lookup"><span data-stu-id="1a815-120">Functions</span></span>](index.md)
