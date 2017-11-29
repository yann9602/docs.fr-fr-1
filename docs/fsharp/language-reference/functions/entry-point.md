---
title: "Point d'entrée (F#)"
description: "Découvrez comment définir le point d’entrée à un programme F # est compilé en tant qu’un fichier exécutable, où l’exécution démarre formellement."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 91455443-ff9d-4510-a7e9-1560bdcd0bb0
ms.openlocfilehash: 685fd4da67119aa5fcaaffd142a0a17c8f5dc7f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="entry-point"></a><span data-ttu-id="0ac3f-104">Point d'entrée</span><span class="sxs-lookup"><span data-stu-id="0ac3f-104">Entry Point</span></span>

<span data-ttu-id="0ac3f-105">Cette rubrique décrit la méthode que vous utilisez pour définir le point d’entrée à un programme F #.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-105">This topic describes the method that you use to set the entry point to an F# program.</span></span>


## <a name="syntax"></a><span data-ttu-id="0ac3f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ac3f-106">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="0ac3f-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="0ac3f-107">Remarks</span></span>
<span data-ttu-id="0ac3f-108">Dans la syntaxe précédente, *permettent de liaison de fonction* est la définition d’une fonction dans une `let` liaison.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-108">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="0ac3f-109">Le point d’entrée à un programme qui est compilé, car un fichier exécutable est où l’exécution démarre formellement.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-109">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="0ac3f-110">Vous spécifiez le point d’entrée à une application F # en appliquant la `EntryPoint` attribut du programme `main` (fonction).</span><span class="sxs-lookup"><span data-stu-id="0ac3f-110">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="0ac3f-111">Cette fonction (créée à l’aide un `let` liaison) doit être la dernière fonction dans le dernier fichier compilé.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-111">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="0ac3f-112">Le dernier fichier compilé est le dernier fichier dans le projet ou le dernier fichier passé à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-112">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="0ac3f-113">La fonction de point d’entrée a le type `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-113">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="0ac3f-114">Les arguments fournis sur la ligne de commande sont passés à la `main` fonction dans le tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-114">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="0ac3f-115">Le premier élément du tableau est le premier argument ; le nom du fichier exécutable n’est pas inclus dans le tableau, comme dans d’autres langages.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-115">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="0ac3f-116">La valeur de retour est utilisée en tant que le code de sortie pour le processus.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-116">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="0ac3f-117">Zéro indique généralement le cas de réussite ; valeurs différentes de zéro indiquent une erreur.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-117">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="0ac3f-118">Il n’existe aucune convention pour la signification spécifique de codes de retour différente de zéro ; les significations des codes de retour sont spécifiques à l’application.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-118">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="0ac3f-119">L’exemple suivant illustre un simple `main` (fonction).</span><span class="sxs-lookup"><span data-stu-id="0ac3f-119">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="0ac3f-120">Lorsque ce code est exécuté avec la ligne de commande `EntryPoint.exe 1 2 3`, la sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-120">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="0ac3f-121">Point d’entrée implicite</span><span class="sxs-lookup"><span data-stu-id="0ac3f-121">Implicit Entry Point</span></span>
<span data-ttu-id="0ac3f-122">Lorsqu’un programme n’a aucun **EntryPoint** attribut qui indique explicitement le point d’entrée, les liaisons de niveau supérieur dans le dernier fichier à compiler sont utilisées comme point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="0ac3f-122">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>


## <a name="see-also"></a><span data-ttu-id="0ac3f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ac3f-123">See Also</span></span>
[<span data-ttu-id="0ac3f-124">Fonctions</span><span class="sxs-lookup"><span data-stu-id="0ac3f-124">Functions</span></span>](index.md)

[<span data-ttu-id="0ac3f-125">Liaisons let</span><span class="sxs-lookup"><span data-stu-id="0ac3f-125">let Bindings</span></span>](let-bindings.md)
