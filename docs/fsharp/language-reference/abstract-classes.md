---
title: Classes abstraites (F#)
description: "En savoir plus sur les classes abstraites F #, qui laissent certains ou tous les membres non implémentés et représentent des fonctionnalités communes de différents types de types d’objet."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 209bcca70318db59506011b1f2bb74a09bf3814a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="abstract-classes"></a><span data-ttu-id="8c4a9-104">Classes abstraites</span><span class="sxs-lookup"><span data-stu-id="8c4a9-104">Abstract Classes</span></span>

<span data-ttu-id="8c4a9-105">*Classes abstraites* sont des classes qui laissent certains ou tous les membres non implémentés, afin que les implémentations puissent être fournies par les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-105">*Abstract classes* are classes that leave some or all members unimplemented, so that implementations can be provided by derived classes.</span></span>

## <a name="syntax"></a><span data-ttu-id="8c4a9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c4a9-106">Syntax</span></span>

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a><span data-ttu-id="8c4a9-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="8c4a9-107">Remarks</span></span>
<span data-ttu-id="8c4a9-108">Dans la programmation orientée objet, une classe abstraite est utilisée comme classe de base d’une hiérarchie et représente les fonctionnalités communes de différents types de types d’objet.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-108">In object-oriented programming, an abstract class is used as a base class of a hierarchy, and represents common functionality of a diverse set of object types.</span></span> <span data-ttu-id="8c4a9-109">Comme l’indique l’abstraite « nom », les classes abstraites ne correspondent pas souvent directement à des entités concrètes dans le domaine de problème.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-109">As the name "abstract" implies, abstract classes often do not correspond directly onto concrete entities in the problem domain.</span></span> <span data-ttu-id="8c4a9-110">Toutefois, elles ne représentent que nombreuses entités concrètes ont en commun.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-110">However, they do represent what many different concrete entities have in common.</span></span>

<span data-ttu-id="8c4a9-111">Classes abstraites doivent avoir le `AbstractClass` attribut.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-111">Abstract classes must have the `AbstractClass` attribute.</span></span> <span data-ttu-id="8c4a9-112">Ils peuvent ont implémenté et non implémenté des membres.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-112">They can have implemented and unimplemented members.</span></span> <span data-ttu-id="8c4a9-113">L’utilisation du terme *abstraite* quand il est appliqué à une classe est la même que dans d’autres langages .NET ; Toutefois, l’utilisation du terme *abstraite* quand il est appliqué aux méthodes (et des propriétés) est un peu différente en F # à partir de son utiliser dans d’autres langages .NET.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-113">The use of the term *abstract* when applied to a class is the same as in other .NET languages; however, the use of the term *abstract* when applied to methods (and properties) is a little different in F# from its use in other .NET languages.</span></span> <span data-ttu-id="8c4a9-114">En F #, lorsqu’une méthode est marquée avec la `abstract` (mot clé), cela indique qu’un membre a une entrée, appelée un *emplacement de dispatch virtuel*, dans la table interne des fonctions virtuelles pour ce type.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-114">In F#, when a method is marked with the `abstract` keyword, this indicates that a member has an entry, known as a *virtual dispatch slot*, in the internal table of virtual functions for that type.</span></span> <span data-ttu-id="8c4a9-115">En d’autres termes, la méthode est virtuelle, bien que le `virtual` mot clé n’est pas utilisé dans le langage F #.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-115">In other words, the method is virtual, although the `virtual` keyword is not used in the F# language.</span></span> <span data-ttu-id="8c4a9-116">Le mot clé `abstract` est utilisé pour les méthodes virtuelles, quelle que soit la méthode est implémentée ou non.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-116">The keyword `abstract` is used on virtual methods regardless of whether the method is implemented.</span></span> <span data-ttu-id="8c4a9-117">La déclaration d’un emplacement de dispatch virtuel est séparée de la définition d’une méthode pour cet emplacement de dispatch.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-117">The declaration of a virtual dispatch slot is separate from the definition of a method for that dispatch slot.</span></span> <span data-ttu-id="8c4a9-118">Par conséquent, l’équivalent en F # d’une déclaration de méthode virtuelle et la définition dans un autre langage .NET est une combinaison d’une déclaration de méthode abstraite et d’une définition séparée, avec l’option le `default` mot clé ou le `override` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="8c4a9-118">Therefore, the F# equivalent of a virtual method declaration and definition in another .NET language is a combination of both an abstract method declaration and a separate definition, with either the `default` keyword or the `override` keyword.</span></span> <span data-ttu-id="8c4a9-119">Pour plus d’informations et d’exemples, consultez [méthodes](members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="8c4a9-119">For more information and examples, see [Methods](members/methods.md).</span></span>

<span data-ttu-id="8c4a9-120">Une classe est considérée comme abstraite uniquement s’il existe des méthodes abstraites qui sont déclarés mais pas définis.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-120">A class is considered abstract only if there are abstract methods that are declared but not defined.</span></span> <span data-ttu-id="8c4a9-121">Par conséquent, les classes qui ont des méthodes abstraites ne sont pas nécessairement des classes abstraites.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-121">Therefore, classes that have abstract methods are not necessarily abstract classes.</span></span> <span data-ttu-id="8c4a9-122">Si une classe a des méthodes abstraites non définies, n’utilisez pas le **AbstractClass** attribut.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-122">Unless a class has undefined abstract methods, do not use the **AbstractClass** attribute.</span></span>

<span data-ttu-id="8c4a9-123">Dans la syntaxe précédente, *modificateur d’accessibilité* peut être `public`, `private` ou `internal`.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-123">In the previous syntax, *accessibility-modifier* can be `public`, `private` or `internal`.</span></span> <span data-ttu-id="8c4a9-124">Pour plus d’informations, consultez [Contrôle d’accès](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="8c4a9-124">For more information, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="8c4a9-125">Comme avec d’autres types, les classes abstraites peuvent avoir une classe de base et un ou plusieurs interfaces de base.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-125">As with other types, abstract classes can have a base class and one or more base interfaces.</span></span> <span data-ttu-id="8c4a9-126">Chaque classe de base ou l’interface s’affiche sur une ligne distincte avec le `inherit` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="8c4a9-126">Each base class or interface appears on a separate line together with the `inherit` keyword.</span></span>

<span data-ttu-id="8c4a9-127">La définition du type d’une classe abstraite peut contenir des membres entièrement définis, mais elle peut également contenir des membres abstraits.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-127">The type definition of an abstract class can contain fully defined members, but it can also contain abstract members.</span></span> <span data-ttu-id="8c4a9-128">La syntaxe pour les membres abstraits est affichée séparément dans la syntaxe précédente.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-128">The syntax for abstract members is shown separately in the previous syntax.</span></span> <span data-ttu-id="8c4a9-129">Dans cette syntaxe, la *signature de type* d’un membre est une liste qui contient les types de paramètre dans l’ordre et les types de retour, séparée par `->` jetons et/ou `*` jetons selon ce qui convient pour curryfiés et basée sur des tuples paramètres.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-129">In this syntax, the *type signature* of a member is a list that contains the parameter types in order and the return types, separated by `->` tokens and/or `*` tokens as appropriate for curried and tupled parameters.</span></span> <span data-ttu-id="8c4a9-130">La syntaxe pour les signatures de type de membre abstrait est identique qu’utilisés dans les fichiers de signature et celle indiquée par IntelliSense dans l’éditeur de Code Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-130">The syntax for abstract member type signatures is the same as that used in signature files and that shown by IntelliSense in the Visual Studio Code Editor.</span></span>

<span data-ttu-id="8c4a9-131">Le code suivant illustre une classe abstraite forme, qui dispose de deux classes dérivées non abstraite, carré et un cercle.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-131">The following code illustrates an abstract class Shape, which has two non-abstract derived classes, Square and Circle.</span></span> <span data-ttu-id="8c4a9-132">L’exemple montre comment utiliser les propriétés, méthodes et classes abstraites.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-132">The example shows how to use abstract classes, methods, and properties.</span></span> <span data-ttu-id="8c4a9-133">Dans l’exemple, la forme de classe abstraite représente les éléments communs des entités concrètes circle et square.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-133">In the example, the abstract class Shape represents the common elements of the concrete entities circle and square.</span></span> <span data-ttu-id="8c4a9-134">Les fonctionnalités communes à toutes les formes (dans un système de coordonnées à deux dimensions) sont abstraites dans la classe de forme : la position sur la grille, un angle de rotation et les propriétés de zone et de périmètre.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-134">The common features of all shapes (in a two-dimensional coordinate system) are abstracted out into the Shape class: the position on the grid, an angle of rotation, and the area and perimeter properties.</span></span> <span data-ttu-id="8c4a9-135">Celles-ci peuvent être substituées, à l’exception de position, le comportement qui ne peut pas modifier des formes.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-135">These can be overridden, except for position, the behavior of which individual shapes cannot change.</span></span>

<span data-ttu-id="8c4a9-136">La méthode de rotation peut être substituée, comme dans la classe Circle, qui est indifférente à la rotation en raison de sa symétrie.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-136">The rotation method can be overridden, as in the Circle class, which is rotation invariant because of its symmetry.</span></span> <span data-ttu-id="8c4a9-137">Dans la classe Circle, la méthode de rotation est remplacée par une méthode qui ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="8c4a9-137">So in the Circle class, the rotation method is replaced by a method that does nothing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

<span data-ttu-id="8c4a9-138">**Sortie :**</span><span class="sxs-lookup"><span data-stu-id="8c4a9-138">**Output:**</span></span>

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a><span data-ttu-id="8c4a9-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c4a9-139">See Also</span></span>
[<span data-ttu-id="8c4a9-140">Classes</span><span class="sxs-lookup"><span data-stu-id="8c4a9-140">Classes</span></span>](classes.md)

[<span data-ttu-id="8c4a9-141">Membres</span><span class="sxs-lookup"><span data-stu-id="8c4a9-141">Members</span></span>](members/index.md)

[<span data-ttu-id="8c4a9-142">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8c4a9-142">Methods</span></span>](members/methods.md)

[<span data-ttu-id="8c4a9-143">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8c4a9-143">Properties</span></span>](members/Properties.md)
