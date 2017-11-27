---
title: Extensions de type (F#)
description: "Découvrez comment les extensions de type F # permettent de que vous ajoutez de nouveaux membres à un type d’objet précédemment défini."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c9d7ce27-f5ad-4766-b9e9-34187da5bc24
ms.openlocfilehash: f78f8689e95fc1547f1a2b17c615592c00051f7c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="type-extensions"></a><span data-ttu-id="9132a-104">Extensions de type</span><span class="sxs-lookup"><span data-stu-id="9132a-104">Type Extensions</span></span>

<span data-ttu-id="9132a-105">Extensions de type vous permettent d’ajouter de nouveaux membres à un type d’objet précédemment défini.</span><span class="sxs-lookup"><span data-stu-id="9132a-105">Type extensions let you add new members to a previously defined object type.</span></span>

## <a name="syntax"></a><span data-ttu-id="9132a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9132a-106">Syntax</span></span>

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a><span data-ttu-id="9132a-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="9132a-107">Remarks</span></span>
<span data-ttu-id="9132a-108">Il existe deux formes d’extensions de type qui ont des comportements et une syntaxe légèrement différente.</span><span class="sxs-lookup"><span data-stu-id="9132a-108">There are two forms of type extensions that have slightly different syntax and behavior.</span></span> <span data-ttu-id="9132a-109">Un *extension intrinsèque* est une extension qui s’affiche dans le même espace de noms ou module, dans le même fichier source et dans le même assembly (DLL ou fichier exécutable) que le type étendu.</span><span class="sxs-lookup"><span data-stu-id="9132a-109">An *intrinsic extension* is an extension that appears in the same namespace or module, in the same source file, and in the same assembly (DLL or executable file) as the type being extended.</span></span> <span data-ttu-id="9132a-110">Un *extension facultative* est une extension qui apparaît en dehors du module, espace de noms ou assembly du type en cours d’extension d’origine.</span><span class="sxs-lookup"><span data-stu-id="9132a-110">An *optional extension* is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span> <span data-ttu-id="9132a-111">Les extensions intrinsèques apparaissent sur le type lorsque le type est examiné par réflexion, mais pas des extensions facultatives.</span><span class="sxs-lookup"><span data-stu-id="9132a-111">Intrinsic extensions appear on the type when the type is examined by reflection, but optional extensions do not.</span></span> <span data-ttu-id="9132a-112">Facultatif pour les extensions doivent être dans des modules et sont uniquement dans la portée lorsque le module qui contient l’extension est ouvert.</span><span class="sxs-lookup"><span data-stu-id="9132a-112">Optional extensions must be in modules, and they are only in scope when the module that contains the extension is open.</span></span>

<span data-ttu-id="9132a-113">Dans la syntaxe précédente, *typename* représente le type qui est étendu.</span><span class="sxs-lookup"><span data-stu-id="9132a-113">In the previous syntax, *typename* represents the type that is being extended.</span></span> <span data-ttu-id="9132a-114">N’importe quel type accessible peut être étendu, mais le nom de type doit être un nom de type réel, pas une abréviation de type.</span><span class="sxs-lookup"><span data-stu-id="9132a-114">Any type that can be accessed can be extended, but the type name must be an actual type name, not a type abbreviation.</span></span> <span data-ttu-id="9132a-115">Vous pouvez définir plusieurs membres dans une extension de type.</span><span class="sxs-lookup"><span data-stu-id="9132a-115">You can define multiple members in one type extension.</span></span> <span data-ttu-id="9132a-116">Le *auto-identificateur* représente l’instance de l’objet qui est appelée, comme dans des membres ordinaires.</span><span class="sxs-lookup"><span data-stu-id="9132a-116">The *self-identifier* represents the instance of the object being invoked, just as in ordinary members.</span></span>

<span data-ttu-id="9132a-117">Le `end` mot clé est facultatif dans la syntaxe simplifiée.</span><span class="sxs-lookup"><span data-stu-id="9132a-117">The `end` keyword is optional in lightweight syntax.</span></span>

<span data-ttu-id="9132a-118">Les membres définis dans les extensions de type peuvent être utilisés comme les autres membres sur un type de classe.</span><span class="sxs-lookup"><span data-stu-id="9132a-118">Members defined in type extensions can be used just like other members on a class type.</span></span> <span data-ttu-id="9132a-119">Comme d’autres membres, ils peuvent être statiques ou membres d’instance.</span><span class="sxs-lookup"><span data-stu-id="9132a-119">Like other members, they can be static or instance members.</span></span> <span data-ttu-id="9132a-120">Ces méthodes sont également appelés *les méthodes d’extension*; propriétés sont appelées *propriétés d’extension*, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="9132a-120">These methods are also known as *extension methods*; properties are known as *extension properties*, and so on.</span></span> <span data-ttu-id="9132a-121">Membres d’extension facultatifs sont compilés en membres statiques pour lequel l’instance d’objet est passée implicitement comme premier paramètre.</span><span class="sxs-lookup"><span data-stu-id="9132a-121">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="9132a-122">Toutefois, ils agissent comme si elles étaient des membres d’instance ou des membres statiques en fonction de la façon dont ils sont déclarés.</span><span class="sxs-lookup"><span data-stu-id="9132a-122">However, they act as if they were instance members or static members according to how they are declared.</span></span> <span data-ttu-id="9132a-123">Membres d’extension implicites sont inclus en tant que membres du type et peuvent être utilisés sans restriction.</span><span class="sxs-lookup"><span data-stu-id="9132a-123">Implicit extension members are included as members of the type and can be used without restriction.</span></span>

<span data-ttu-id="9132a-124">Méthodes d’extension ne peut pas être des méthodes virtuelles ou abstraites.</span><span class="sxs-lookup"><span data-stu-id="9132a-124">Extension methods cannot be virtual or abstract methods.</span></span> <span data-ttu-id="9132a-125">Elles peuvent surcharger d’autres méthodes portant le même nom, mais le compilateur donne la préférence des méthodes d’extension non dans le cas d’un appel ambigu.</span><span class="sxs-lookup"><span data-stu-id="9132a-125">They can overload other methods of the same name, but the compiler gives preference to non-extension methods in the case of an ambiguous call.</span></span>

<span data-ttu-id="9132a-126">Si plusieurs extensions de type intrinsèque existent pour un type, tous les membres doivent être uniques.</span><span class="sxs-lookup"><span data-stu-id="9132a-126">If multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="9132a-127">Pour les extensions de type facultatif, les membres dans différentes extensions de type vers le même type peuvent avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="9132a-127">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="9132a-128">Erreurs d’ambiguïté se produisent uniquement si le code client ouvre deux portées différentes qui définissent les mêmes noms de membre.</span><span class="sxs-lookup"><span data-stu-id="9132a-128">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

<span data-ttu-id="9132a-129">Dans l’exemple suivant, un type dans un module a une extension de type intrinsèque.</span><span class="sxs-lookup"><span data-stu-id="9132a-129">In the following example, a type in a module has an intrinsic type extension.</span></span> <span data-ttu-id="9132a-130">Au code client en dehors du module, l’extension de type apparaît comme un membre standard du type à tous les égards.</span><span class="sxs-lookup"><span data-stu-id="9132a-130">To client code outside the module, the type extension appears as a regular member of the type in all respects.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

<span data-ttu-id="9132a-131">Vous pouvez utiliser des extensions de type intrinsèque pour séparer la définition d’un type en sections.</span><span class="sxs-lookup"><span data-stu-id="9132a-131">You can use intrinsic type extensions to separate the definition of a type into sections.</span></span> <span data-ttu-id="9132a-132">Cela peut être utile pour gérer les définitions de type de grande taille, par exemple, pour séparer le code généré par le compilateur et le code créé ou permettent de regrouper de code créés par différentes personnes ou associés à des fonctionnalités différentes.</span><span class="sxs-lookup"><span data-stu-id="9132a-132">This can be useful in managing large type definitions, for example, to keep compiler-generated code and authored code separate or to group together code created by different people or associated with different functionality.</span></span>

<span data-ttu-id="9132a-133">Dans l’exemple suivant, une extension de type facultative étend la `System.Int32` type avec une méthode d’extension `FromString` qui appelle le membre statique `Parse`.</span><span class="sxs-lookup"><span data-stu-id="9132a-133">In the following example, an optional type extension extends the `System.Int32` type with an extension method `FromString` that calls the static member `Parse`.</span></span> <span data-ttu-id="9132a-134">Le `testFromString` méthode montre que le nouveau membre est appelé comme n’importe quel membre d’instance.</span><span class="sxs-lookup"><span data-stu-id="9132a-134">The `testFromString` method demonstrates that the new member is called just like any instance member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

<span data-ttu-id="9132a-135">Le nouveau membre d’instance apparaît comme toute autre méthode de la `Int32` type dans IntelliSense, mais uniquement lorsque le module qui contient l’extension est ouvert ou dans la portée.</span><span class="sxs-lookup"><span data-stu-id="9132a-135">The new instance member will appear like any other method of the `Int32` type in IntelliSense, but only when the module that contains the extension is open or otherwise in scope.</span></span>

## <a name="generic-extension-methods"></a><span data-ttu-id="9132a-136">Méthodes d’Extension générique</span><span class="sxs-lookup"><span data-stu-id="9132a-136">Generic Extension Methods</span></span>
<span data-ttu-id="9132a-137">Avant de F # 3.1, le compilateur F # n’a pas prendre en charge l’utilisation du langage c#-style de méthodes d’extension avec une variable de type générique, type de tableau, type de tuple ou un type de fonction F # comme paramètre de « THI ».</span><span class="sxs-lookup"><span data-stu-id="9132a-137">Before F# 3.1, the F# compiler didn't support the use of C#-style extension methods with a generic type variable, array type, tuple type, or an F# function type as the "this" parameter.</span></span> <span data-ttu-id="9132a-138">F # 3.1 prend en charge l’utilisation de ces membres d’extension.</span><span class="sxs-lookup"><span data-stu-id="9132a-138">F# 3.1 supports the use of these extension members.</span></span>

<span data-ttu-id="9132a-139">Par exemple, dans le code F # 3.1, vous pouvez utiliser les méthodes d’extension avec des signatures qui ressemblent à la syntaxe suivante en c# :</span><span class="sxs-lookup"><span data-stu-id="9132a-139">For example, in F# 3.1 code, you can use extension methods with signatures that resemble the following syntax in C#:</span></span>

```csharp
static member Method<T>(this T input, T other)
```

<span data-ttu-id="9132a-140">Cette approche est particulièrement utile lorsque le paramètre de type générique est limité.</span><span class="sxs-lookup"><span data-stu-id="9132a-140">This approach is particularly useful when the generic type parameter is constrained.</span></span> <span data-ttu-id="9132a-141">En outre, vous pouvez désormais déclarer les membres d’extension comme suit dans le code F # et définir un ensemble supplémentaire, sémantiquement riche de méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="9132a-141">Further, you can now declare extension members like this in F# code and define an additional, semantically rich set of extension methods.</span></span> <span data-ttu-id="9132a-142">En F #, vous définissez généralement les membres d’extension comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="9132a-142">In F#, you usually define extension members as the following example shows:</span></span>

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

<span data-ttu-id="9132a-143">Toutefois, pour un type générique, la variable de type ne peut pas être contraints.</span><span class="sxs-lookup"><span data-stu-id="9132a-143">However, for a generic type, the type variable may not be constrained.</span></span> <span data-ttu-id="9132a-144">Vous pouvez désormais déclarer c#-membre d’extension de style en F # pour contourner cette limitation.</span><span class="sxs-lookup"><span data-stu-id="9132a-144">You can now declare a C#-style extension member in F# to work around this limitation.</span></span> <span data-ttu-id="9132a-145">Lorsque vous combinez ce type de déclaration avec la fonctionnalité inline de F #, vous pouvez présenter les algorithmes génériques en tant que membres d’extension.</span><span class="sxs-lookup"><span data-stu-id="9132a-145">When you combine this kind of declaration with the inline feature of F#, you can present generic algorithms as extension members.</span></span>

<span data-ttu-id="9132a-146">Prenons la déclaration suivante :</span><span class="sxs-lookup"><span data-stu-id="9132a-146">Consider the following declaration:</span></span>

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="9132a-147">À l’aide de cette déclaration, vous pouvez écrire du code qui ressemble à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9132a-147">By using this declaration, you can write code that resembles the following sample.</span></span>

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

<span data-ttu-id="9132a-148">Dans ce code, le même code arithmétique générique est appliqué aux listes de deux types sans surcharge, en définissant un membre de la même extension.</span><span class="sxs-lookup"><span data-stu-id="9132a-148">In this code, the same generic arithmetic code is applied to lists of two types without overloading, by defining a single extension member.</span></span>


## <a name="see-also"></a><span data-ttu-id="9132a-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9132a-149">See Also</span></span>
[<span data-ttu-id="9132a-150">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="9132a-150">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="9132a-151">Membres</span><span class="sxs-lookup"><span data-stu-id="9132a-151">Members</span></span>](members/index.md)
