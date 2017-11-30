---
title: Expressions d'objet (F#)
description: "Apprenez à utiliser les expressions d’objet F # lorsque vous souhaitez éviter le code supplémentaire et la surcharge requise pour créer un nouveau type nommé."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c6dcf4c9-e7fd-4eee-9e4e-1176f4c27f57
ms.openlocfilehash: 28660d430473de02a8a55e37a26609827b364012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="object-expressions"></a><span data-ttu-id="08d10-104">Expressions d'objet</span><span class="sxs-lookup"><span data-stu-id="08d10-104">Object Expressions</span></span>

<span data-ttu-id="08d10-105">Un *objet expression* est une expression qui crée une nouvelle instance d’un type d’objet créé dynamiquement et anonyme qui est basée sur un type de base existante, une interface ou un ensemble d’interfaces.</span><span class="sxs-lookup"><span data-stu-id="08d10-105">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>


## <a name="syntax"></a><span data-ttu-id="08d10-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08d10-106">Syntax</span></span>

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a><span data-ttu-id="08d10-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="08d10-107">Remarks</span></span>
<span data-ttu-id="08d10-108">Dans la syntaxe précédente, le *typename* représente un type de classe existant ou un type d’interface.</span><span class="sxs-lookup"><span data-stu-id="08d10-108">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="08d10-109">*type-params* décrit les paramètres de type générique facultatifs.</span><span class="sxs-lookup"><span data-stu-id="08d10-109">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="08d10-110">Le *arguments* sont utilisés uniquement pour les types de classe, qui nécessitent des paramètres du constructeur.</span><span class="sxs-lookup"><span data-stu-id="08d10-110">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="08d10-111">Le *définitions de membre* sont des substitutions de méthodes de classe de base ou des implémentations de méthodes abstraites d’une classe de base ou une interface.</span><span class="sxs-lookup"><span data-stu-id="08d10-111">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="08d10-112">L’exemple suivant illustre différents types d’expressions d’objet.</span><span class="sxs-lookup"><span data-stu-id="08d10-112">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="08d10-113">À l’aide d’Expressions d’objet</span><span class="sxs-lookup"><span data-stu-id="08d10-113">Using Object Expressions</span></span>
<span data-ttu-id="08d10-114">Vous utilisez des expressions d’objet lorsque vous souhaitez éviter le code supplémentaire et la surcharge requise pour créer un nouveau type nommé.</span><span class="sxs-lookup"><span data-stu-id="08d10-114">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="08d10-115">Si vous utilisez des expressions d’objet pour réduire le nombre de types créés dans un programme, vous pouvez réduire le nombre de lignes de code et empêcher la prolifération inutile de types.</span><span class="sxs-lookup"><span data-stu-id="08d10-115">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="08d10-116">Au lieu de créer de nombreux types uniquement pour gérer des situations spécifiques, vous pouvez utiliser une expression d’objet qui personnalise un type existant ou fournit une implémentation appropriée d’une interface pour le cas spécifique à portée de main.</span><span class="sxs-lookup"><span data-stu-id="08d10-116">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>


## <a name="see-also"></a><span data-ttu-id="08d10-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08d10-117">See Also</span></span>
[<span data-ttu-id="08d10-118">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="08d10-118">F# Language Reference</span></span>](index.md)
