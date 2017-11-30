---
title: "Exceptions : fonction raise (F#)"
description: "Découvrez comment la fonction F # 'raise' est utilisée pour indiquer qu’une erreur ou une condition exceptionnelle s’est produite."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b00da469-4789-4cdd-9f77-7a2e29f28637
ms.openlocfilehash: dc524a06d075b982a6aa1fd266769bfc7d883517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="de654-104">Exceptions : fonction raise</span><span class="sxs-lookup"><span data-stu-id="de654-104">Exceptions: the raise Function</span></span>

<span data-ttu-id="de654-105">Le `raise` fonction est utilisée pour indiquer qu’une erreur ou une condition exceptionnelle s’est produite.</span><span class="sxs-lookup"><span data-stu-id="de654-105">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="de654-106">Informations sur l’erreur sont capturées dans un objet exception.</span><span class="sxs-lookup"><span data-stu-id="de654-106">Information about the error is captured in an exception object.</span></span>


## <a name="syntax"></a><span data-ttu-id="de654-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de654-107">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="de654-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="de654-108">Remarks</span></span>
<span data-ttu-id="de654-109">Le `raise` fonction génère un objet exception et lance une pile de processus de déroulement.</span><span class="sxs-lookup"><span data-stu-id="de654-109">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="de654-110">Le processus de déroulement de pile est géré par le common language runtime (CLR), par conséquent, le comportement de ce processus est le même, comme dans tout autre langage .NET.</span><span class="sxs-lookup"><span data-stu-id="de654-110">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="de654-111">Le processus de déroulement de pile est une recherche pour un gestionnaire d’exceptions qui correspond à l’exception générée.</span><span class="sxs-lookup"><span data-stu-id="de654-111">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="de654-112">La recherche commence dans le courant `try...with` expression, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="de654-112">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="de654-113">Chaque modèle dans le `with` bloc est activé, dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="de654-113">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="de654-114">Lorsqu’un gestionnaire d’exceptions correspondant est trouvé, l’exception est considérée comme gérée ; Sinon, la pile est déroulée et `with` blocs de la chaîne d’appel sont vérifiées jusqu'à ce qu’un gestionnaire correspondant est trouvé.</span><span class="sxs-lookup"><span data-stu-id="de654-114">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="de654-115">N’importe quel `finally` blocs qui sont rencontrées dans la chaîne d’appel sont également exécutées en séquence comme la pile se déroule.</span><span class="sxs-lookup"><span data-stu-id="de654-115">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="de654-116">Le `raise` fonction est l’équivalent de `throw` en c# ou C++.</span><span class="sxs-lookup"><span data-stu-id="de654-116">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="de654-117">Utilisez `reraise` dans un gestionnaire catch pour propager la même exception en haut de la chaîne d’appel.</span><span class="sxs-lookup"><span data-stu-id="de654-117">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="de654-118">Les exemples de code suivants illustrent l’utilisation de la `raise` fonction génère une exception.</span><span class="sxs-lookup"><span data-stu-id="de654-118">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="de654-119">Le `raise` fonction peut également être utilisée pour lever des exceptions .NET, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="de654-119">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a><span data-ttu-id="de654-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de654-120">See Also</span></span>
[<span data-ttu-id="de654-121">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="de654-121">Exception Handling</span></span>](index.md)

[<span data-ttu-id="de654-122">Types d'exceptions</span><span class="sxs-lookup"><span data-stu-id="de654-122">Exception Types</span></span>](exception-types.md)

[<span data-ttu-id="de654-123">Exceptions : expression `try...with`</span><span class="sxs-lookup"><span data-stu-id="de654-123">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)

[<span data-ttu-id="de654-124">Exceptions : expression `try...finally`</span><span class="sxs-lookup"><span data-stu-id="de654-124">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)

[<span data-ttu-id="de654-125">Exceptions : fonction `failwith`</span><span class="sxs-lookup"><span data-stu-id="de654-125">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)

[<span data-ttu-id="de654-126">Exceptions : fonction `invalidArg`</span><span class="sxs-lookup"><span data-stu-id="de654-126">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
