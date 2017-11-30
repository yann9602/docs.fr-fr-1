---
title: "Boucles : expression while...do (F#)"
description: "Voir comment la while... procédez comme expression est utilisée pour effectuer une exécution itérative (boucle) lorsqu’une condition de test spécifié a la valeur true."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0416ffca-7ed9-4aff-9493-e001fdba8c9b
ms.openlocfilehash: 6a186d75dcda383764949c2cd3b09bc9e3d1080a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="afe6c-104">Boucles : expression while...do</span><span class="sxs-lookup"><span data-stu-id="afe6c-104">Loops: while...do Expression</span></span>

<span data-ttu-id="afe6c-105">Le `while...do` expression est utilisée pour effectuer une exécution itérative (boucle) lorsqu’une condition de test spécifié a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="afe6c-105">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>


## <a name="syntax"></a><span data-ttu-id="afe6c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afe6c-106">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="afe6c-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="afe6c-107">Remarks</span></span>
<span data-ttu-id="afe6c-108">Le *test-expression* est évaluée ; si elle est `true`, le *expression de corps* est exécuté et l’expression de test est réévaluée.</span><span class="sxs-lookup"><span data-stu-id="afe6c-108">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="afe6c-109">Le *expression de corps* doit avoir un type `unit`.</span><span class="sxs-lookup"><span data-stu-id="afe6c-109">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="afe6c-110">Si l’expression de test est `false`, l’itération se termine.</span><span class="sxs-lookup"><span data-stu-id="afe6c-110">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="afe6c-111">L’exemple suivant illustre l’utilisation de la `while...do` expression.</span><span class="sxs-lookup"><span data-stu-id="afe6c-111">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="afe6c-112">La sortie du code précédent est un flux de nombres aléatoires compris entre 1 et 20, le dernier est 10.</span><span class="sxs-lookup"><span data-stu-id="afe6c-112">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
<span data-ttu-id="afe6c-113">Vous pouvez utiliser `while...do` dans les expressions de séquence et autres expressions de calcul, auquel cas une version personnalisée de la `while...do` expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="afe6c-113">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="afe6c-114">Pour plus d’informations, consultez [séquences](sequences.md), [Workflows asynchrones](asynchronous-workflows.md), et [Expressions de calcul](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="afe6c-114">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="afe6c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afe6c-115">See Also</span></span>
[<span data-ttu-id="afe6c-116">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="afe6c-116">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="afe6c-117">Boucles : expression `for...in`</span><span class="sxs-lookup"><span data-stu-id="afe6c-117">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="afe6c-118">Boucles : expression `for...to`</span><span class="sxs-lookup"><span data-stu-id="afe6c-118">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
