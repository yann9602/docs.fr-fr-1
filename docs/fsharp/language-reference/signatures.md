---
title: Signatures (F#)
description: "Découvrez comment utiliser un fichier de signature F # pour conserver les informations sur les signatures publiques d’un jeu de F # d’éléments de programme, telles que des types, des espaces de noms et des modules."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 76c84a62-b2f6-44ec-8238-e687e2f7d18e
ms.openlocfilehash: d0f71c6472852268303a2d3af2e4b0a3c256704e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="signatures"></a><span data-ttu-id="cc528-104">Signatures</span><span class="sxs-lookup"><span data-stu-id="cc528-104">Signatures</span></span>

<span data-ttu-id="cc528-105">Un fichier de signature contient des informations sur les signatures publiques d’un jeu d’éléments de programme F#, tels que des types, des espaces de noms et des modules.</span><span class="sxs-lookup"><span data-stu-id="cc528-105">A signature file contains information about the public signatures of a set of F# program elements, such as types, namespaces, and modules.</span></span> <span data-ttu-id="cc528-106">Il peut être utilisé pour spécifier l’accessibilité de ces éléments de programme.</span><span class="sxs-lookup"><span data-stu-id="cc528-106">It can be used to specify the accessibility of these program elements.</span></span>


## <a name="remarks"></a><span data-ttu-id="cc528-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="cc528-107">Remarks</span></span>
<span data-ttu-id="cc528-108">Pour chaque fichier de code F#, vous pouvez avoir un *fichier de signature*, qui est un fichier portant le même nom que le fichier de code, mais avec l’extension .fsi au lieu de .fs.</span><span class="sxs-lookup"><span data-stu-id="cc528-108">For each F# code file, you can have a *signature file*, which is a file that has the same name as the code file but with the extension .fsi instead of .fs.</span></span> <span data-ttu-id="cc528-109">Les fichiers de signature peuvent également être ajoutés à la ligne de commande de compilation si vous utilisez la ligne de commande directement.</span><span class="sxs-lookup"><span data-stu-id="cc528-109">Signature files can also be added to the compilation command-line if you are using the command line directly.</span></span> <span data-ttu-id="cc528-110">Pour faire la distinction entre les fichiers de code et les fichiers de signature, les fichiers de code sont parfois appelés *fichiers d’implémentation*.</span><span class="sxs-lookup"><span data-stu-id="cc528-110">To distinguish between code files and signature files, code files are sometimes referred to as *implementation files*.</span></span> <span data-ttu-id="cc528-111">Dans un projet, le fichier de signature doit précéder le fichier de code associé.</span><span class="sxs-lookup"><span data-stu-id="cc528-111">In a project, the signature file should precede the associated code file.</span></span>

<span data-ttu-id="cc528-112">Un fichier de signature décrit les espaces de noms, modules, types et membres dans le fichier d’implémentation correspondant.</span><span class="sxs-lookup"><span data-stu-id="cc528-112">A signature file describes the namespaces, modules, types, and members in the corresponding implementation file.</span></span> <span data-ttu-id="cc528-113">Les informations dans un fichier de signature vous permettent de spécifier les parties du code dans le fichier d’implémentation correspondant auxquelles le code peut accéder à l’extérieur du fichier d’implémentation, ainsi que les parties qui sont internes au fichier d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="cc528-113">You use the information in a signature file to specify what parts of the code in the corresponding implementation file can be accessed from code outside the implementation file, and what parts are internal to the implementation file.</span></span> <span data-ttu-id="cc528-114">Les espaces de noms, modules et types inclus dans le fichier de signature doivent être un sous-ensemble des espaces de noms, des modules et des types inclus dans le fichier d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="cc528-114">The namespaces, modules, and types that are included in the signature file must be a subset of the namespaces, modules, and types that are included in the implementation file.</span></span> <span data-ttu-id="cc528-115">À quelques exceptions près notées plus loin dans cette rubrique, les éléments de langage qui n’apparaissent pas dans le fichier de signature sont considérés comme privés pour le fichier d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="cc528-115">With some exceptions noted later in this topic, those language elements that are not listed in the signature file are considered private to the implementation file.</span></span> <span data-ttu-id="cc528-116">Si aucun fichier de signature n’est trouvé dans le projet ou la ligne de commande, l’accessibilité par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="cc528-116">If no signature file is found in the project or command line, the default accessibility is used.</span></span>

<span data-ttu-id="cc528-117">Pour plus d’informations sur l’accessibilité par défaut, consultez [le contrôle d’accès](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="cc528-117">For more information about the default accessibility, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="cc528-118">Dans un fichier de signature, vous ne répétez pas la définition des types et les implémentations de chaque méthode ou fonction.</span><span class="sxs-lookup"><span data-stu-id="cc528-118">In a signature file, you do not repeat the definition of the types and the implementations of each method or function.</span></span> <span data-ttu-id="cc528-119">Au lieu de cela, vous utilisez la signature pour chaque méthode et fonction, qui sert de spécification complète des fonctionnalités implémentées par un fragment de module ou d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cc528-119">Instead, you use the signature for each method and function, which acts as a complete specification of the functionality that is implemented by a module or namespace fragment.</span></span> <span data-ttu-id="cc528-120">La syntaxe pour une signature de type est la même que celle utilisée dans les déclarations de méthode abstraites dans les interfaces et les classes abstraites, et est également indiquée par IntelliSense et l’interpréteur F# fsi.exe lorsqu’il affiche correctement l’entrée compilée.</span><span class="sxs-lookup"><span data-stu-id="cc528-120">The syntax for a type signature is the same as that used in abstract method declarations in interfaces and abstract classes, and is also shown by IntelliSense and by the F# interpreter fsi.exe when it displays correctly compiled input.</span></span>

<span data-ttu-id="cc528-121">Quand il n’y a pas assez d’informations dans la signature de type pour indiquer si un type est sealed ou non, ou s’il s’agit d’un type d’interface, vous devez ajouter un attribut qui indique la nature du type au compilateur.</span><span class="sxs-lookup"><span data-stu-id="cc528-121">If there is not enough information in the type signature to indicate whether a type is sealed, or whether it is an interface type, you must add an attribute that indicates the nature of the type to the compiler.</span></span> <span data-ttu-id="cc528-122">Les attributs utilisés à cette fin sont décrits dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="cc528-122">Attributes that you use for this purpose are described in the following table.</span></span>



|<span data-ttu-id="cc528-123">Attribut</span><span class="sxs-lookup"><span data-stu-id="cc528-123">Attribute</span></span>|<span data-ttu-id="cc528-124">Description</span><span class="sxs-lookup"><span data-stu-id="cc528-124">Description</span></span>|
|---------|-----------|
|`[<Sealed>]`|<span data-ttu-id="cc528-125">Type qui n’a pas de membres abstraits ou qui ne doit pas être étendu.</span><span class="sxs-lookup"><span data-stu-id="cc528-125">For a type that has no abstract members, or that should not be extended.</span></span>|
|`[<Interface>]`|<span data-ttu-id="cc528-126">Type qui est une interface.</span><span class="sxs-lookup"><span data-stu-id="cc528-126">For a type that is an interface.</span></span>|
<span data-ttu-id="cc528-127">Le compilateur produit une erreur si les attributs ne sont pas cohérents entre la signature et la déclaration dans le fichier d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="cc528-127">The compiler produces an error if the attributes are not consistent between the signature and the declaration in the implementation file.</span></span>

<span data-ttu-id="cc528-128">Utilisez le mot clé `val` pour créer une signature pour une valeur ou une valeur de fonction.</span><span class="sxs-lookup"><span data-stu-id="cc528-128">Use the keyword `val` to create a signature for a value or function value.</span></span> <span data-ttu-id="cc528-129">Le mot clé `type` introduit une signature de type.</span><span class="sxs-lookup"><span data-stu-id="cc528-129">The keyword `type` introduces a type signature.</span></span>

<span data-ttu-id="cc528-130">Vous pouvez générer un fichier de signature à l’aide de l’option de compilateur `--sig` .</span><span class="sxs-lookup"><span data-stu-id="cc528-130">You can generate a signature file by using the `--sig` compiler option.</span></span> <span data-ttu-id="cc528-131">En général, vous n’écrivez pas les fichiers .fsi manuellement.</span><span class="sxs-lookup"><span data-stu-id="cc528-131">Generally, you do not write .fsi files manually.</span></span> <span data-ttu-id="cc528-132">À la place, vous générez des fichiers .fsi à l’aide du compilateur, vous les ajoutez à votre projet, si vous en avez un, et vous les modifiez en supprimant les méthodes et les fonctions que vous ne souhaitez pas rendre accessibles.</span><span class="sxs-lookup"><span data-stu-id="cc528-132">Instead, you generate .fsi files by using the compiler, add them to your project, if you have one, and edit them by removing methods and functions that you do not want to be accessible.</span></span>

<span data-ttu-id="cc528-133">Les signatures de type sont soumises à plusieurs règles :</span><span class="sxs-lookup"><span data-stu-id="cc528-133">There are several rules for type signatures:</span></span>


- <span data-ttu-id="cc528-134">Les abréviations de type dans un fichier d’implémentation ne doivent pas correspondre à un type sans abréviation dans un fichier de signature.</span><span class="sxs-lookup"><span data-stu-id="cc528-134">Type abbreviations in an implementation file must not match a type without an abbreviation in a signature file.</span></span>


- <span data-ttu-id="cc528-135">Les enregistrements et les unions discriminées doivent exposer la totalité ou aucun de leurs champs et constructeurs, et l’ordre dans la signature doit correspondre à celui dans le fichier d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="cc528-135">Records and discriminated unions must expose either all or none of their fields and constructors, and the order in the signature must match the order in the implementation file.</span></span> <span data-ttu-id="cc528-136">Les classes peuvent révéler une partie, la totalité ou aucun des champs et des méthodes dans la signature.</span><span class="sxs-lookup"><span data-stu-id="cc528-136">Classes can reveal some, all, or none of their fields and methods in the signature.</span></span>


- <span data-ttu-id="cc528-137">Les classes et les structures qui ont des constructeurs doivent exposer les déclarations de leurs classes de base (déclaration `inherits` ).</span><span class="sxs-lookup"><span data-stu-id="cc528-137">Classes and structures that have constructors must expose the declarations of their base classes (the `inherits` declaration).</span></span> <span data-ttu-id="cc528-138">En outre, les classes et les structures qui ont des constructeurs doivent exposer toutes leurs méthodes abstraites et leurs déclarations d’interface.</span><span class="sxs-lookup"><span data-stu-id="cc528-138">Also, classes and structures that have constructors must expose all of their abstract methods and interface declarations.</span></span>


- <span data-ttu-id="cc528-139">Les types d’interface doivent révéler toutes leurs méthodes et interfaces.</span><span class="sxs-lookup"><span data-stu-id="cc528-139">Interface types must reveal all their methods and interfaces.</span></span>


<span data-ttu-id="cc528-140">Les signatures de valeur obéissent aux règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc528-140">The rules for value signatures are as follows:</span></span>


- <span data-ttu-id="cc528-141">Les modificateurs d’accessibilité (`public`, `internal`, etc.) et les modificateurs `inline` et `mutable` dans la signature doivent correspondre à ceux présents dans l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="cc528-141">Modifiers for accessibility (`public`, `internal`, and so on) and the `inline` and `mutable` modifiers in the signature must match those in the implementation.</span></span>


- <span data-ttu-id="cc528-142">Le nombre de paramètres de type générique (déduits implicitement ou déclarés explicitement) doit correspondre, et les types et contraintes de type dans les paramètres de type générique doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="cc528-142">The number of generic type parameters (either implicitly inferred or explicitly declared) must match, and the types and type constraints in generic type parameters must match.</span></span>


- <span data-ttu-id="cc528-143">Si l’attribut `Literal` est utilisé, il doit figurer dans la signature et l’implémentation, et la même valeur littérale doit être utilisée pour les deux.</span><span class="sxs-lookup"><span data-stu-id="cc528-143">If the `Literal` attribute is used, it must appear in both the signature and the implementation, and the same literal value must be used for both.</span></span>


- <span data-ttu-id="cc528-144">Le modèle de paramètres (aussi appelé *arité*) des signatures et des implémentations doit être cohérent.</span><span class="sxs-lookup"><span data-stu-id="cc528-144">The pattern of parameters (also known as the *arity*) of signatures and implementations must be consistent.</span></span>


<span data-ttu-id="cc528-145">Le code suivant illustre un exemple de fichier de signature contenant des signatures d’espace de noms, de module, de valeur de fonction et de type avec les attributs appropriés.</span><span class="sxs-lookup"><span data-stu-id="cc528-145">The following code example shows an example of a signature file that has namespace, module, function value, and type signatures together with the appropriate attributes.</span></span> <span data-ttu-id="cc528-146">Il indique également le fichier d’implémentation correspondant.</span><span class="sxs-lookup"><span data-stu-id="cc528-146">It also shows the corresponding implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

<span data-ttu-id="cc528-147">Le code suivant représente le fichier d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="cc528-147">The following code shows the implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a><span data-ttu-id="cc528-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc528-148">See Also</span></span>
[<span data-ttu-id="cc528-149">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="cc528-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="cc528-150">Contrôle d'accès</span><span class="sxs-lookup"><span data-stu-id="cc528-150">Access Control</span></span>](access-control.md)

[<span data-ttu-id="cc528-151">Options du compilateur</span><span class="sxs-lookup"><span data-stu-id="cc528-151">Compiler Options</span></span>](compiler-options.md)
