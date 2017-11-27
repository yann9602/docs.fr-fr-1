---
title: Structures (F#)
description: "En savoir plus sur la structure F #, un type d’objet compact souvent plus efficace qu’une classe pour les types avec une petite quantité de données et un comportement simple."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 50819506-3210-418f-9602-0ee1c9a52177
ms.openlocfilehash: 542b69a5aacb8fcfb0e8f6d6c943fe1954c4c59c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="structures"></a><span data-ttu-id="856b8-104">Structures</span><span class="sxs-lookup"><span data-stu-id="856b8-104">Structures</span></span>

<span data-ttu-id="856b8-105">A *structure* est un type d’objet compact qui peut être plus efficace qu’une classe pour les types qui ont une petite quantité de données et un comportement simple.</span><span class="sxs-lookup"><span data-stu-id="856b8-105">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="856b8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="856b8-106">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements
```

## <a name="remarks"></a><span data-ttu-id="856b8-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="856b8-107">Remarks</span></span>
<span data-ttu-id="856b8-108">Les structures sont *types valeur*, ce qui signifie qu’elles sont stockées directement sur la pile ou, lorsqu’ils sont utilisés en tant que champs ou éléments de tableau, inline dans le parent de type.</span><span class="sxs-lookup"><span data-stu-id="856b8-108">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="856b8-109">Contrairement aux classes et aux enregistrements, les structures ont une sémantique de passage par valeur.</span><span class="sxs-lookup"><span data-stu-id="856b8-109">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="856b8-110">Cela signifie qu'elles sont principalement utilisées pour les petits volumes de données qui sont fréquemment sollicités et copiés.</span><span class="sxs-lookup"><span data-stu-id="856b8-110">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="856b8-111">Dans la syntaxe précédente, deux formes sont présentes.</span><span class="sxs-lookup"><span data-stu-id="856b8-111">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="856b8-112">La première n'est pas la syntaxe simplifiée, mais elle est néanmoins fréquemment utilisée, car quand vous employez les mots clés `struct` et `end`, vous pouvez omettre l'attribut `StructAttribute` qui apparaît dans la seconde forme.</span><span class="sxs-lookup"><span data-stu-id="856b8-112">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="856b8-113">Vous pouvez abréger `StructAttribute` en `Struct`.</span><span class="sxs-lookup"><span data-stu-id="856b8-113">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="856b8-114">Le *éléments de définition de type* dans la syntaxe précédente représente les définitions et déclarations de membre.</span><span class="sxs-lookup"><span data-stu-id="856b8-114">The *type-definition-elements* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="856b8-115">Les structures peuvent avoir des constructeurs et des champs modifiables et non modifiables, et peuvent déclarer des membres et des implémentations d'interface.</span><span class="sxs-lookup"><span data-stu-id="856b8-115">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="856b8-116">Pour plus d’informations, consultez [membres](members/index.md).</span><span class="sxs-lookup"><span data-stu-id="856b8-116">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="856b8-117">Les structures ne peuvent pas participer à l'héritage, ne peuvent pas contenir les liaisons `let` ou `do`, et ne peuvent pas comporter de manière récursive les champs de leur propre type (bien qu'elles puissent contenir des cellules de référence qui référencent leur propre type).</span><span class="sxs-lookup"><span data-stu-id="856b8-117">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="856b8-118">Étant donné que les structures n'autorisent pas les liaisons `let`, vous devez déclarer leurs champs à l'aide du mot clé `val`.</span><span class="sxs-lookup"><span data-stu-id="856b8-118">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="856b8-119">Le mot clé `val` définit un champ et son type, mais n'autorise pas l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="856b8-119">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="856b8-120">À la place, les déclarations `val` sont initialisées à la valeur zéro ou null.</span><span class="sxs-lookup"><span data-stu-id="856b8-120">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="856b8-121">Pour cette raison, les structures ayant un constructeur implicite (c'est-à-dire les paramètres qui sont fournis immédiatement après le nom de la structure dans la déclaration) requièrent que les déclarations `val` soient annotées avec l'attribut `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="856b8-121">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="856b8-122">Les structures ayant un constructeur défini prennent toujours en charge l'initialisation à zéro.</span><span class="sxs-lookup"><span data-stu-id="856b8-122">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="856b8-123">Par conséquent, l'attribut `DefaultValue` est une déclaration selon laquelle une telle valeur égale à zéro est valide pour le champ.</span><span class="sxs-lookup"><span data-stu-id="856b8-123">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="856b8-124">Les constructeurs implicites pour les structures n'exécutent aucune action, car les liaisons `let` et `do` ne sont pas autorisées sur le type, mais les valeurs de paramètre de constructeur implicite passées sont disponibles en tant que champs privés.</span><span class="sxs-lookup"><span data-stu-id="856b8-124">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="856b8-125">Les constructeurs explicites peuvent impliquer l'initialisation des valeurs de champ.</span><span class="sxs-lookup"><span data-stu-id="856b8-125">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="856b8-126">Quand une structure a un constructeur explicite, elle prend toujours en charge l'initialisation à zéro ; toutefois, vous n'utilisez pas l'attribut `DefaultValue` sur les déclarations `val`, car il est en conflit avec le constructeur explicite.</span><span class="sxs-lookup"><span data-stu-id="856b8-126">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="856b8-127">Pour plus d’informations sur `val` déclarations, consultez [champs explicites : le `val` mot clé](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="856b8-127">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="856b8-128">Les attributs et les modificateurs d'accessibilité sont autorisés sur les structures et suivent les mêmes règles que celles des autres types.</span><span class="sxs-lookup"><span data-stu-id="856b8-128">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="856b8-129">Pour plus d’informations, consultez [attributs](attributes.md) et [le contrôle d’accès](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="856b8-129">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="856b8-130">Les exemples de code suivants illustrent des définitions de structure.</span><span class="sxs-lookup"><span data-stu-id="856b8-130">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="856b8-131">Les enregistrements de struct et les Unions discriminées</span><span class="sxs-lookup"><span data-stu-id="856b8-131">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="856b8-132">À compter de F # 4.1, vous pouvez représenter [enregistrements](records.md) et [les Unions discriminées](discriminated-unions.md) en tant que structures avec le `[<Struct>]` attribut.</span><span class="sxs-lookup"><span data-stu-id="856b8-132">Starting with F# 4.1, you can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="856b8-133">Consultez chaque article pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="856b8-133">See each article to learn more.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="856b8-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="856b8-134">See Also</span></span>
[<span data-ttu-id="856b8-135">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="856b8-135">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="856b8-136">Classes</span><span class="sxs-lookup"><span data-stu-id="856b8-136">Classes</span></span>](classes.md)

[<span data-ttu-id="856b8-137">Enregistrements</span><span class="sxs-lookup"><span data-stu-id="856b8-137">Records</span></span>](records.md)

[<span data-ttu-id="856b8-138">Membres</span><span class="sxs-lookup"><span data-stu-id="856b8-138">Members</span></span>](members/index.md)
