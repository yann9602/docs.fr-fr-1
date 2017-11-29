---
title: "Cellules de référence (F#)"
description: "Découvrez comment les cellules de référence de F # sont les emplacements de stockage qui vous permettent de créer des valeurs mutables avec la sémantique de référence."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 09a0b221-ea21-45c4-bae8-5e4a339750c4
ms.openlocfilehash: c7470c9a36cf2cd24dd89ceffcf6e90c6dc4d2dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="reference-cells"></a><span data-ttu-id="084d7-104">Cellules de référence</span><span class="sxs-lookup"><span data-stu-id="084d7-104">Reference Cells</span></span>

<span data-ttu-id="084d7-105">*Cellules de référence* sont des emplacements de stockage qui vous permettent de créer des valeurs mutables avec la sémantique de référence.</span><span class="sxs-lookup"><span data-stu-id="084d7-105">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="084d7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="084d7-106">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="084d7-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="084d7-107">Remarks</span></span>
<span data-ttu-id="084d7-108">Pour créer une cellule de référence qui encapsule la valeur, utilisez l'opérateur `ref`.</span><span class="sxs-lookup"><span data-stu-id="084d7-108">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="084d7-109">Vous pouvez ensuite modifier la valeur sous-jacente, car elle est mutable.</span><span class="sxs-lookup"><span data-stu-id="084d7-109">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="084d7-110">Une cellule de référence contient une valeur réelle, et pas uniquement une adresse.</span><span class="sxs-lookup"><span data-stu-id="084d7-110">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="084d7-111">Lorsque vous créez une cellule de référence à l'aide de l'opérateur `ref`, vous créez une copie de la valeur sous-jacente en tant que valeur mutable encapsulée.</span><span class="sxs-lookup"><span data-stu-id="084d7-111">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="084d7-112">Vous pouvez déréférencer une cellule de référence à l'aide de l'opérateur `!` (bang).</span><span class="sxs-lookup"><span data-stu-id="084d7-112">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="084d7-113">L'exemple de code suivant illustre la déclaration et l'utilisation de cellules de référence.</span><span class="sxs-lookup"><span data-stu-id="084d7-113">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="084d7-114">Le résultat est `50`.</span><span class="sxs-lookup"><span data-stu-id="084d7-114">The output is `50`.</span></span>

<span data-ttu-id="084d7-115">Les cellules de référence sont des instances du type d'enregistrement générique `Ref` qui est déclaré comme suit.</span><span class="sxs-lookup"><span data-stu-id="084d7-115">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="084d7-116">Le type `'a ref` (affiché par le compilateur et IntelliSense dans l'IDE) est un synonyme de `Ref<'a>`</span><span class="sxs-lookup"><span data-stu-id="084d7-116">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="084d7-117">(définition sous-jacente).</span><span class="sxs-lookup"><span data-stu-id="084d7-117">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="084d7-118">L'opérateur `ref` crée une cellule de référence.</span><span class="sxs-lookup"><span data-stu-id="084d7-118">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="084d7-119">Le code suivant est la déclaration de l'opérateur `ref`.</span><span class="sxs-lookup"><span data-stu-id="084d7-119">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="084d7-120">Le tableau suivant répertorie les fonctionnalités disponibles sur la cellule de référence.</span><span class="sxs-lookup"><span data-stu-id="084d7-120">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="084d7-121">Opérateur, membre ou champ</span><span class="sxs-lookup"><span data-stu-id="084d7-121">Operator, member, or field</span></span>|<span data-ttu-id="084d7-122">Description</span><span class="sxs-lookup"><span data-stu-id="084d7-122">Description</span></span>|<span data-ttu-id="084d7-123">Type</span><span class="sxs-lookup"><span data-stu-id="084d7-123">Type</span></span>|<span data-ttu-id="084d7-124">Définition</span><span class="sxs-lookup"><span data-stu-id="084d7-124">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="084d7-125">`!` (opérateur de déréférence)</span><span class="sxs-lookup"><span data-stu-id="084d7-125">`!` (dereference operator)</span></span>|<span data-ttu-id="084d7-126">Retourne la valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="084d7-126">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="084d7-127">`:=` (opérateur d'assignation)</span><span class="sxs-lookup"><span data-stu-id="084d7-127">`:=` (assignment operator)</span></span>|<span data-ttu-id="084d7-128">Modifie la valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="084d7-128">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="084d7-129">`ref` (opérateur)</span><span class="sxs-lookup"><span data-stu-id="084d7-129">`ref` (operator)</span></span>|<span data-ttu-id="084d7-130">Encapsule une valeur dans une nouvelle cellule de référence.</span><span class="sxs-lookup"><span data-stu-id="084d7-130">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="084d7-131">`Value` (propriété)</span><span class="sxs-lookup"><span data-stu-id="084d7-131">`Value` (property)</span></span>|<span data-ttu-id="084d7-132">Obtient ou définit la valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="084d7-132">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="084d7-133">`contents` (champ d'enregistrement)</span><span class="sxs-lookup"><span data-stu-id="084d7-133">`contents` (record field)</span></span>|<span data-ttu-id="084d7-134">Obtient ou définit la valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="084d7-134">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="084d7-135">Vous pouvez accéder à la valeur sous-jacente de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="084d7-135">There are several ways to access the underlying value.</span></span> <span data-ttu-id="084d7-136">La valeur retournée par l'opérateur de déréférence (`!`) n'est pas une valeur assignable.</span><span class="sxs-lookup"><span data-stu-id="084d7-136">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="084d7-137">Par conséquent, si vous modifiez la valeur sous-jacente, vous devez utiliser à la place l'opérateur d'assignation (`:=`).</span><span class="sxs-lookup"><span data-stu-id="084d7-137">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="084d7-138">La propriété `Value` et le champ `contents` sont des valeurs assignables.</span><span class="sxs-lookup"><span data-stu-id="084d7-138">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="084d7-139">Par conséquent, vous pouvez les utiliser pour accéder ou modifier la valeur sous-jacente, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="084d7-139">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="084d7-140">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="084d7-140">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="084d7-141">Le champ `contents` est fourni à des fins de compatibilité avec d'autres versions de ML et produit un avertissement au cours de la compilation.</span><span class="sxs-lookup"><span data-stu-id="084d7-141">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="084d7-142">Pour désactiver l'avertissement, utilisez l'option de compilateur `--mlcompatibility`.</span><span class="sxs-lookup"><span data-stu-id="084d7-142">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="084d7-143">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="084d7-143">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="084d7-144">Le code suivant illustre l'utilisation de cellules de référence dans le cadre du passage de paramètres.</span><span class="sxs-lookup"><span data-stu-id="084d7-144">The following code illustrates the use of reference cells in parameter passing.</span></span> <span data-ttu-id="084d7-145">Le type de l’incrémentation du a une méthode incrément qui prend un paramètre qui inclut le type de paramètre byref.</span><span class="sxs-lookup"><span data-stu-id="084d7-145">The Incrementor type has a method Increment that takes a parameter that includes byref in the parameter type.</span></span> <span data-ttu-id="084d7-146">Dans le type de paramètre byref indique que les appelants doivent passer une cellule de référence ou l’adresse d’une variable normale du type spécifié, dans ce cas int : Le code restant illustre comment appeler un incrément avec ces deux types d’arguments et illustre l’utilisation de l’opérateur ref sur une variable pour créer une cellule de référence (ref myDelta1).</span><span class="sxs-lookup"><span data-stu-id="084d7-146">The byref in the parameter type indicates that callers must pass a reference cell or the address of a typical variable of the specified type, in this case int. The remaining code illustrates how to call Increment with both of these types of arguments, and shows the use of the ref operator on a variable to create a reference cell (ref myDelta1).</span></span> <span data-ttu-id="084d7-147">Il montre ensuite l'utilisation de l'opérateur d'adresse (&amp;) pour générer un argument approprié.</span><span class="sxs-lookup"><span data-stu-id="084d7-147">It then shows the use of the address-of operator (&amp;) to generate an appropriate argument.</span></span> <span data-ttu-id="084d7-148">Enfin, la méthode de l’incrément est appelée à nouveau à l’aide d’une cellule de référence déclarée à l’aide d’une liaison let.</span><span class="sxs-lookup"><span data-stu-id="084d7-148">Finally, the Increment method is called again by using a reference cell that is declared by using a let binding.</span></span> <span data-ttu-id="084d7-149">La dernière ligne de code illustre l’utilisation de la !</span><span class="sxs-lookup"><span data-stu-id="084d7-149">The final line of code demonstrates the use of the !</span></span> <span data-ttu-id="084d7-150">opérateur pour déréférencer la cellule de référence pour l’impression.</span><span class="sxs-lookup"><span data-stu-id="084d7-150">operator to dereference the reference cell for printing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

<span data-ttu-id="084d7-151">Pour plus d’informations sur le passage par référence, consultez [paramètres et Arguments](parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="084d7-151">For more information about how to pass by reference, see [Parameters and Arguments](parameters-and-arguments.md).</span></span>

>[!NOTE]
<span data-ttu-id="084d7-152">Les programmeurs c# doivent savoir que ref différemment en F # fonctionne et en c#.</span><span class="sxs-lookup"><span data-stu-id="084d7-152">C# programmers should know that ref works differently in F# than it does in C#.</span></span> <span data-ttu-id="084d7-153">Par exemple, l’utilisation de ref lorsque vous passez un argument n’a pas le même effet en F # et en c#.</span><span class="sxs-lookup"><span data-stu-id="084d7-153">For example, the use of ref when you pass an argument does not have the same effect in F# as it does in C#.</span></span>

## <a name="consuming-c-ref-returns"></a><span data-ttu-id="084d7-154">Utilisation de c# `ref` retourne</span><span class="sxs-lookup"><span data-stu-id="084d7-154">Consuming C# `ref` returns</span></span>

<span data-ttu-id="084d7-155">À compter de F # 4.1, vous pouvez utiliser `ref` retourne généré en c#.</span><span class="sxs-lookup"><span data-stu-id="084d7-155">Starting with F# 4.1, you can consume `ref` returns generated in C#.</span></span>  <span data-ttu-id="084d7-156">Le résultat de cet appel est un `byref<_>` pointeur.</span><span class="sxs-lookup"><span data-stu-id="084d7-156">The result of such a call is a `byref<_>` pointer.</span></span>

<span data-ttu-id="084d7-157">La méthode c# suivante :</span><span class="sxs-lookup"><span data-stu-id="084d7-157">The following C# method:</span></span>

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

<span data-ttu-id="084d7-158">Peut être appelée en toute transparence par F # avec aucune syntaxe particulière :</span><span class="sxs-lookup"><span data-stu-id="084d7-158">Can be transparently called by F# with no special syntax:</span></span>

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

<span data-ttu-id="084d7-159">Vous pouvez également déclarer des fonctions, ce qui peut prendre un `ref` retourner en tant qu’entrée, par exemple :</span><span class="sxs-lookup"><span data-stu-id="084d7-159">You can also declare functions which could take a `ref` return as input, for example:</span></span>

```fsharp
let f (x: byref<int>) = &x
```

<span data-ttu-id="084d7-160">Il n’existe actuellement aucun moyen de générer un `ref` retour en F #, qui peut être consommé en c#.</span><span class="sxs-lookup"><span data-stu-id="084d7-160">There is currently no way to generate a `ref` return in F# which could be consumed in C#.</span></span>

## <a name="see-also"></a><span data-ttu-id="084d7-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="084d7-161">See Also</span></span>
[<span data-ttu-id="084d7-162">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="084d7-162">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="084d7-163">Paramètres et arguments</span><span class="sxs-lookup"><span data-stu-id="084d7-163">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="084d7-164">Informations de référence des symboles et opérateurs</span><span class="sxs-lookup"><span data-stu-id="084d7-164">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
