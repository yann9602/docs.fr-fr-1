---
title: Liaisons do (F#)
description: "Découvrir comment une liaison de ' do' F # est utilisé pour exécuter du code sans définir de fonction ou une valeur."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4c1057a3-3aa1-4b64-b46a-25ffe33f0be9
ms.openlocfilehash: f2563d384b67c005c96c2ff487c786476d385e70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings"></a><span data-ttu-id="9fbe3-104">Liaisons do</span><span class="sxs-lookup"><span data-stu-id="9fbe3-104">do Bindings</span></span>

<span data-ttu-id="9fbe3-105">A `do` liaison est utilisée pour exécuter du code sans définir de fonction ou une valeur.</span><span class="sxs-lookup"><span data-stu-id="9fbe3-105">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="9fbe3-106">En outre, les liaisons do peuvent être utilisées dans les classes, consultez [ `do` liaisons dans les Classes](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="9fbe3-106">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="9fbe3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fbe3-107">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="9fbe3-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="9fbe3-108">Remarks</span></span>
<span data-ttu-id="9fbe3-109">Utilisez un `do` liaison lorsque vous souhaitez exécuter du code indépendamment d’une définition de fonction ou de valeur.</span><span class="sxs-lookup"><span data-stu-id="9fbe3-109">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="9fbe3-110">L’expression dans une `do` liaison doit retourner `unit`.</span><span class="sxs-lookup"><span data-stu-id="9fbe3-110">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="9fbe3-111">Le code dans un niveau supérieur `do` liaison est exécutée lorsque le module est initialisé.</span><span class="sxs-lookup"><span data-stu-id="9fbe3-111">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="9fbe3-112">Le mot clé `do` est facultatif.</span><span class="sxs-lookup"><span data-stu-id="9fbe3-112">The keyword `do` is optional.</span></span>

<span data-ttu-id="9fbe3-113">Attributs peuvent être appliqués à un niveau supérieur `do` liaison.</span><span class="sxs-lookup"><span data-stu-id="9fbe3-113">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="9fbe3-114">Par exemple, si votre programme utilise COM interop, vous pouvez souhaiter appliquer le `STAThread` d’attribut à votre programme.</span><span class="sxs-lookup"><span data-stu-id="9fbe3-114">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="9fbe3-115">Vous pouvez pour cela à l’aide d’un attribut sur un `do` de liaison, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9fbe3-115">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a><span data-ttu-id="9fbe3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fbe3-116">See Also</span></span>
[<span data-ttu-id="9fbe3-117">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="9fbe3-117">F# Language Reference</span></span>](../index.md)

[<span data-ttu-id="9fbe3-118">Fonctions</span><span class="sxs-lookup"><span data-stu-id="9fbe3-118">Functions</span></span>](index.md)

