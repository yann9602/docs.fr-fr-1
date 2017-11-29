---
title: Tuples (F#)
description: "Découvrez le tuple F #, un regroupement de valeurs sans nom, mais ordonnées, de types éventuellement différents."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 35069073-9a82-410f-8dea-912e2a152e6d
ms.openlocfilehash: c6a0565ac7022928f5c2bdad5387d896c6c3d387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="tuples"></a><span data-ttu-id="89cea-104">Tuples</span><span class="sxs-lookup"><span data-stu-id="89cea-104">Tuples</span></span>

<span data-ttu-id="89cea-105">A *tuple* est un regroupement de valeurs sans nom, mais ordonnées, de types éventuellement différents.</span><span class="sxs-lookup"><span data-stu-id="89cea-105">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="89cea-106">Tuples peut s’agir de types référence ou des structures.</span><span class="sxs-lookup"><span data-stu-id="89cea-106">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="89cea-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89cea-107">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a><span data-ttu-id="89cea-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="89cea-108">Remarks</span></span>
<span data-ttu-id="89cea-109">Chaque *élément* dans la syntaxe précédente peut être toute expression valide de F #.</span><span class="sxs-lookup"><span data-stu-id="89cea-109">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="89cea-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="89cea-110">Examples</span></span>
<span data-ttu-id="89cea-111">Les exemples de tuples de paires, triples et ainsi de suite, des types identiques ou différents.</span><span class="sxs-lookup"><span data-stu-id="89cea-111">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="89cea-112">Certains exemples sont illustrés dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="89cea-112">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a><span data-ttu-id="89cea-113">Obtention de valeurs individuelles</span><span class="sxs-lookup"><span data-stu-id="89cea-113">Obtaining Individual Values</span></span>
<span data-ttu-id="89cea-114">Vous pouvez utiliser critères spéciaux pour accéder et affecter des noms pour les éléments de tuple, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="89cea-114">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="89cea-115">Vous pouvez décomposer également un tuple via la recherche de correspondance en dehors d’un `match` expression via `let` liaison :</span><span class="sxs-lookup"><span data-stu-id="89cea-115">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="89cea-116">Ou vous pouvez répéter correspondent dans les tuples comme entrées des fonctions :</span><span class="sxs-lookup"><span data-stu-id="89cea-116">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="89cea-117">Si vous avez besoin qu’un seul élément de tuple, le caractère générique (trait de soulignement) peut être utilisé pour éviter de créer un nouveau nom pour une valeur que vous n’avez pas besoin.</span><span class="sxs-lookup"><span data-stu-id="89cea-117">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="89cea-118">Copier des éléments à partir d’un tuple de référence dans un tuple d’un struct est également simple :</span><span class="sxs-lookup"><span data-stu-id="89cea-118">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="89cea-119">Les fonctions `fst` et `snd` (référencer uniquement les tuples) retourne la première et deuxième élément d’un tuple, respectivement.</span><span class="sxs-lookup"><span data-stu-id="89cea-119">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="89cea-120">Il n’existe aucune fonction intégrée qui renvoie le troisième élément d’un triple, mais vous pouvez facilement écrire une comme suit.</span><span class="sxs-lookup"><span data-stu-id="89cea-120">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="89cea-121">En général, il est préférable d’utiliser des critères spéciaux pour accéder à des éléments individuels d’un tuple.</span><span class="sxs-lookup"><span data-stu-id="89cea-121">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="89cea-122">À l’aide de Tuples</span><span class="sxs-lookup"><span data-stu-id="89cea-122">Using Tuples</span></span>
<span data-ttu-id="89cea-123">Tuples fournissent un moyen pratique de retourner plusieurs valeurs à partir d’une fonction, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="89cea-123">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="89cea-124">Cet exemple effectue une division d’entier et retourne le résultat arrondi de l’opération en tant que premier membre d’une paire de tuple et le reste comme deuxième membre de la paire.</span><span class="sxs-lookup"><span data-stu-id="89cea-124">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="89cea-125">Tuples peuvent également servir en tant qu’arguments de fonction lorsque vous souhaitez éviter la curryfication implicite des arguments de fonction qui est impliquée par la syntaxe de fonction standard.</span><span class="sxs-lookup"><span data-stu-id="89cea-125">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="89cea-126">La syntaxe habituelle pour la définition de la fonction `let sum a b = a + b` vous permet de définir une fonction qui est l’application partielle du premier argument de la fonction, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="89cea-126">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="89cea-127">À l’aide d’un tuple comme paramètre désactive la curryfication.</span><span class="sxs-lookup"><span data-stu-id="89cea-127">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="89cea-128">Pour plus d’informations, consultez « Application partielle d’Arguments » dans [fonctions](functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="89cea-128">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="89cea-129">Noms des Types de Tuple</span><span class="sxs-lookup"><span data-stu-id="89cea-129">Names of Tuple Types</span></span>
<span data-ttu-id="89cea-130">Lorsque vous écrivez le nom d’un type qui est un tuple, vous utilisez la `*` symbole pour séparer les éléments.</span><span class="sxs-lookup"><span data-stu-id="89cea-130">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="89cea-131">Pour un tuple qui se compose d’un `int`, un `float`et un `string`, tel que `(10, 10.0, "ten")`, le type est écrit comme suit.</span><span class="sxs-lookup"><span data-stu-id="89cea-131">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="89cea-132">Interopérabilité avec des Tuples c#</span><span class="sxs-lookup"><span data-stu-id="89cea-132">Interoperation with C# Tuples</span></span>

<span data-ttu-id="89cea-133">C# 7 introduit des tuples de la langue.</span><span class="sxs-lookup"><span data-stu-id="89cea-133">C# 7 introduced tuples to the language.</span></span>  <span data-ttu-id="89cea-134">Tuples dans c# et sont des structures et sont équivalents aux tuples struct en F #.</span><span class="sxs-lookup"><span data-stu-id="89cea-134">Tuples in C# and are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="89cea-135">Si vous avez besoin d’interagir avec c# utilise des tuples, vous devez utiliser des tuples de struct.</span><span class="sxs-lookup"><span data-stu-id="89cea-135">If you need to interoperate with C# uses tuples, you must use struct tuples.</span></span>

<span data-ttu-id="89cea-136">Il est facile à suivre.</span><span class="sxs-lookup"><span data-stu-id="89cea-136">This is easy to do.</span></span>  <span data-ttu-id="89cea-137">Par exemple, imaginez que vous devez passer un tuple à une classe c# et ensuite utiliser son résultat, qui est également un tuple :</span><span class="sxs-lookup"><span data-stu-id="89cea-137">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

<span data-ttu-id="89cea-138">Dans votre code F #, vous pouvez passer un tuple d’un struct comme paramètre et consommer le résultat sous forme de tuple struct.</span><span class="sxs-lookup"><span data-stu-id="89cea-138">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="89cea-139">Conversion entre des Tuples de référence et les Tuples de Struct</span><span class="sxs-lookup"><span data-stu-id="89cea-139">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="89cea-140">Référence Tuples et Struct Tuples ayant une représentation sous-jacente complètement différente, ils ne sont pas implicitement convertibles.</span><span class="sxs-lookup"><span data-stu-id="89cea-140">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="89cea-141">Autrement dit, ne compilez les code semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="89cea-141">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="89cea-142">Vous devez répéter correspondent dans un tuple et construire l’autre avec les parties qui le composent.</span><span class="sxs-lookup"><span data-stu-id="89cea-142">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="89cea-143">Exemple :</span><span class="sxs-lookup"><span data-stu-id="89cea-143">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="89cea-144">Forme compilée de Tuples de référence</span><span class="sxs-lookup"><span data-stu-id="89cea-144">Compiled Form of Reference Tuples</span></span>
<span data-ttu-id="89cea-145">Cette section explique le formulaire de tuples quand elles sont compilées.</span><span class="sxs-lookup"><span data-stu-id="89cea-145">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="89cea-146">Les informations ici n’est pas nécessaire de lire, sauf si vous ciblez .NET Framework 3.5 ou inférieur.</span><span class="sxs-lookup"><span data-stu-id="89cea-146">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="89cea-147">Tuples sont compilés en objets de l’un des divers types génériques, tous appelés `System.Tuple`, qui sont surchargés sur l’arité, nombre de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="89cea-147">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="89cea-148">Types de tuple apparaissent dans cet écran lorsque vous les affichez à partir d’un autre langage, tel que c# ou Visual Basic, ou lorsque vous utilisez un outil qui n’est pas conscient des constructions F #.</span><span class="sxs-lookup"><span data-stu-id="89cea-148">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="89cea-149">Le `Tuple` types ont été introduits dans .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="89cea-149">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="89cea-150">Si vous ciblez une version antérieure du .NET Framework, le compilateur utilise les versions de [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) à partir de la version 2.0 de la bibliothèque principale F #.</span><span class="sxs-lookup"><span data-stu-id="89cea-150">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="89cea-151">Les types dans cette bibliothèque sont utilisés uniquement pour les applications qui ciblent la version 2.0, 3.0 et les versions du .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="89cea-151">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="89cea-152">Transfert de type est utilisé pour assurer la compatibilité binaire entre les composants .NET Framework 2.0 et .NET Framework 4) (F #.</span><span class="sxs-lookup"><span data-stu-id="89cea-152">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="89cea-153">Forme compilée de Tuples d’un Struct</span><span class="sxs-lookup"><span data-stu-id="89cea-153">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="89cea-154">Struct tuples (par exemple, `struct (x, y)`), sont fondamentalement différents à partir des tuples de référence.</span><span class="sxs-lookup"><span data-stu-id="89cea-154">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="89cea-155">Ils sont compilés dans le <xref:System.ValueTuple> type, surchargé par une arité, ou le nombre de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="89cea-155">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="89cea-156">Ils sont équivalents aux [C# 7 Tuples](../../csharp/tuples.md) et [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md)et interagir de façon bidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="89cea-156">They are equivalent to [C# 7 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="89cea-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89cea-157">See Also</span></span>
[<span data-ttu-id="89cea-158">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="89cea-158">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="89cea-159">Types F#</span><span class="sxs-lookup"><span data-stu-id="89cea-159">F# Types</span></span>](fsharp-types.md)
