---
title: Types d'exceptions (F#)
description: "Découvrez comment définir et utiliser des types d’exception F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e850205a-b8da-459e-8f6d-cb3510f8f173
ms.openlocfilehash: a0864218841396c0ebdf26c7585e0e5bb778f83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-types"></a><span data-ttu-id="d8eb7-104">Types d'exceptions</span><span class="sxs-lookup"><span data-stu-id="d8eb7-104">Exception Types</span></span>

<span data-ttu-id="d8eb7-105">Il existe deux catégories d’exceptions en F #: les types d’exceptions .NET et les types d’exception F #.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-105">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="d8eb7-106">Cette rubrique décrit comment définir et utiliser des types d’exception F #.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-106">This topic describes how to define and use F# exception types.</span></span>


## <a name="syntax"></a><span data-ttu-id="d8eb7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8eb7-107">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="d8eb7-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="d8eb7-108">Remarks</span></span>
<span data-ttu-id="d8eb7-109">Dans la syntaxe précédente, *-type d’exception* est le nom d’un type d’exception F # nouveau, et *-type d’argument* représente le type d’un argument qui peut être fourni lorsque vous déclenchez une exception de ce type.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-109">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="d8eb7-110">Vous pouvez spécifier plusieurs arguments à l’aide d’un type de tuple pour *-type d’argument*.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-110">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="d8eb7-111">Une définition classique pour une exception F # semblable au suivant.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-111">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="d8eb7-112">Vous pouvez générer une exception de ce type en utilisant la `raise` de fonction, comme suit.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-112">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="d8eb7-113">Vous pouvez utiliser un type d’exception F # directement dans les filtres dans un `try...with` expression, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-113">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="d8eb7-114">Le type d’exception que vous définissez avec la `exception` mot-clé dans F # est un nouveau type qui hérite de `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-114">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>


## <a name="see-also"></a><span data-ttu-id="d8eb7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8eb7-115">See Also</span></span>
[<span data-ttu-id="d8eb7-116">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="d8eb7-116">Exception Handling</span></span>](index.md)

[<span data-ttu-id="d8eb7-117">Exceptions : fonction `raise`</span><span class="sxs-lookup"><span data-stu-id="d8eb7-117">Exceptions: the `raise` Function</span></span>](the-raise-function.md)

[<span data-ttu-id="d8eb7-118">Hiérarchie des exceptions</span><span class="sxs-lookup"><span data-stu-id="d8eb7-118">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
