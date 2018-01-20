---
title: Enregistrements (F#)
description: "Découvrez comment F # enregistrements représentent des agrégats simples de valeurs nommées, éventuellement avec des membres."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a3701ea-4308-4fa1-9b5c-b955c470f17a
ms.openlocfilehash: 478ab74ad32cc6e53daffd1bd6229729149d2a1e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="records"></a><span data-ttu-id="954d8-104">Enregistrements</span><span class="sxs-lookup"><span data-stu-id="954d8-104">Records</span></span>

<span data-ttu-id="954d8-105">Les enregistrements représentent des agrégats simples de valeurs nommées, éventuellement avec des membres.</span><span class="sxs-lookup"><span data-stu-id="954d8-105">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="954d8-106">Depuis 4.1 F #, ils peuvent être soit structs ou référence des types.</span><span class="sxs-lookup"><span data-stu-id="954d8-106">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="954d8-107">Ils sont des types de référence par défaut.</span><span class="sxs-lookup"><span data-stu-id="954d8-107">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="954d8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="954d8-108">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="954d8-109">Notes</span><span class="sxs-lookup"><span data-stu-id="954d8-109">Remarks</span></span>
<span data-ttu-id="954d8-110">Dans la syntaxe précédente, *typename* est le nom du type d’enregistrement, *label1* et *label2* sont des noms de valeurs, appelés *étiquettes*, et *type1* et *type2* sont les types de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="954d8-110">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="954d8-111">*liste des membres* est la liste facultative de membres pour le type.</span><span class="sxs-lookup"><span data-stu-id="954d8-111">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="954d8-112">Vous pouvez utiliser la `[<Struct>]` attribut pour créer un enregistrement de struct plutôt qu’un enregistrement qui est un type référence.</span><span class="sxs-lookup"><span data-stu-id="954d8-112">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="954d8-113">Voici quelques exemples.</span><span class="sxs-lookup"><span data-stu-id="954d8-113">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="954d8-114">Lorsque chaque étiquette se trouve sur une ligne distincte, le point-virgule est facultatif.</span><span class="sxs-lookup"><span data-stu-id="954d8-114">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="954d8-115">Vous pouvez définir des valeurs dans les expressions appelées *enregistrer expressions*.</span><span class="sxs-lookup"><span data-stu-id="954d8-115">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="954d8-116">Le compilateur déduit le type à partir des étiquettes utilisées (si les étiquettes sont suffisamment distinctes de celles des autres types d’enregistrements).</span><span class="sxs-lookup"><span data-stu-id="954d8-116">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="954d8-117">L’expression d’enregistrement placez-le entre accolades ({}).</span><span class="sxs-lookup"><span data-stu-id="954d8-117">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="954d8-118">Le code suivant montre une expression d’enregistrement qui initialise un enregistrement avec trois éléments flottants avec étiquettes `x`, `y` et `z`.</span><span class="sxs-lookup"><span data-stu-id="954d8-118">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="954d8-119">S’il peut y avoir un autre type qui possède également les étiquettes de mêmes, n’utilisez pas la forme abrégée.</span><span class="sxs-lookup"><span data-stu-id="954d8-119">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="954d8-120">Les étiquettes du type plus récemment déclaré ont priorité sur ceux du type déclaré précédemment, c’est le cas dans l’exemple précédent, `mypoint3D` est déduit que `Point3D`.</span><span class="sxs-lookup"><span data-stu-id="954d8-120">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="954d8-121">Vous pouvez spécifier explicitement le type d’enregistrement, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="954d8-121">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="954d8-122">Méthodes peuvent être définies pour les types d’enregistrements, comme pour des types de classe.</span><span class="sxs-lookup"><span data-stu-id="954d8-122">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="954d8-123">Création d’enregistrements à l’aide d’Expressions d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="954d8-123">Creating Records by Using Record Expressions</span></span>
<span data-ttu-id="954d8-124">Vous pouvez initialiser des enregistrements en utilisant les étiquettes qui sont définis dans l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="954d8-124">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="954d8-125">Une expression qui effectue l’opération est appelée un *enregistrer expression*.</span><span class="sxs-lookup"><span data-stu-id="954d8-125">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="954d8-126">Utiliser des accolades pour encadrer l’expression d’enregistrement et le point-virgule comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="954d8-126">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="954d8-127">L’exemple suivant montre comment créer un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="954d8-127">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="954d8-128">Les points-virgules après le dernier champ dans l’expression d’enregistrement et la définition de type sont facultatifs, que les champs soient tous sur une ligne.</span><span class="sxs-lookup"><span data-stu-id="954d8-128">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="954d8-129">Lorsque vous créez un enregistrement, vous devez fournir des valeurs pour chaque champ.</span><span class="sxs-lookup"><span data-stu-id="954d8-129">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="954d8-130">Vous ne pouvez pas référencer les valeurs des autres champs dans l’expression d’initialisation d’un champ.</span><span class="sxs-lookup"><span data-stu-id="954d8-130">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="954d8-131">Dans le code suivant, le type de `myRecord2` est déduit des noms des champs.</span><span class="sxs-lookup"><span data-stu-id="954d8-131">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="954d8-132">Si vous le souhaitez, vous pouvez spécifier le nom de type explicitement.</span><span class="sxs-lookup"><span data-stu-id="954d8-132">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="954d8-133">Une autre forme de construction d’enregistrement peut être utile lorsque vous devez copier un enregistrement existant et éventuellement modifier certaines des valeurs du champ.</span><span class="sxs-lookup"><span data-stu-id="954d8-133">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="954d8-134">La ligne de code suivante illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="954d8-134">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="954d8-135">Cette forme de l’expression d’enregistrement est appelée le *copier et mettre à jour des enregistrement expression*.</span><span class="sxs-lookup"><span data-stu-id="954d8-135">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="954d8-136">Les enregistrements sont immuables par défaut ; Toutefois, vous pouvez facilement créer des enregistrements modifiés à l’aide d’une expression de copie et de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="954d8-136">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="954d8-137">Vous pouvez également spécifier explicitement un champ mutable.</span><span class="sxs-lookup"><span data-stu-id="954d8-137">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="954d8-138">N’utilisez pas l’attribut DefaultValue avec les champs d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="954d8-138">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="954d8-139">Une meilleure approche consiste à définir des instances par défaut des enregistrements avec des champs qui sont initialisés les valeurs par défaut puis utiliser une copie et mise à jour d’expression d’enregistrement pour définir les champs qui diffèrent des valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="954d8-139">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a><span data-ttu-id="954d8-140">Mise en correspondance avec des enregistrements</span><span class="sxs-lookup"><span data-stu-id="954d8-140">Pattern Matching with Records</span></span>
<span data-ttu-id="954d8-141">Enregistrements peuvent être utilisés avec les critères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="954d8-141">Records can be used with pattern matching.</span></span> <span data-ttu-id="954d8-142">Vous pouvez spécifier des champs explicitement et fournir des variables pour les autres champs qui seront attribués lorsqu’une correspondance se produit.</span><span class="sxs-lookup"><span data-stu-id="954d8-142">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="954d8-143">L'exemple de code suivant illustre ceci.</span><span class="sxs-lookup"><span data-stu-id="954d8-143">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="954d8-144">La sortie de ce code est comme suit.</span><span class="sxs-lookup"><span data-stu-id="954d8-144">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="954d8-145">Différences entre les Classes et les enregistrements</span><span class="sxs-lookup"><span data-stu-id="954d8-145">Differences Between Records and Classes</span></span>
<span data-ttu-id="954d8-146">Champs d’enregistrement diffèrent des classes dans la mesure où ils sont automatiquement exposés en tant que propriétés, et ils sont utilisés lors de la création et de copie d’enregistrements.</span><span class="sxs-lookup"><span data-stu-id="954d8-146">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="954d8-147">La construction d’enregistrement diffère également de construction de la classe.</span><span class="sxs-lookup"><span data-stu-id="954d8-147">Record construction also differs from class construction.</span></span> <span data-ttu-id="954d8-148">Dans un type d’enregistrement, vous ne pouvez pas définir un constructeur.</span><span class="sxs-lookup"><span data-stu-id="954d8-148">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="954d8-149">Au lieu de cela, la syntaxe de construction décrite dans cette rubrique s’applique.</span><span class="sxs-lookup"><span data-stu-id="954d8-149">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="954d8-150">Classes ont aucune relation directe entre les paramètres du constructeur, des champs et propriétés.</span><span class="sxs-lookup"><span data-stu-id="954d8-150">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="954d8-151">Comme les types d’union et de structure, les enregistrements ont une sémantique d’égalité structurelle.</span><span class="sxs-lookup"><span data-stu-id="954d8-151">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="954d8-152">Classes ont référence une sémantique d’égalité.</span><span class="sxs-lookup"><span data-stu-id="954d8-152">Classes have reference equality semantics.</span></span> <span data-ttu-id="954d8-153">L’exemple de code suivant illustre cela.</span><span class="sxs-lookup"><span data-stu-id="954d8-153">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="954d8-154">Si vous écrivez le même code avec les classes, les deux objets de classe seraient inégaux parce que les deux valeurs représenteraient deux objets sur le tas et seules les adresses seraient comparées (à moins que le type de classe substitue le `System.Object.Equals` méthode).</span><span class="sxs-lookup"><span data-stu-id="954d8-154">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="954d8-155">Si vous avez besoin de l’égalité pour les enregistrements de référence, ajoutez l’attribut `[<ReferenceEquality>]` au-dessus de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="954d8-155">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="954d8-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="954d8-156">See Also</span></span>
[<span data-ttu-id="954d8-157">Types F#</span><span class="sxs-lookup"><span data-stu-id="954d8-157">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="954d8-158">Classes</span><span class="sxs-lookup"><span data-stu-id="954d8-158">Classes</span></span>](classes.md)

[<span data-ttu-id="954d8-159">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="954d8-159">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="954d8-160">Égalité des références</span><span class="sxs-lookup"><span data-stu-id="954d8-160">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[<span data-ttu-id="954d8-161">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="954d8-161">Pattern Matching</span></span>](pattern-matching.md)
