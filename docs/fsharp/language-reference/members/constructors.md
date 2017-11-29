---
title: Constructeurs (F#)
description: "Découvrez comment définir et utiliser des constructeurs dans F # pour créer et initialiser des objets de classe ou structure."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e0da2250-29de-4145-a1be-e5faff080759
ms.openlocfilehash: 60ed93f1c1dc15e99465d969c9e4fd3e61c28ffa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="constructors"></a><span data-ttu-id="c912e-104">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="c912e-104">Constructors</span></span>

<span data-ttu-id="c912e-105">Cette rubrique décrit comment définir et utiliser les constructeurs pour créer et initialiser des objets de classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="c912e-105">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>


## <a name="construction-of-class-objects"></a><span data-ttu-id="c912e-106">Construction d’objets de classe</span><span class="sxs-lookup"><span data-stu-id="c912e-106">Construction of Class Objects</span></span>
<span data-ttu-id="c912e-107">Les objets de types de classe ont des constructeurs.</span><span class="sxs-lookup"><span data-stu-id="c912e-107">Objects of class types have constructors.</span></span> <span data-ttu-id="c912e-108">Il existe deux types de constructeurs.</span><span class="sxs-lookup"><span data-stu-id="c912e-108">There are two kinds of constructors.</span></span> <span data-ttu-id="c912e-109">Un est le constructeur principal, dont les paramètres apparaissent entre parenthèses juste après le nom de type.</span><span class="sxs-lookup"><span data-stu-id="c912e-109">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="c912e-110">Spécifiez d’autres, facultatifs des constructeurs supplémentaires à l’aide de la `new` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="c912e-110">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="c912e-111">Ces constructeurs supplémentaires doivent appeler le constructeur principal.</span><span class="sxs-lookup"><span data-stu-id="c912e-111">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="c912e-112">Le constructeur principal contient `let` et `do` les liaisons qui apparaissent au début de la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="c912e-112">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="c912e-113">A `let` liaison déclare des champs privés et les méthodes de la classe ; un `do` liaison exécute du code.</span><span class="sxs-lookup"><span data-stu-id="c912e-113">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="c912e-114">Pour plus d’informations sur `let` liaisons dans les constructeurs de classe, consultez [ `let` liaisons dans les Classes](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="c912e-114">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="c912e-115">Pour plus d’informations sur `do` liaisons dans les constructeurs, consultez [ `do` liaisons dans les Classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="c912e-115">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="c912e-116">Que le constructeur à appeler soit un constructeur principal ou un constructeur supplémentaire, vous pouvez créer des objets en utilisant un `new` expression, avec ou sans le paramètre facultatif `new` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="c912e-116">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="c912e-117">Vous initialisez vos objets avec des arguments de constructeur, soit en répertoriant les arguments dans l’ordre et séparés par des virgules et mise entre parenthèses, ou à l’aide des arguments nommés et des valeurs entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="c912e-117">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="c912e-118">Vous pouvez également définir des propriétés sur un objet lors de la construction de l’objet en utilisant les noms de propriété et assigner des valeurs comme arguments de constructeur nommés.</span><span class="sxs-lookup"><span data-stu-id="c912e-118">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="c912e-119">Le code suivant illustre une classe qui a un constructeur et différentes façons de créer des objets.</span><span class="sxs-lookup"><span data-stu-id="c912e-119">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="c912e-120">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="c912e-120">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="c912e-121">Construction de Structures</span><span class="sxs-lookup"><span data-stu-id="c912e-121">Construction of Structures</span></span>
<span data-ttu-id="c912e-122">Les structures respectent toutes les règles de classes.</span><span class="sxs-lookup"><span data-stu-id="c912e-122">Structures follow all the rules of classes.</span></span> <span data-ttu-id="c912e-123">Par conséquent, vous pouvez avoir un constructeur principal, et vous pouvez fournir des constructeurs supplémentaires à l’aide de `new`.</span><span class="sxs-lookup"><span data-stu-id="c912e-123">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="c912e-124">Toutefois, il existe une différence importante entre les structures et classes : structures peuvent avoir un constructeur par défaut (autrement dit, un sans argument) même si aucun constructeur principal n’est définie.</span><span class="sxs-lookup"><span data-stu-id="c912e-124">However, there is one important difference between structures and classes: structures can have a default constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="c912e-125">Le constructeur par défaut initialise tous les champs à la valeur par défaut pour ce type, généralement zéro ou à son équivalent.</span><span class="sxs-lookup"><span data-stu-id="c912e-125">The default constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="c912e-126">Tous les constructeurs que vous définissez pour des structures doivent avoir au moins un argument afin qu’ils ne sont pas en conflit avec le constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c912e-126">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="c912e-127">En outre, les structures ont souvent des champs qui sont créés à l’aide de la `val` mot-clé ; classes peuvent également avoir ces champs.</span><span class="sxs-lookup"><span data-stu-id="c912e-127">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="c912e-128">Structures et classes qui ont des champs définis à l’aide de la `val` (mot clé) peut également être initialisée dans des constructeurs supplémentaires à l’aide d’expressions d’enregistrement, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="c912e-128">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="c912e-129">Pour plus d’informations, consultez [champs explicites : le `val` mot clé](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="c912e-129">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>


## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="c912e-130">Exécution d’effets secondaires dans les constructeurs</span><span class="sxs-lookup"><span data-stu-id="c912e-130">Executing Side Effects in Constructors</span></span>
<span data-ttu-id="c912e-131">Un constructeur principal dans une classe peut exécuter du code dans un `do` liaison.</span><span class="sxs-lookup"><span data-stu-id="c912e-131">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="c912e-132">Toutefois, que se passe-t-il si vous devez exécuter du code dans un constructeur supplémentaire sans un `do` liaison ?</span><span class="sxs-lookup"><span data-stu-id="c912e-132">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="c912e-133">Pour ce faire, vous utilisez la `then` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="c912e-133">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="c912e-134">Les effets secondaires du constructeur principal est toujours exécuter.</span><span class="sxs-lookup"><span data-stu-id="c912e-134">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="c912e-135">Par conséquent, la sortie est comme suit.</span><span class="sxs-lookup"><span data-stu-id="c912e-135">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="c912e-136">Auto-identificateurs dans les constructeurs</span><span class="sxs-lookup"><span data-stu-id="c912e-136">Self Identifiers in Constructors</span></span>
<span data-ttu-id="c912e-137">Dans d’autres membres, vous fournissez un nom pour l’objet actuel dans la définition de chaque membre.</span><span class="sxs-lookup"><span data-stu-id="c912e-137">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="c912e-138">Vous pouvez également placer l’auto-identificateur sur la première ligne de la définition de classe à l’aide de la `as` (mot clé) immédiatement après les paramètres du constructeur.</span><span class="sxs-lookup"><span data-stu-id="c912e-138">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="c912e-139">L’exemple suivant illustre cette syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c912e-139">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="c912e-140">Dans les constructeurs supplémentaires, vous pouvez également définir un auto-identificateur en plaçant le `as` clause juste après les paramètres du constructeur.</span><span class="sxs-lookup"><span data-stu-id="c912e-140">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="c912e-141">L’exemple suivant illustre cette syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c912e-141">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="c912e-142">Des problèmes peuvent survenir lorsque vous essayez d’utiliser un objet avant d’être entièrement définie.</span><span class="sxs-lookup"><span data-stu-id="c912e-142">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="c912e-143">Par conséquent, les utilisations de l’auto-identificateur peuvent provoquer le compilateur émet un avertissement et d’insérer des contrôles supplémentaires pour vérifier que les membres d’un objet ne sont pas accessibles avant l’initialisation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="c912e-143">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="c912e-144">Vous devez utiliser uniquement l’auto-identificateur dans le `do` liaisons du constructeur principal, ou après le `then` mot clé dans des constructeurs supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="c912e-144">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="c912e-145">Le nom de l’auto-identificateur ne dispose pas être `this`.</span><span class="sxs-lookup"><span data-stu-id="c912e-145">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="c912e-146">Il peut être n’importe quel identificateur valid.</span><span class="sxs-lookup"><span data-stu-id="c912e-146">It can be any valid identifier.</span></span>


## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="c912e-147">Assigner des valeurs aux propriétés lors de l’initialisation</span><span class="sxs-lookup"><span data-stu-id="c912e-147">Assigning Values to Properties at Initialization</span></span>
<span data-ttu-id="c912e-148">Vous pouvez assigner des valeurs aux propriétés d’un objet de classe dans le code d’initialisation en ajoutant une liste d’assignations sous la forme `property = value` à la liste d’arguments pour un constructeur.</span><span class="sxs-lookup"><span data-stu-id="c912e-148">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="c912e-149">Ceci est illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="c912e-149">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="c912e-150">La version suivante du code précédent illustre la combinaison d’arguments ordinaires, les arguments facultatifs et les paramètres de propriété dans un appel de constructeur.</span><span class="sxs-lookup"><span data-stu-id="c912e-150">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a><span data-ttu-id="c912e-151">Constructeurs de classe héritée</span><span class="sxs-lookup"><span data-stu-id="c912e-151">Constructors in inherited class</span></span>
<span data-ttu-id="c912e-152">Lorsque vous héritez d’une classe de base qui a un constructeur, vous devez spécifier ses arguments dans la clause d’héritage.</span><span class="sxs-lookup"><span data-stu-id="c912e-152">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="c912e-153">Pour plus d’informations, consultez [constructeurs et héritage](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="c912e-153">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="c912e-154">Constructeurs statiques ou des constructeurs de Type</span><span class="sxs-lookup"><span data-stu-id="c912e-154">Static Constructors or Type Constructors</span></span>
<span data-ttu-id="c912e-155">En plus de spécifier le code de création d’objets, statiques `let` et `do` liaisons peuvent être créées dans des types de classe qui s’exécutent avant que le type est tout d’abord utilisé pour effectuer l’initialisation au niveau du type.</span><span class="sxs-lookup"><span data-stu-id="c912e-155">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="c912e-156">Pour plus d’informations, consultez [ `let` liaisons dans les Classes](let-bindings-in-classes.md) et [ `do` liaisons dans les Classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="c912e-156">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c912e-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c912e-157">See Also</span></span>
[<span data-ttu-id="c912e-158">Membres</span><span class="sxs-lookup"><span data-stu-id="c912e-158">Members</span></span>](index.md)
