---
title: Liaisons do dans les classes (F#)
description: "Découvrez comment utiliser une liaison dans une définition de classe, qui effectue des actions lorsque l’objet est construit ou le type de la première utilisation de ' do' F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 78987cb8-bdba-46e2-b5b2-994c83fe42c4
ms.openlocfilehash: f9582338306d87c3dd799425083037cc95b31b1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="7eb89-104">Liaisons do dans les classes</span><span class="sxs-lookup"><span data-stu-id="7eb89-104">do Bindings in Classes</span></span>

<span data-ttu-id="7eb89-105">A `do` liaison dans une définition de classe exécute des actions lorsque l’objet est construit ou, pour une analyse statique `do` de liaison, lorsque la première utilisation du type.</span><span class="sxs-lookup"><span data-stu-id="7eb89-105">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>


## <a name="syntax"></a><span data-ttu-id="7eb89-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eb89-106">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="7eb89-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="7eb89-107">Remarks</span></span>
<span data-ttu-id="7eb89-108">A `do` liaison apparaît avec ou après `let` liaisons mais avant les définitions de membre dans une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="7eb89-108">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="7eb89-109">Bien que le `do` (mot clé) est facultatif pour `do` liaisons au niveau du module, il n’est pas facultatif pour `do` liaisons dans une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="7eb89-109">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="7eb89-110">Pour la construction de chaque objet d’un type donné, non statique `do` liaisons et non statiques `let` sont exécutées dans l’ordre dans lequel elles apparaissent dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="7eb89-110">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="7eb89-111">Plusieurs `do` liaisons peuvent se produire dans un type.</span><span class="sxs-lookup"><span data-stu-id="7eb89-111">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="7eb89-112">Non statiques `let` liaisons et non statiques `do` liaisons devient le corps du constructeur principal.</span><span class="sxs-lookup"><span data-stu-id="7eb89-112">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="7eb89-113">Le code non statiques `do` section des liaisons peut référencer les paramètres du constructeur principal et des valeurs ou des fonctions qui sont définies dans la `let` section des liaisons.</span><span class="sxs-lookup"><span data-stu-id="7eb89-113">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="7eb89-114">Non statiques `do` liaisons peuvent accéder aux membres de la classe tant que la classe a un auto-identificateur défini par un `as` mot clé dans la classe de titre et tant que toutes les utilisations de ces membres sont qualifiées avec l’auto-identificateur pour la classe.</span><span class="sxs-lookup"><span data-stu-id="7eb89-114">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="7eb89-115">Étant donné que `let` liaisons initialisent les champs privés d’une classe, qui est souvent nécessaire pour garantir que les membres se comportent comme prévu, `do` liaisons sont généralement placées après `let` liaisons afin que le code dans le `do` peut de liaison s’exécuter avec un objet entièrement initialisé.</span><span class="sxs-lookup"><span data-stu-id="7eb89-115">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="7eb89-116">Si votre code tente d’utiliser un membre avant l’initialisation est terminée, une exception InvalidOperationException est déclenchée.</span><span class="sxs-lookup"><span data-stu-id="7eb89-116">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="7eb89-117">Statique `do` liaisons peuvent référencer des membres statiques ou champs de la classe, mais pas les membres ou les champs d’instance.</span><span class="sxs-lookup"><span data-stu-id="7eb89-117">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="7eb89-118">Statique `do` liaisons font partie de l’initialiseur statique pour la classe, qui est garantie s’exécute avant la première utilisation de la classe.</span><span class="sxs-lookup"><span data-stu-id="7eb89-118">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="7eb89-119">Les attributs sont ignorés pour `do` liaisons dans les types.</span><span class="sxs-lookup"><span data-stu-id="7eb89-119">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="7eb89-120">Si un attribut est requis pour le code qui s’exécute dans un `do` de liaison, il doit être appliqué à un constructeur principal.</span><span class="sxs-lookup"><span data-stu-id="7eb89-120">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="7eb89-121">Dans le code suivant, une classe a un statique `do` de liaison et non statiques `do` liaison.</span><span class="sxs-lookup"><span data-stu-id="7eb89-121">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="7eb89-122">L’objet a un constructeur qui possède deux paramètres, `a` et `b`, et deux champs privés sont définis dans le `let` liaisons pour la classe.</span><span class="sxs-lookup"><span data-stu-id="7eb89-122">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="7eb89-123">Deux propriétés sont également définies.</span><span class="sxs-lookup"><span data-stu-id="7eb89-123">Two properties are also defined.</span></span> <span data-ttu-id="7eb89-124">Tous ces éléments sont dans la portée de la non statique `do` section des liaisons, comme cela est illustré par la ligne qui imprime toutes ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="7eb89-124">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="7eb89-125">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="7eb89-125">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="7eb89-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7eb89-126">See Also</span></span>
[<span data-ttu-id="7eb89-127">Membres</span><span class="sxs-lookup"><span data-stu-id="7eb89-127">Members</span></span>](index.md)

[<span data-ttu-id="7eb89-128">Classes</span><span class="sxs-lookup"><span data-stu-id="7eb89-128">Classes</span></span>](../classes.md)

[<span data-ttu-id="7eb89-129">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="7eb89-129">Constructors</span></span>](constructors.md)

[<span data-ttu-id="7eb89-130">Liaisons `let` dans des classes</span><span class="sxs-lookup"><span data-stu-id="7eb89-130">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)

[<span data-ttu-id="7eb89-131">`do`Liaisons</span><span class="sxs-lookup"><span data-stu-id="7eb89-131">`do` Bindings</span></span>](../functions/do-Bindings.md)
