---
title: "Boucles : expression for...to (F#)"
description: "Voir comment la boucle for) (F #.. à l’expression est utilisé pour itérer au sein d’une boucle sur une plage de valeurs d’une variable de boucle."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e14c38d9-b1ef-4b7f-be9a-fb6ef6708e02
ms.openlocfilehash: 1a1d71d30b5e87e4691a78acd5032de9419399db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forto-expression"></a><span data-ttu-id="a04a9-104">Boucles : expression for...to</span><span class="sxs-lookup"><span data-stu-id="a04a9-104">Loops: for...to Expression</span></span>

<span data-ttu-id="a04a9-105">Le `for...to` expression est utilisée pour itérer au sein d’une boucle sur une plage de valeurs d’une variable de boucle.</span><span class="sxs-lookup"><span data-stu-id="a04a9-105">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="a04a9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a04a9-106">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="a04a9-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="a04a9-107">Remarks</span></span>
<span data-ttu-id="a04a9-108">Le type de l’identificateur est déduit du type de la *Démarrer* et *Terminer* expressions.</span><span class="sxs-lookup"><span data-stu-id="a04a9-108">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="a04a9-109">Types pour ces expressions doivent être des entiers 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a04a9-109">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="a04a9-110">Bien que techniquement d’une expression, `for...to` plus à une instruction traditionnelle dans un langage de programmation impérative.</span><span class="sxs-lookup"><span data-stu-id="a04a9-110">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="a04a9-111">Le type de retour pour la *expression de corps* doit être `unit`.</span><span class="sxs-lookup"><span data-stu-id="a04a9-111">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="a04a9-112">Les exemples suivants illustrent différentes utilisations de la `for...to` expression.</span><span class="sxs-lookup"><span data-stu-id="a04a9-112">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="a04a9-113">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="a04a9-113">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="a04a9-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a04a9-114">See Also</span></span>
[<span data-ttu-id="a04a9-115">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="a04a9-115">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="a04a9-116">Boucles : expression `for...in`</span><span class="sxs-lookup"><span data-stu-id="a04a9-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="a04a9-117">Boucles : expression `while...do`</span><span class="sxs-lookup"><span data-stu-id="a04a9-117">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
