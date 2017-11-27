---
title: Espaces de noms (F#)
description: "Découvrez comment un espace de noms F # permet d’organiser le code dans des zones de fonctionnalités connexes en vous permettant de joindre un nom à un regroupement d’éléments de programme."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea42156f-e1b9-4535-9383-b45f46f3f7ca
ms.openlocfilehash: 4378afebe6fd0d9317f734457576dc75d7488bf0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces"></a><span data-ttu-id="68a2c-104">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="68a2c-104">Namespaces</span></span>

<span data-ttu-id="68a2c-105">Un espace de noms vous permet d’organiser le code en zones de fonctionnalités connexes. Pour cela, vous attachez un nom à un regroupement d’éléments de programme.</span><span class="sxs-lookup"><span data-stu-id="68a2c-105">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of program elements.</span></span>


## <a name="syntax"></a><span data-ttu-id="68a2c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68a2c-106">Syntax</span></span>

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="68a2c-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="68a2c-107">Remarks</span></span>
<span data-ttu-id="68a2c-108">Si vous souhaitez placer le code dans un espace de noms, la première déclaration dans le fichier doit déclarer l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="68a2c-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="68a2c-109">Le contenu du fichier entier fait alors partie de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="68a2c-109">The contents of the entire file then become part of the namespace.</span></span>

<span data-ttu-id="68a2c-110">Espaces de noms ne peut pas contenir directement de valeurs et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="68a2c-110">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="68a2c-111">Au lieu de cela, les fonctions et les valeurs doivent être incluses dans les modules et les modules sont inclus dans les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="68a2c-111">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="68a2c-112">Espaces de noms peuvent contenir des types, des modules.</span><span class="sxs-lookup"><span data-stu-id="68a2c-112">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="68a2c-113">Espaces de noms peuvent être déclarés explicitement avec le mot clé d’espace de noms, ou implicitement lors de la déclaration d’un module.</span><span class="sxs-lookup"><span data-stu-id="68a2c-113">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="68a2c-114">Pour déclarer un espace de noms explicitement, utilisez le mot clé namespace suivi du nom de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="68a2c-114">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="68a2c-115">L’exemple suivant montre un fichier de code qui déclare un espace de noms Widgets avec un type et un module inclus dans cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="68a2c-115">The following example shows a code file that declares a namespace Widgets with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="68a2c-116">Si le contenu entier du fichier est dans un module, vous pouvez également déclarer espaces de noms implicitement à l’aide de la `module` (mot clé) et en fournissant le nouveau nom d’espace de noms dans le nom du module complet.</span><span class="sxs-lookup"><span data-stu-id="68a2c-116">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="68a2c-117">L’exemple suivant montre un fichier de code qui déclare un espace de noms `Widgets` et un module `WidgetsModule`, qui contient une fonction.</span><span class="sxs-lookup"><span data-stu-id="68a2c-117">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="68a2c-118">Le code suivant est équivalent au code précédent, mais le module est une déclaration de module locale.</span><span class="sxs-lookup"><span data-stu-id="68a2c-118">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="68a2c-119">Dans ce cas, l’espace de noms doit apparaître sur sa propre ligne.</span><span class="sxs-lookup"><span data-stu-id="68a2c-119">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="68a2c-120">Si plusieurs modules est requise dans le même fichier dans un ou plusieurs espaces de noms, vous devez utiliser des déclarations de module locales.</span><span class="sxs-lookup"><span data-stu-id="68a2c-120">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="68a2c-121">Lorsque vous utilisez des déclarations de module locales, vous ne pouvez pas utiliser l’espace de noms qualifié dans les déclarations de module.</span><span class="sxs-lookup"><span data-stu-id="68a2c-121">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="68a2c-122">Le code suivant montre un fichier qui a une déclaration d’espace de noms et deux déclarations de module locales.</span><span class="sxs-lookup"><span data-stu-id="68a2c-122">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="68a2c-123">Dans ce cas, les modules sont contenus directement dans l’espace de noms ; Il n’existe aucun module créé implicitement qui porte le même nom que le fichier.</span><span class="sxs-lookup"><span data-stu-id="68a2c-123">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="68a2c-124">N’importe quel autre code dans le fichier, tel qu’un `do` , la liaison est dans l’espace de noms mais pas dans les modules internes, vous devez qualifier le membre de module `widgetFunction` en utilisant le nom de module.</span><span class="sxs-lookup"><span data-stu-id="68a2c-124">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="68a2c-125">La sortie de cet exemple est la suivante.</span><span class="sxs-lookup"><span data-stu-id="68a2c-125">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="68a2c-126">Pour plus d’informations, consultez [Modules](modules.md).</span><span class="sxs-lookup"><span data-stu-id="68a2c-126">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="68a2c-127">Espaces de noms imbriqués</span><span class="sxs-lookup"><span data-stu-id="68a2c-127">Nested Namespaces</span></span>
<span data-ttu-id="68a2c-128">Lorsque vous créez un espace de noms imbriqué, vous devez le qualifier complètement.</span><span class="sxs-lookup"><span data-stu-id="68a2c-128">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="68a2c-129">Sinon, vous créez un nouvel espace de noms de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="68a2c-129">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="68a2c-130">Mise en retrait est ignorée dans les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="68a2c-130">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="68a2c-131">L’exemple suivant montre comment déclarer un espace de noms imbriqué.</span><span class="sxs-lookup"><span data-stu-id="68a2c-131">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="68a2c-132">Espaces de noms de fichiers et des assemblys</span><span class="sxs-lookup"><span data-stu-id="68a2c-132">Namespaces in Files and Assemblies</span></span>
<span data-ttu-id="68a2c-133">Espaces de noms peut s’étendre sur plusieurs fichiers dans un projet unique ou de la compilation.</span><span class="sxs-lookup"><span data-stu-id="68a2c-133">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="68a2c-134">Le terme *fragment de l’espace de noms* décrit la partie d’un espace de noms qui est inclus dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="68a2c-134">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="68a2c-135">Espaces de noms peut également couvrir plusieurs assemblys.</span><span class="sxs-lookup"><span data-stu-id="68a2c-135">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="68a2c-136">Par exemple, le `System` espace de noms inclut l’ensemble .NET Framework, qui couvre de nombreux assemblys et qui contient plusieurs espaces de noms imbriqués.</span><span class="sxs-lookup"><span data-stu-id="68a2c-136">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>


## <a name="global-namespace"></a><span data-ttu-id="68a2c-137">Global Namespace</span><span class="sxs-lookup"><span data-stu-id="68a2c-137">Global Namespace</span></span>
<span data-ttu-id="68a2c-138">Vous utilisez l’espace de noms prédéfini `global` pour mettre des noms dans l’espace de noms de niveau supérieur .NET.</span><span class="sxs-lookup"><span data-stu-id="68a2c-138">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="68a2c-139">Vous pouvez également utiliser global pour référencer l’espace de noms .NET niveau supérieur, par exemple, pour résoudre des conflits de noms avec d’autres espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="68a2c-139">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

##

<span data-ttu-id="68a2c-140">F # 4.1 introduit la notion d’espaces de noms permettant à tous les contenus du code mutuellement récursive.</span><span class="sxs-lookup"><span data-stu-id="68a2c-140">F# 4.1 introduces the notion of namespaces which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="68a2c-141">Cette opération est effectuée `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="68a2c-141">This is done via `namespace rec`.</span></span>  <span data-ttu-id="68a2c-142">Utilisation de `namespace rec` peut atténuer certains problèmes dans l’impossibilité d’écrire du code mutuellement référentielle entre les types et des modules.</span><span class="sxs-lookup"><span data-stu-id="68a2c-142">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="68a2c-143">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="68a2c-143">The following is an example of this:</span></span>

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set
    
    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b : Banana) =
        let flip banana =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides banana =
            for side in banana.Sides do
                if side = Unpeeled then
                    side <- Peeled

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

<span data-ttu-id="68a2c-144">Notez que l’exception `DontSqueezeTheBananaException` et la classe `Banana` font référence à l’autre.</span><span class="sxs-lookup"><span data-stu-id="68a2c-144">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="68a2c-145">En outre, le module `BananaHelpers` et la classe `Banana` également faire référence à l’autre.</span><span class="sxs-lookup"><span data-stu-id="68a2c-145">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="68a2c-146">Cela ne serait pas possible d’exprimer dans F #, si vous avez supprimé le `rec` (mot clé) à partir de la `MutualReferences` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="68a2c-146">This would not be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="68a2c-147">Cette fonctionnalité est également disponible pour niveau supérieur [Modules](modules.md) dans F # 4.1 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="68a2c-147">This feature is also available for top-level [Modules](modules.md) in F# 4.1 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="68a2c-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68a2c-148">See Also</span></span>
[<span data-ttu-id="68a2c-149">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="68a2c-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="68a2c-150">Modules</span><span class="sxs-lookup"><span data-stu-id="68a2c-150">Modules</span></span>](modules.md)

[<span data-ttu-id="68a2c-151">F # RFC FS-1009 - autoriser les modules et types mutuellement référentielles sur étendues supérieure dans les fichiers</span><span class="sxs-lookup"><span data-stu-id="68a2c-151">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
