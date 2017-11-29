---
title: Modules (F#)
description: "Découvrez comment un module F # est un regroupement de code F #, telles que les valeurs, les types et les valeurs de la fonction dans un programme F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 46de2d18-da51-40fa-a262-92edecada79d
ms.openlocfilehash: 89401c1f889be6c5585a302e3a7ac62478573b95
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="modules"></a><span data-ttu-id="772a7-104">Modules</span><span class="sxs-lookup"><span data-stu-id="772a7-104">Modules</span></span>

<span data-ttu-id="772a7-105">Dans le contexte du langage F #, une *module* est un regroupement de code F #, telles que les valeurs, les types et les valeurs de la fonction dans un programme F #.</span><span class="sxs-lookup"><span data-stu-id="772a7-105">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="772a7-106">Le regroupement de code en modules vous permet de centraliser le code connexe et d’éviter les conflits de nom dans votre programme.</span><span class="sxs-lookup"><span data-stu-id="772a7-106">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="772a7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="772a7-107">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="772a7-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="772a7-108">Remarks</span></span>
<span data-ttu-id="772a7-109">Un module F # est un regroupement de constructions de code F # tels que les types, les valeurs, les valeurs de fonction et les code dans `do` liaisons.</span><span class="sxs-lookup"><span data-stu-id="772a7-109">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="772a7-110">Il est implémenté comme une classe du common language runtime (CLR) qui comporte uniquement des membres statiques.</span><span class="sxs-lookup"><span data-stu-id="772a7-110">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="772a7-111">Il existe deux types de déclarations de module, selon que la totalité du fichier est inclus dans le module : une déclaration de module de niveau supérieur et une déclaration de module locale.</span><span class="sxs-lookup"><span data-stu-id="772a7-111">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="772a7-112">Une déclaration de module de niveau supérieur comprend la totalité du fichier dans le module.</span><span class="sxs-lookup"><span data-stu-id="772a7-112">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="772a7-113">Une déclaration de module de niveau supérieur peut apparaître uniquement comme la première déclaration dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="772a7-113">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="772a7-114">Dans la syntaxe de la déclaration de module de niveau supérieur, le paramètre facultatif *espace de noms qualifié* est la séquence de noms de l’espace de noms imbriqué qui contient le module.</span><span class="sxs-lookup"><span data-stu-id="772a7-114">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="772a7-115">L’espace de noms qualifié pas nécessairement être déclaré précédemment.</span><span class="sxs-lookup"><span data-stu-id="772a7-115">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="772a7-116">Vous n’avez pas à mettre en retrait les déclarations dans un module de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="772a7-116">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="772a7-117">Vous n’avez pas à mettre en retrait toutes les déclarations dans les modules locaux.</span><span class="sxs-lookup"><span data-stu-id="772a7-117">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="772a7-118">Dans une déclaration de module locale, seules les déclarations apparaissent en retrait sous cette déclaration de module font partie du module.</span><span class="sxs-lookup"><span data-stu-id="772a7-118">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="772a7-119">Si un fichier de code ne commence pas par une déclaration de module de niveau supérieur ou une déclaration d’espace de noms, tout le contenu du fichier, y compris tous les modules locaux, devient partie d’un module de niveau supérieur créé implicitement qui porte le même nom que le fichier, sans l’extension, avec la première lettre convertie en majuscules.</span><span class="sxs-lookup"><span data-stu-id="772a7-119">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="772a7-120">Par exemple, considérez le fichier suivant.</span><span class="sxs-lookup"><span data-stu-id="772a7-120">For example, consider the following file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="772a7-121">Ce fichier est compilé comme s’il était écrit de cette manière :</span><span class="sxs-lookup"><span data-stu-id="772a7-121">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="772a7-122">Si vous avez plusieurs modules dans un fichier, vous devez utiliser une déclaration de module locale pour chaque module.</span><span class="sxs-lookup"><span data-stu-id="772a7-122">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="772a7-123">Si un espace de noms englobant est déclaré, ces modules font partie de l’espace de noms englobant.</span><span class="sxs-lookup"><span data-stu-id="772a7-123">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="772a7-124">Si un espace de noms englobant n’est pas déclaré, les modules font partie du module de niveau supérieur créé implicitement.</span><span class="sxs-lookup"><span data-stu-id="772a7-124">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="772a7-125">L’exemple de code suivant montre un fichier de code qui contient plusieurs modules.</span><span class="sxs-lookup"><span data-stu-id="772a7-125">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="772a7-126">Le compilateur crée implicitement un module de niveau supérieur nommé `Multiplemodules`, et `MyModule1` et `MyModule2` sont imbriqués dans ce module de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="772a7-126">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="772a7-127">Si vous avez plusieurs fichiers dans un projet ou dans une compilation unique, ou si vous créez une bibliothèque, vous devez inclure une déclaration d’espace de noms ou module en haut du fichier.</span><span class="sxs-lookup"><span data-stu-id="772a7-127">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="772a7-128">Le compilateur F # détermine uniquement un nom de module implicitement qu’un seul fichier dans une ligne de commande de compilation ou de projet, et lorsque vous créez une application.</span><span class="sxs-lookup"><span data-stu-id="772a7-128">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="772a7-129">Le *modificateur d’accessibilité* peut prendre l’une des opérations suivantes : `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="772a7-129">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="772a7-130">Pour plus d’informations, consultez [Contrôle d’accès](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="772a7-130">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="772a7-131">La valeur par défaut est « public ».</span><span class="sxs-lookup"><span data-stu-id="772a7-131">The default is public.</span></span>


## <a name="referencing-code-in-modules"></a><span data-ttu-id="772a7-132">Code de référencement dans des Modules</span><span class="sxs-lookup"><span data-stu-id="772a7-132">Referencing Code in Modules</span></span>
<span data-ttu-id="772a7-133">Lorsque vous référencez des fonctions, des types et des valeurs à partir d’un autre module, vous devez utiliser un nom qualifié ou d’ouvrir le module.</span><span class="sxs-lookup"><span data-stu-id="772a7-133">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="772a7-134">Si vous utilisez un nom qualifié, vous devez spécifier les espaces de noms, le module et l’identificateur de l’élément de programme.</span><span class="sxs-lookup"><span data-stu-id="772a7-134">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="772a7-135">En séparant chaque partie du chemin d’accès qualifié par un point (.), comme suit.</span><span class="sxs-lookup"><span data-stu-id="772a7-135">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="772a7-136">Vous pouvez ouvrir le module ou la valeur d’un ou plusieurs des espaces de noms pour simplifier le code.</span><span class="sxs-lookup"><span data-stu-id="772a7-136">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="772a7-137">Pour plus d’informations sur les espaces de noms lors de l’ouverture et de modules, consultez [déclarations d’importation : le `open` mot clé](import-declarations-the-open-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="772a7-137">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="772a7-138">L’exemple de code suivant montre un module de niveau supérieur qui contient tout le code jusqu'à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="772a7-138">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="772a7-139">Pour utiliser ce code à partir d’un autre fichier dans le même projet, vous utiliser des noms qualifiés ou ouvrir le module avant d’utiliser les fonctions, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="772a7-139">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="772a7-140">Modules imbriqués</span><span class="sxs-lookup"><span data-stu-id="772a7-140">Nested Modules</span></span>
<span data-ttu-id="772a7-141">Les modules peuvent être imbriquées.</span><span class="sxs-lookup"><span data-stu-id="772a7-141">Modules can be nested.</span></span> <span data-ttu-id="772a7-142">Modules internes doivent être mis en retrait aussi loin que les déclarations de module externe pour indiquer qu’ils sont des modules internes, pas de nouveaux modules.</span><span class="sxs-lookup"><span data-stu-id="772a7-142">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="772a7-143">Par exemple, comparez les deux exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="772a7-143">For example, compare the following two examples.</span></span> <span data-ttu-id="772a7-144">Module `Z` est un module interne dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="772a7-144">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="772a7-145">Mais le module `Z` est un frère du module `Y` dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="772a7-145">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="772a7-146">Module `Z` est également un module frère dans le code suivant, car il n’est pas mise en retrait aussi loin que d’autres déclarations de module `Y`.</span><span class="sxs-lookup"><span data-stu-id="772a7-146">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="772a7-147">Enfin, si le module externe a pas de déclarations et est suivi immédiatement par une autre déclaration de module, la nouvelle déclaration de module est considéré comme un module interne, mais le compilateur vous avertit si la deuxième définition de module n’est pas mise en retrait par à la première.</span><span class="sxs-lookup"><span data-stu-id="772a7-147">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="772a7-148">Pour éliminer l’avertissement, mettre en retrait le module interne.</span><span class="sxs-lookup"><span data-stu-id="772a7-148">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="772a7-149">Si vous souhaitez que tout le code dans un fichier dans un module externe unique et que vous souhaitez des modules internes, le module externe ne requiert pas le signe égal, et les déclarations, y compris toutes les déclarations de module interne qui iront dans le module externe n’ont pas à être mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="772a7-149">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="772a7-150">Les déclarations dans les déclarations de module interne doivent être mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="772a7-150">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="772a7-151">Le code suivant illustre ce cas.</span><span class="sxs-lookup"><span data-stu-id="772a7-151">The following code shows this case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="module-rec-allowing-mutual-recursive-code-at-the-module-level"></a><span data-ttu-id="772a7-152">Module `rec`: permettant à du code récursive mutuelle au niveau du module</span><span class="sxs-lookup"><span data-stu-id="772a7-152">Module `rec`: allowing mutual recursive code at the module level</span></span>

<span data-ttu-id="772a7-153">F # 4.1 introduit la notion de modules permettant à tous les contenus du code mutuellement récursive.</span><span class="sxs-lookup"><span data-stu-id="772a7-153">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="772a7-154">Cette opération est effectuée `module rec`.</span><span class="sxs-lookup"><span data-stu-id="772a7-154">This is done via `module rec`.</span></span>  <span data-ttu-id="772a7-155">Utilisation de `module rec` peut atténuer certains problèmes dans l’impossibilité d’écrire du code mutuellement référentielle entre les types et des modules.</span><span class="sxs-lookup"><span data-stu-id="772a7-155">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="772a7-156">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="772a7-156">The following is an example of this:</span></span>

```fsharp
module rec RecursiveModule =
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

    module private BananaHelpers =
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

<span data-ttu-id="772a7-157">Notez que l’exception `DontSqueezeTheBananaException` et la classe `Banana` font référence à l’autre.</span><span class="sxs-lookup"><span data-stu-id="772a7-157">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="772a7-158">En outre, le module `BananaHelpers` et la classe `Banana` également faire référence à l’autre.</span><span class="sxs-lookup"><span data-stu-id="772a7-158">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="772a7-159">Cela ne serait pas possible d’exprimer dans F #, si vous avez supprimé le `rec` (mot clé) à partir de la `RecursiveModule` module.</span><span class="sxs-lookup"><span data-stu-id="772a7-159">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="772a7-160">Cette fonctionnalité est également possible dans [espaces de noms](namespaces.md) 4.1 F #.</span><span class="sxs-lookup"><span data-stu-id="772a7-160">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="772a7-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="772a7-161">See Also</span></span>

<span data-ttu-id="772a7-162">[Référence du langage F #](index.md)
[espaces de noms](namespaces.md)
[F # RFC FS-1009 - autoriser les modules et types mutuellement référentielles sur étendues supérieure dans les fichiers](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)</span><span class="sxs-lookup"><span data-stu-id="772a7-162">[F# Language Reference](index.md)
[Namespaces](namespaces.md)
[F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)</span></span>
