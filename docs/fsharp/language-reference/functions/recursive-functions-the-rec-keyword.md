---
title: "Fonctions récursives : mot clé rec (F#)"
description: "Découvrez comment le mot clé F # 'rec' est utilisé avec le mot clé 'let' pour définir une fonction récursive."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1a95639f-9bfe-4f1d-a5e2-246d1d37776e
ms.openlocfilehash: b837d2c0f8e2b1d28980620103097ccc8345c098
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="2ad69-104">Fonctions récursives : mot clé rec</span><span class="sxs-lookup"><span data-stu-id="2ad69-104">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="2ad69-105">Le `rec` (mot clé) est utilisé conjointement avec le `let` mot clé pour définir une fonction récursive.</span><span class="sxs-lookup"><span data-stu-id="2ad69-105">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>


## <a name="syntax"></a><span data-ttu-id="2ad69-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ad69-106">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="2ad69-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="2ad69-107">Remarks</span></span>
<span data-ttu-id="2ad69-108">Les fonctions récursives, les fonctions qui appellent elles-mêmes, sont identifiées de façon explicite dans le langage F #.</span><span class="sxs-lookup"><span data-stu-id="2ad69-108">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="2ad69-109">Cela permet l’identificateur qui est défini dans la portée de la fonction.</span><span class="sxs-lookup"><span data-stu-id="2ad69-109">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="2ad69-110">Le code suivant illustre une fonction récursive qui calcule le  *n* ème nombre de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="2ad69-110">The following code illustrates a recursive function that computes the *n*th Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="2ad69-111">Dans la pratique, code ci-dessus comme cela est gaspille de la mémoire et le temps processeur, car il implique le recalcul des valeurs précédemment calculées.</span><span class="sxs-lookup"><span data-stu-id="2ad69-111">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>


<span data-ttu-id="2ad69-112">Les méthodes sont implicitement récursives dans le type ; Il n’est pas nécessaire d’ajouter le `rec` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="2ad69-112">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="2ad69-113">Liaisons let dans les classes ne sont pas implicitement récursives.</span><span class="sxs-lookup"><span data-stu-id="2ad69-113">Let bindings within classes are not implicitly recursive.</span></span>


## <a name="mutually-recursive-functions"></a><span data-ttu-id="2ad69-114">Fonctions mutuellement récursives</span><span class="sxs-lookup"><span data-stu-id="2ad69-114">Mutually Recursive Functions</span></span>
<span data-ttu-id="2ad69-115">Parfois, les fonctions sont *mutuellement récursives*, ce qui signifie que les appels forment un cercle, où une fonction appelle une autre qui à son tour appelle la première, avec n’importe quel nombre d’appels entre les deux.</span><span class="sxs-lookup"><span data-stu-id="2ad69-115">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="2ad69-116">Vous devez définir de telles fonctions un `let` de liaison, à l’aide de la `and` (mot clé) pour lier les.</span><span class="sxs-lookup"><span data-stu-id="2ad69-116">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="2ad69-117">L’exemple suivant montre deux mutuellement les fonctions récursives.</span><span class="sxs-lookup"><span data-stu-id="2ad69-117">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="2ad69-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ad69-118">See Also</span></span>
[<span data-ttu-id="2ad69-119">Fonctions</span><span class="sxs-lookup"><span data-stu-id="2ad69-119">Functions</span></span>](index.md)
