---
title: "Méthodes (F#)"
description: "Découvrez comment une méthode) (F # est une fonction associée à un type qui sont utilisées pour exposer et implémenter les fonctionnalités et le comportement des objets et des types."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1febab3b-c922-49c6-889f-c22db107710c
ms.openlocfilehash: dae31abe6bb0773671b889646c9cceb410a492cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="methods"></a><span data-ttu-id="0fa9e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0fa9e-104">Methods</span></span>

<span data-ttu-id="0fa9e-105">A *méthode* est une fonction qui est associée à un type.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-105">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="0fa9e-106">Dans la programmation orientée objet, les méthodes sont utilisées pour exposer et implémenter les fonctionnalités et le comportement des objets et des types.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-106">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>


## <a name="syntax"></a><span data-ttu-id="0fa9e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fa9e-107">Syntax</span></span>

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-nameparameter-list [ : return-type ]=
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member self-identifier.method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member [inline] self-identifier.method-name : type-signature
[ attributes ]
default member [inline] self-identifier.method-nameparameter-list[ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue([ default-value ])>] input) [ : return-type ]
```

## <a name="remarks"></a><span data-ttu-id="0fa9e-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="0fa9e-108">Remarks</span></span>
<span data-ttu-id="0fa9e-109">Dans la syntaxe précédente, vous pouvez voir les différentes formes de définitions et déclarations de méthode.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-109">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="0fa9e-110">Dans le corps de méthode plus longs, un saut de ligne suit le signe égal (=) et le corps de la totalité de la méthode est mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-110">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="0fa9e-111">Attributs peuvent être appliqués à une déclaration de méthode.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-111">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="0fa9e-112">Ils précèdent la syntaxe pour une définition de méthode et sont généralement répertoriés sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-112">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="0fa9e-113">Pour plus d’informations, consultez [Attributs](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0fa9e-113">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="0fa9e-114">Les méthodes peuvent être marquées `inline`.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-114">Methods can be marked `inline`.</span></span> <span data-ttu-id="0fa9e-115">Pour plus d’informations sur `inline`, consultez [Fonctions inline](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0fa9e-115">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="0fa9e-116">Les méthodes non inline peuvent être utilisées de manière récursive dans le type ; Il n’est pas nécessaire d’utiliser explicitement le `rec` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="0fa9e-116">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>


## <a name="instance-methods"></a><span data-ttu-id="0fa9e-117">Méthodes d’instance</span><span class="sxs-lookup"><span data-stu-id="0fa9e-117">Instance Methods</span></span>
<span data-ttu-id="0fa9e-118">Méthodes d’instance sont déclarées avec le `member` (mot clé) et un *auto-identificateur*, suivi d’un point (.) et le nom de la méthode et des paramètres.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-118">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="0fa9e-119">Comme c’est le cas pour `let` liaisons, le *la liste des paramètres* peut être un modèle.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-119">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="0fa9e-120">En règle générale, vous insérez la méthode paramètres entre parenthèses dans une forme de tuple, qui est les façon dont les méthodes apparaissent en F # lorsqu’ils sont créés dans d’autres langages .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-120">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="0fa9e-121">Toutefois, le formulaire curryfié (paramètres séparés par des espaces) est également courant et autres modèles sont également pris en charge.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-121">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="0fa9e-122">L’exemple suivant illustre la définition et l’utilisation d’une méthode d’instance non abstraite.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-122">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="0fa9e-123">Dans les méthodes d’instance, n’utilisez pas l’auto-identificateur pour accéder aux champs définis à l’aide de liaisons let.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-123">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="0fa9e-124">Utilisez l’auto-identificateur lorsque l’accès à d’autres membres et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-124">Use the self identifier when accessing other members and properties.</span></span>


## <a name="static-methods"></a><span data-ttu-id="0fa9e-125">Méthodes statiques</span><span class="sxs-lookup"><span data-stu-id="0fa9e-125">Static Methods</span></span>
<span data-ttu-id="0fa9e-126">Le mot clé `static` est utilisé pour spécifier qu’une méthode peut être appelée sans une instance et n’est pas associé à une instance d’objet.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-126">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="0fa9e-127">Sinon, les méthodes sont des méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-127">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="0fa9e-128">L’exemple dans la section suivante montre les champs déclarés avec le `let` (mot clé), les membres de propriété déclarés avec le `member` (mot clé) et une méthode statique est déclaré avec le `static` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="0fa9e-128">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="0fa9e-129">L’exemple suivant illustre la définition et l’utilisation de méthodes statiques.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-129">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="0fa9e-130">Supposez que ces définitions de méthode se trouvent dans le `SomeType` classe dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-130">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="0fa9e-131">Méthodes abstraites et virtuelles</span><span class="sxs-lookup"><span data-stu-id="0fa9e-131">Abstract and Virtual Methods</span></span>
<span data-ttu-id="0fa9e-132">Le mot clé `abstract` indique qu’une méthode a un emplacement de dispatch virtuel et peut-être pas une définition de la classe.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-132">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="0fa9e-133">A *emplacement de dispatch virtuel* est une entrée dans une table de fonctions gérée en interne qui est utilisée au moment de l’exécution pour rechercher des fonctions virtuelles appelle dans un type orienté objet.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-133">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="0fa9e-134">Le mécanisme de dispatch virtuel est le mécanisme qui implémente *le polymorphisme*, une fonctionnalité importante de la programmation orientée objet.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-134">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="0fa9e-135">Une classe qui a au moins une méthode abstraite sans définition est une *classe abstraite*, ce qui signifie qu’aucune instance de cette classe ne peut être créée.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-135">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="0fa9e-136">Pour plus d’informations sur les classes abstraites, consultez [Classes abstraites](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0fa9e-136">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="0fa9e-137">Les déclarations de méthode abstraite n’incluent pas de corps de méthode.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-137">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="0fa9e-138">Au lieu de cela, le nom de la méthode est suivi par un signe deux-points ( :) et une signature de type pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-138">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="0fa9e-139">La signature de type d’une méthode est identique à celle indiquée par IntelliSense lorsque vous placez le pointeur de la souris sur un nom de méthode dans l’éditeur de Code Visual Studio, à l’exception sans nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-139">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="0fa9e-140">Les signatures de type sont également affichées par l’interpréteur, fsi.exe, lorsque vous travaillez de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-140">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="0fa9e-141">La signature de type d’une méthode est formée en répertoriant les types des paramètres, suivis par le type de retour, avec les symboles de séparateur approprié.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-141">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="0fa9e-142">Les paramètres curryfiés sont séparés par `->` et les paramètres de tuple sont séparés par `*`.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-142">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="0fa9e-143">La valeur de retour est toujours séparée des arguments par une `->` symbole.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-143">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="0fa9e-144">Parenthèses peuvent être utilisées pour grouper des paramètres complexes, par exemple lorsqu’un type de fonction est un paramètre, ou pour indiquer lorsqu’un tuple est traité comme un paramètre unique plutôt que comme deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-144">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="0fa9e-145">Vous pouvez également attribuer des définitions par défaut méthodes abstraites en ajoutant la définition à la classe et en utilisant le `default` (mot clé), comme indiqué dans le bloc de syntaxe dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-145">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="0fa9e-146">Une méthode abstraite qui a une définition dans la même classe équivaut à une méthode virtuelle dans d’autres langages .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-146">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="0fa9e-147">Il existe ou non une définition, le `abstract` (mot clé) crée un nouvel emplacement de dispatch dans la table de fonctions virtuelles pour la classe.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-147">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="0fa9e-148">Indépendamment de si une classe de base implémente ses méthodes abstraites, classes dérivées peuvent fournir des implémentations de méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-148">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="0fa9e-149">Pour implémenter une méthode abstraite dans une classe dérivée, définissez une méthode qui a le même nom et la signature dans la classe dérivée, mais utilisez le `override` ou `default` (mot clé) et fournissez le corps de méthode.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-149">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="0fa9e-150">Les mots clés `override` et `default` exactement la même signification.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-150">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="0fa9e-151">Utilisez `override` si la nouvelle méthode substitue une implémentation de la classe de base ; Utilisez `default` lorsque vous créez une implémentation dans la même classe que la déclaration abstraite d’origine.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-151">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="0fa9e-152">N’utilisez pas le `abstract` mot clé dans la méthode qui implémente la méthode déclarée abstraite dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-152">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="0fa9e-153">L’exemple suivant illustre une méthode abstraite `Rotate` qui a une implémentation par défaut, l’équivalent d’une méthode virtuelle .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-153">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="0fa9e-154">L’exemple suivant illustre une classe dérivée qui substitue une méthode de classe de base.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-154">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="0fa9e-155">Dans ce cas, la substitution modifie le comportement afin que la méthode ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-155">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="0fa9e-156">Méthodes surchargées</span><span class="sxs-lookup"><span data-stu-id="0fa9e-156">Overloaded Methods</span></span>
<span data-ttu-id="0fa9e-157">Les méthodes surchargées sont des méthodes qui ont des noms identiques dans un type donné, mais qui ont des arguments différents.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-157">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="0fa9e-158">En F #, les arguments facultatifs sont généralement utilisées au lieu de méthodes surchargées.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-158">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="0fa9e-159">Toutefois, les méthodes surchargées sont autorisées dans le langage, autant que les arguments sont sous forme de tuple, curryfiée pas de formulaire.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-159">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="0fa9e-160">Arguments facultatifs</span><span class="sxs-lookup"><span data-stu-id="0fa9e-160">Optional Arguments</span></span>

<span data-ttu-id="0fa9e-161">À compter de F # 4.1, vous pouvez également avoir des arguments facultatifs avec une valeur de paramètre par défaut dans les méthodes.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-161">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="0fa9e-162">Cela a pour but de faciliter l’interopérabilité avec du code c#.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-162">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="0fa9e-163">L’exemple suivant illustre la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="0fa9e-163">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="0fa9e-164">Notez que la valeur transmise pour `DefaultParameterValue` doit correspondre au type d’entrée.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-164">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="0fa9e-165">Dans l’exemple ci-dessus, il est un `int`.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-165">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="0fa9e-166">Tentative de passer une valeur non entière dans `DefaultParameterValue` entraînera une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-166">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="0fa9e-167">Exemple : Propriétés et méthodes</span><span class="sxs-lookup"><span data-stu-id="0fa9e-167">Example: Properties and Methods</span></span>
<span data-ttu-id="0fa9e-168">L’exemple suivant contient un type qui a des exemples de champs, des fonctions privées, des propriétés et une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="0fa9e-168">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="0fa9e-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fa9e-169">See Also</span></span>
[<span data-ttu-id="0fa9e-170">Membres</span><span class="sxs-lookup"><span data-stu-id="0fa9e-170">Members</span></span>](index.md)
