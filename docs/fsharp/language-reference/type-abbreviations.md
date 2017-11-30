---
title: "Abréviations de types (F#)"
description: "Découvrez les abréviations de type F # pour donner un nom plus significatif à un type afin de rendre le code plus facile à lire."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 560af74f-935f-415c-af56-604cddb9da6b
ms.openlocfilehash: 235c0240fe89d203b9474dec2b3f91947f453cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="type-abbreviations"></a><span data-ttu-id="058bc-104">Abréviations de types</span><span class="sxs-lookup"><span data-stu-id="058bc-104">Type Abbreviations</span></span>

<span data-ttu-id="058bc-105">A *abréviation de type* est un alias ou un autre nom pour un type.</span><span class="sxs-lookup"><span data-stu-id="058bc-105">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="058bc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="058bc-106">Syntax</span></span>

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="058bc-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="058bc-107">Remarks</span></span>
<span data-ttu-id="058bc-108">Vous pouvez utiliser les abréviations de type pour donner un nom plus significatif, à un type afin de rendre le code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="058bc-108">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="058bc-109">Vous pouvez également les utiliser pour créer un nom facile à utiliser pour un type fastidieux à écrire. En outre, vous pouvez utiliser les abréviations de type pour le rendre plus facile de modifier un type sous-jacent sans modifier tout code qui utilise le type.</span><span class="sxs-lookup"><span data-stu-id="058bc-109">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="058bc-110">Voici une abréviation de type simple.</span><span class="sxs-lookup"><span data-stu-id="058bc-110">The following is a simple type abbreviation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="058bc-111">Les abréviations de type peuvent inclure des paramètres génériques, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="058bc-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="058bc-112">Dans le code précédent, `Transform` est une abréviation de type représentant une fonction qui accepte un argument unique de n’importe quel type et qui retourne une valeur unique du même type.</span><span class="sxs-lookup"><span data-stu-id="058bc-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="058bc-113">Les abréviations de type ne sont pas conservées dans le code MSIL .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="058bc-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="058bc-114">Par conséquent, lorsque vous utilisez un assembly F # à partir d’un autre langage .NET Framework, vous devez utiliser le nom du type sous-jacent pour une abréviation de type.</span><span class="sxs-lookup"><span data-stu-id="058bc-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="058bc-115">Les abréviations de type peuvent également servir dans les unités de mesure.</span><span class="sxs-lookup"><span data-stu-id="058bc-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="058bc-116">Pour plus d’informations, consultez [unités](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="058bc-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="058bc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="058bc-117">See Also</span></span>
[<span data-ttu-id="058bc-118">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="058bc-118">F# Language Reference</span></span>](index.md)

