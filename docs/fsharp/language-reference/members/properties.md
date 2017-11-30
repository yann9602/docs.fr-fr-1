---
title: "Propriétés (F#)"
description: "En savoir plus sur les propriétés F #, qui sont des membres qui représentent des valeurs associées à un objet."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 98b363a5-ee6a-4b7b-b8ae-b244f2a0b316
ms.openlocfilehash: 53b93b20310c557ad9c30226bc08f85cbf2f3010
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="properties"></a><span data-ttu-id="004d1-104">Propriétés</span><span class="sxs-lookup"><span data-stu-id="004d1-104">Properties</span></span>

<span data-ttu-id="004d1-105">*Propriétés* sont des membres qui représentent des valeurs associées à un objet.</span><span class="sxs-lookup"><span data-stu-id="004d1-105">*Properties* are members that represent values associated with an object.</span></span>


## <a name="syntax"></a><span data-ttu-id="004d1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="004d1-106">Syntax</span></span>

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a><span data-ttu-id="004d1-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="004d1-107">Remarks</span></span>
<span data-ttu-id="004d1-108">Propriétés représentent la » a une « relation dans la programmation orientée objet, représentant les données qui sont associés à des instances d’objet ou, pour les propriétés statiques, avec le type.</span><span class="sxs-lookup"><span data-stu-id="004d1-108">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="004d1-109">Vous pouvez déclarer des propriétés de deux façons, selon que vous souhaitez spécifier explicitement la valeur sous-jacente (également appelée magasin de stockage) pour la propriété, ou si vous souhaitez permettre au compilateur de générer automatiquement le magasin de stockage pour vous.</span><span class="sxs-lookup"><span data-stu-id="004d1-109">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="004d1-110">En règle générale, vous devez utiliser le mode plus explicite si la propriété a une implémentation non triviale et automatique lorsque la propriété est un simple wrapper simple pour une valeur ou une variable.</span><span class="sxs-lookup"><span data-stu-id="004d1-110">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="004d1-111">Pour déclarer une propriété explicitement, utilisez le `member` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="004d1-111">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="004d1-112">Cette syntaxe déclarative est suivie par la syntaxe qui spécifie le `get` et `set` méthodes, également nommés *accesseurs*.</span><span class="sxs-lookup"><span data-stu-id="004d1-112">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="004d1-113">Les différentes formes de la syntaxe explicite indiquée dans la section syntaxe sont utilisées pour les propriétés en lecture/écriture, en lecture seule et en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="004d1-113">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="004d1-114">Pour les propriétés en lecture seule, vous définissez uniquement un `get` méthode ; définir uniquement pour les propriétés en écriture seule, un `set` (méthode).</span><span class="sxs-lookup"><span data-stu-id="004d1-114">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="004d1-115">Notez que lorsqu’une propriété a à la fois `get` et `set` accesseurs, l’autre syntaxe vous permet de spécifier les attributs et les modificateurs d’accessibilité qui sont différents pour chaque accesseur, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="004d1-115">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="004d1-116">Pour les propriétés en lecture/écriture, qui ont à la fois un `get` et `set` (méthode), l’ordre des `get` et `set` peuvent être inversées.</span><span class="sxs-lookup"><span data-stu-id="004d1-116">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="004d1-117">Vous pouvez également fournir la syntaxe indiquée pour `get` uniquement et la syntaxe indiquée pour `set` uniquement, au lieu d’utiliser la syntaxe combinée.</span><span class="sxs-lookup"><span data-stu-id="004d1-117">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="004d1-118">Cela facilite Commentez la personne `get` ou `set` (méthode), si cela vous peuvent s’avérer nécessaires.</span><span class="sxs-lookup"><span data-stu-id="004d1-118">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="004d1-119">Cette solution à l’aide de la syntaxe combinée est indiquée dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="004d1-119">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="004d1-120">Cette suspension les données pour les propriétés sont appelées des valeurs privé *magasins de stockage*.</span><span class="sxs-lookup"><span data-stu-id="004d1-120">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="004d1-121">Pour indiquer au compilateur de créer le magasin de stockage automatiquement, utilisez les mots clés `member val`, omettez l’auto-identificateur, puis indiquez une expression pour initialiser la propriété.</span><span class="sxs-lookup"><span data-stu-id="004d1-121">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="004d1-122">Si la propriété doit être mutable, inclure `with get, set`.</span><span class="sxs-lookup"><span data-stu-id="004d1-122">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="004d1-123">Par exemple, le type de classe suivant inclut deux propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="004d1-123">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="004d1-124">`Property1`est en lecture seule et est initialisée à l’argument fourni pour le constructeur principal, et `Property2` est une propriété définissable initialisée avec une chaîne vide :</span><span class="sxs-lookup"><span data-stu-id="004d1-124">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="004d1-125">Propriétés implémentées automatiquement font partie de l’initialisation d’un type, afin qu’ils doivent figurer avant les autres définitions de membre, comme `let` liaisons et `do` liaisons dans une définition de type.</span><span class="sxs-lookup"><span data-stu-id="004d1-125">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="004d1-126">Notez que l’expression qui initialise une propriété implémentée automatiquement n’est évaluée que lors de l’initialisation, et pas chaque fois que la propriété est accessible.</span><span class="sxs-lookup"><span data-stu-id="004d1-126">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="004d1-127">Ce comportement diffère du comportement d’une propriété implémentée explicitement.</span><span class="sxs-lookup"><span data-stu-id="004d1-127">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="004d1-128">Cela efficacement signifie que le code d’initialisation de ces propriétés est ajouté au constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="004d1-128">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="004d1-129">Prenons le code suivant qui illustre cette différence :</span><span class="sxs-lookup"><span data-stu-id="004d1-129">Consider the following code that shows this difference:</span></span>

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

<span data-ttu-id="004d1-130">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="004d1-130">**Output**</span></span>

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="004d1-131">La sortie du code précédent montre que la valeur de AutoProperty est inchangée lorsqu’elle est appelée à plusieurs reprises, tandis que le ExplicitProperty change chaque fois qu’elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="004d1-131">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="004d1-132">Cela montre que l’expression pour une propriété implémentée automatiquement n’est pas évaluée chaque fois, est la méthode d’accesseur Get de la propriété explicite.</span><span class="sxs-lookup"><span data-stu-id="004d1-132">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>


>[!WARNING]
<span data-ttu-id="004d1-133">Il existe certaines bibliothèques, telles que Entity Framework (`System.Data.Entity`) qui effectuent des opérations personnalisées dans les constructeurs de classe de base qui ne fonctionnent pas correctement avec l’initialisation des propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="004d1-133">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="004d1-134">Dans ce cas, essayez d’utiliser des propriétés explicites.</span><span class="sxs-lookup"><span data-stu-id="004d1-134">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="004d1-135">Propriétés peuvent être membres de classes, structures, unions discriminées, les enregistrements, interfaces et des extensions de type et peuvent également être définies dans les expressions d’objet.</span><span class="sxs-lookup"><span data-stu-id="004d1-135">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="004d1-136">Attributs peuvent être appliqués aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="004d1-136">Attributes can be applied to properties.</span></span> <span data-ttu-id="004d1-137">Pour appliquer un attribut à une propriété, écrire l’attribut sur une ligne distincte avant que la propriété.</span><span class="sxs-lookup"><span data-stu-id="004d1-137">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="004d1-138">Pour plus d’informations, consultez [Attributs](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="004d1-138">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="004d1-139">Par défaut, les propriétés sont publiques.</span><span class="sxs-lookup"><span data-stu-id="004d1-139">By default, properties are public.</span></span> <span data-ttu-id="004d1-140">Les modificateurs d’accessibilité peuvent également être appliqués aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="004d1-140">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="004d1-141">Pour appliquer un modificateur d’accessibilité, ajoutez-le immédiatement avant le nom de la propriété si elle est destinée à appliquer à la fois à la `get` et `set` méthodes ; avant d’ajouter le `get` et `set` mots clés si une accessibilité différente est obligatoire pour chaque accesseur.</span><span class="sxs-lookup"><span data-stu-id="004d1-141">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="004d1-142">Le *modificateur d’accessibilité* peut prendre l’une des opérations suivantes : `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="004d1-142">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="004d1-143">Pour plus d’informations, consultez [Contrôle d’accès](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="004d1-143">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="004d1-144">Les implémentations de propriété sont exécutées chaque fois qu’une propriété est accessible.</span><span class="sxs-lookup"><span data-stu-id="004d1-144">Property implementations are executed each time a property is accessed.</span></span>


## <a name="static-and-instance-properties"></a><span data-ttu-id="004d1-145">Statique et les propriétés de l’Instance</span><span class="sxs-lookup"><span data-stu-id="004d1-145">Static and Instance Properties</span></span>
<span data-ttu-id="004d1-146">Propriétés peuvent être statiques ou des propriétés de l’instance.</span><span class="sxs-lookup"><span data-stu-id="004d1-146">Properties can be static or instance properties.</span></span> <span data-ttu-id="004d1-147">Propriétés statiques peuvent être appelées sans une instance et sont utilisées pour les valeurs associées de type, pas avec des objets individuels.</span><span class="sxs-lookup"><span data-stu-id="004d1-147">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="004d1-148">Pour les propriétés statiques, omettez l’auto-identificateur.</span><span class="sxs-lookup"><span data-stu-id="004d1-148">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="004d1-149">L’auto-identificateur est requis pour les propriétés de l’instance.</span><span class="sxs-lookup"><span data-stu-id="004d1-149">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="004d1-150">La définition de propriété statique suivante est basée sur un scénario dans lequel vous avez un champ statique `myStaticValue` qui est le magasin de stockage pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="004d1-150">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="004d1-151">Propriétés peuvent également être de type de tableau, auquel cas elles sont appelées *propriétés indexées*.</span><span class="sxs-lookup"><span data-stu-id="004d1-151">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="004d1-152">Pour plus d’informations, consultez [propriétés indexées](indexed-properties.md).</span><span class="sxs-lookup"><span data-stu-id="004d1-152">For more information, see [Indexed Properties](indexed-properties.md).</span></span>


## <a name="type-annotation-for-properties"></a><span data-ttu-id="004d1-153">Annotation de type pour les propriétés</span><span class="sxs-lookup"><span data-stu-id="004d1-153">Type Annotation for Properties</span></span>
<span data-ttu-id="004d1-154">Dans de nombreux cas, le compilateur dispose de suffisamment d’informations pour déduire le type d’une propriété du type de magasin de stockage, mais vous pouvez définir explicitement le type en ajoutant une annotation de type.</span><span class="sxs-lookup"><span data-stu-id="004d1-154">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="004d1-155">À l’aide de la propriété d’accesseurs set</span><span class="sxs-lookup"><span data-stu-id="004d1-155">Using Property set Accessors</span></span>
<span data-ttu-id="004d1-156">Vous pouvez définir des propriétés qui fournissent des `set` accesseurs à l’aide de la `<-` opérateur.</span><span class="sxs-lookup"><span data-stu-id="004d1-156">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="004d1-157">La sortie est **20**.</span><span class="sxs-lookup"><span data-stu-id="004d1-157">The output is **20**.</span></span>


## <a name="abstract-properties"></a><span data-ttu-id="004d1-158">Propriétés abstraites</span><span class="sxs-lookup"><span data-stu-id="004d1-158">Abstract Properties</span></span>
<span data-ttu-id="004d1-159">Propriétés peuvent être abstract.</span><span class="sxs-lookup"><span data-stu-id="004d1-159">Properties can be abstract.</span></span> <span data-ttu-id="004d1-160">Comme avec les méthodes, `abstract` signifie simplement qu’il existe un dispatch virtuel est associé à la propriété.</span><span class="sxs-lookup"><span data-stu-id="004d1-160">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="004d1-161">Propriétés abstraites peuvent être vraiment abstraites, autrement dit, sans une définition dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="004d1-161">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="004d1-162">La classe qui contient une telle propriété est par conséquent une classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="004d1-162">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="004d1-163">Vous pouvez également abstraite peut simplement signifie qu’une propriété est virtuelle, et dans ce cas, une définition doit être présente dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="004d1-163">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="004d1-164">Notez que les propriétés abstraites ne doivent pas être privées, et si un accesseur est abstrait, l’autre doit également être abstract.</span><span class="sxs-lookup"><span data-stu-id="004d1-164">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="004d1-165">Pour plus d’informations sur les classes abstraites, consultez [Classes abstraites](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="004d1-165">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="004d1-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="004d1-166">See Also</span></span>
[<span data-ttu-id="004d1-167">Membres</span><span class="sxs-lookup"><span data-stu-id="004d1-167">Members</span></span>](index.md)

[<span data-ttu-id="004d1-168">Méthodes</span><span class="sxs-lookup"><span data-stu-id="004d1-168">Methods</span></span>](methods.md)
