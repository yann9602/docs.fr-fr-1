---
title: "Propriétés indexées (F#)"
description: "En savoir plus sur les propriétés indexées F #, qui sont des propriétés qui fournissent un accès de type tableau aux données classées."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f1266b8b-e2e3-4f49-9332-65c6d34dc0f3
ms.openlocfilehash: 78a09a70621e82f073346471e68ec826359641d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="indexed-properties"></a><span data-ttu-id="02ec4-104">Propriétés indexées</span><span class="sxs-lookup"><span data-stu-id="02ec4-104">Indexed Properties</span></span>

<span data-ttu-id="02ec4-105">*Propriétés indexées* sont classées les propriétés qui fournissent un accès de type tableau aux données.</span><span class="sxs-lookup"><span data-stu-id="02ec4-105">*Indexed properties* are properties that provide array-like access to ordered data.</span></span>


## <a name="syntax"></a><span data-ttu-id="02ec4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02ec4-106">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.PropertyName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.PropertyName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.PropertyName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.PropertyName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a><span data-ttu-id="02ec4-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="02ec4-107">Remarks</span></span>
<span data-ttu-id="02ec4-108">Les trois formes de la syntaxe précédente montrent comment définir des propriétés indexées qui ont à la fois un `get` et un `set` (méthode), ont un `get` uniquement, méthode ou avoir un `set` méthode uniquement.</span><span class="sxs-lookup"><span data-stu-id="02ec4-108">The three forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="02ec4-109">Vous pouvez également combiner les deux la syntaxe indiquée pour get uniquement et la syntaxe indiquée pour set uniquement et produire une propriété qui a get et set.</span><span class="sxs-lookup"><span data-stu-id="02ec4-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="02ec4-110">Cette dernière forme vous permet de placer les modificateurs d’accessibilité différente et les attributs sur get et de définir des méthodes.</span><span class="sxs-lookup"><span data-stu-id="02ec4-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="02ec4-111">Lorsque le *PropertyName* est `Item`, le compilateur traite la propriété comme une propriété indexée par défaut.</span><span class="sxs-lookup"><span data-stu-id="02ec4-111">When the *PropertyName* is `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="02ec4-112">A *propriété indexée par défaut* est une propriété que vous pouvez accéder à l’aide de la syntaxe de type tableau sur l’instance d’objet.</span><span class="sxs-lookup"><span data-stu-id="02ec4-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="02ec4-113">Par exemple, si `obj` est un objet du type qui définit cette propriété, la syntaxe `obj.[index]` est utilisé pour accéder à la propriété.</span><span class="sxs-lookup"><span data-stu-id="02ec4-113">For example, if `obj` is an object of the type that defines this property, the syntax `obj.[index]` is used to access the property.</span></span>

<span data-ttu-id="02ec4-114">La syntaxe pour l’accès à une propriété indexée par défaut est de fournir le nom de la propriété et l’index entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="02ec4-114">The syntax for accessing a nondefault indexed property is to provide the name of the property and the index in parentheses.</span></span> <span data-ttu-id="02ec4-115">Par exemple, si la propriété est `Ordinal`, vous écrivez `obj.Ordinal(index)` pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="02ec4-115">For example, if the property is `Ordinal`, you write `obj.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="02ec4-116">Quelle que soit la forme que vous utilisez, vous devez toujours utiliser le formulaire curryfié pour le `set` méthode sur une propriété indexée.</span><span class="sxs-lookup"><span data-stu-id="02ec4-116">Regardless of which form you use, you should always use the curried form for the `set` method on an indexed property.</span></span> <span data-ttu-id="02ec4-117">Pour plus d’informations sur les fonctions curryfiées, consultez [fonctions](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="02ec4-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="02ec4-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="02ec4-118">Example</span></span>

<span data-ttu-id="02ec4-119">L’exemple de code suivant illustre la définition et l’utilisation de la valeur par défaut et les propriétés indexées non définies par défaut et définir des méthodes get.</span><span class="sxs-lookup"><span data-stu-id="02ec4-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="02ec4-120">Sortie</span><span class="sxs-lookup"><span data-stu-id="02ec4-120">Output</span></span>

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="02ec4-121">Propriétés indexées avec plusieurs Variables d’Index</span><span class="sxs-lookup"><span data-stu-id="02ec4-121">Indexed Properties with Multiple Index Variables</span></span>
<span data-ttu-id="02ec4-122">Les propriétés indexées peuvent avoir plus d’une variable d’index.</span><span class="sxs-lookup"><span data-stu-id="02ec4-122">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="02ec4-123">Dans ce cas, les variables sont séparées par des virgules lorsque la propriété est utilisée.</span><span class="sxs-lookup"><span data-stu-id="02ec4-123">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="02ec4-124">La méthode set dans une telle propriété doit avoir deux arguments curryfiés, le premier étant un tuple qui contient les clés et le second est la valeur définie.</span><span class="sxs-lookup"><span data-stu-id="02ec4-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="02ec4-125">Le code suivant illustre l’utilisation d’une propriété indexée avec plusieurs variables d’index.</span><span class="sxs-lookup"><span data-stu-id="02ec4-125">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="02ec4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02ec4-126">See Also</span></span>
[<span data-ttu-id="02ec4-127">Membres</span><span class="sxs-lookup"><span data-stu-id="02ec4-127">Members</span></span>](index.md)
