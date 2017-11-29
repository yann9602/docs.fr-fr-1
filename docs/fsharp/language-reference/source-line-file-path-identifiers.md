---
title: "Identificateurs de ligne, de fichier et de chemin d’accès source (F#)"
description: "Découvrez comment utiliser F # identificateur valeurs intégrées qui vous permettent d’accéder à la source de numéro de ligne, un répertoire et un nom de fichier dans votre code."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4cfe7439-275c-4d08-980b-784e240bbf29
ms.openlocfilehash: 44cc0914226c120f2b877ce3decd25caa6817eec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="9778b-104">Identificateurs de ligne, de fichier et de chemin d’accès source</span><span class="sxs-lookup"><span data-stu-id="9778b-104">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="9778b-105">Les identificateurs `__LINE__`, `__SOURCE_DIRECTORY__` et `__SOURCE_FILE__` sont des valeurs intégrées qui vous permettent d’accéder à la ligne source nombre, les répertoires et les fichiers nom dans votre code.</span><span class="sxs-lookup"><span data-stu-id="9778b-105">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>


## <a name="syntax"></a><span data-ttu-id="9778b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9778b-106">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="9778b-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="9778b-107">Remarks</span></span>
<span data-ttu-id="9778b-108">Chacune de ces valeurs a le type `string`.</span><span class="sxs-lookup"><span data-stu-id="9778b-108">Each of these values has type `string`.</span></span>

<span data-ttu-id="9778b-109">Le tableau suivant récapitule la ligne source, fichier et les identificateurs de chemin d’accès qui sont disponibles en F #.</span><span class="sxs-lookup"><span data-stu-id="9778b-109">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="9778b-110">Ces identificateurs ne sont pas des macros de préprocesseur ; ils sont des valeurs intégrées qui sont reconnus par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="9778b-110">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="9778b-111">Identificateur prédéfini</span><span class="sxs-lookup"><span data-stu-id="9778b-111">Predefined identifier</span></span>|<span data-ttu-id="9778b-112">Description</span><span class="sxs-lookup"><span data-stu-id="9778b-112">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="9778b-113">Prend la valeur de numéro de ligne active, vous envisagez de `#line` directives.</span><span class="sxs-lookup"><span data-stu-id="9778b-113">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="9778b-114">Prend la valeur de chemin d’accès complet en cours du répertoire source, envisagez `#line` directives.</span><span class="sxs-lookup"><span data-stu-id="9778b-114">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="9778b-115">Donne le nom du fichier source et son chemin d’accès, vous envisagez de `#line` directives.</span><span class="sxs-lookup"><span data-stu-id="9778b-115">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="9778b-116">Pour plus d’informations sur la `#line` directive, voir [Directives de compilateur](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="9778b-116">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="9778b-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="9778b-117">Example</span></span>

<span data-ttu-id="9778b-118">L’exemple de code suivant illustre l’utilisation de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="9778b-118">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="9778b-119">Sortie :</span><span class="sxs-lookup"><span data-stu-id="9778b-119">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="9778b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9778b-120">See Also</span></span>
[<span data-ttu-id="9778b-121">Directives de compilateur</span><span class="sxs-lookup"><span data-stu-id="9778b-121">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="9778b-122">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="9778b-122">F# Language Reference</span></span>](index.md)
