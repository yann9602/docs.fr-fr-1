---
title: Liaisons let dans les classes (F#)
description: "Apprendre à définir des champs privés et des fonctions privées pour des classes F # à l’aide de liaisons 'let' dans la définition de classe."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9d3710f5-68b1-4e4c-b02b-27fe018f20e8
ms.openlocfilehash: 1337cc0794e366e8c39745f5c45065362c9c38c9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="8fff4-104">Liaisons let dans des classes</span><span class="sxs-lookup"><span data-stu-id="8fff4-104">let Bindings in Classes</span></span>

<span data-ttu-id="8fff4-105">Vous pouvez définir des champs privés et des fonctions privées pour les classes F # à l’aide de `let` liaisons dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="8fff4-105">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>


## <a name="syntax"></a><span data-ttu-id="8fff4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fff4-106">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="8fff4-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="8fff4-107">Remarks</span></span>
<span data-ttu-id="8fff4-108">La syntaxe précédente apparaît après les déclarations de titre et l’héritage de classe, mais avant les définitions de membre.</span><span class="sxs-lookup"><span data-stu-id="8fff4-108">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="8fff4-109">La syntaxe est similaire à celle de `let` liaisons en dehors des classes, mais les noms définis dans une classe ont une portée limitée à la classe.</span><span class="sxs-lookup"><span data-stu-id="8fff4-109">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="8fff4-110">A `let` liaison crée un champ privé ou une fonction ; pour exposer des données ou les fonctions déclarer publiquement, une propriété ou une méthode membre.</span><span class="sxs-lookup"><span data-stu-id="8fff4-110">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="8fff4-111">A `let` de liaison qui n’est pas statique est appelée une instance `let` liaison.</span><span class="sxs-lookup"><span data-stu-id="8fff4-111">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="8fff4-112">Instance `let` liaisons s’exécutent lorsque des objets sont créés.</span><span class="sxs-lookup"><span data-stu-id="8fff4-112">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="8fff4-113">Statique `let` liaisons font partie de l’initialiseur statique pour la classe, qui est garantie à exécuter avant le type est utilisé pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="8fff4-113">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="8fff4-114">Le code au sein de l’instance `let` liaisons puissent utiliser les paramètres du constructeur principal.</span><span class="sxs-lookup"><span data-stu-id="8fff4-114">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="8fff4-115">Attributs et les modificateurs d’accessibilité ne sont pas autorisés sur `let` liaisons dans les classes.</span><span class="sxs-lookup"><span data-stu-id="8fff4-115">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="8fff4-116">Les exemples de code suivants illustrent plusieurs types de `let` liaisons dans les classes.</span><span class="sxs-lookup"><span data-stu-id="8fff4-116">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="8fff4-117">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="8fff4-117">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="8fff4-118">Autres manières de créer des champs</span><span class="sxs-lookup"><span data-stu-id="8fff4-118">Alternative Ways to Create Fields</span></span>
<span data-ttu-id="8fff4-119">Vous pouvez également utiliser le `val` (mot clé) pour créer un champ privé.</span><span class="sxs-lookup"><span data-stu-id="8fff4-119">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="8fff4-120">Lorsque vous utilisez la `val` (mot clé), le champ pas une valeur est attribué lors de l’objet est créé, mais est initialisé avec une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8fff4-120">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="8fff4-121">Pour plus d’informations, consultez [champs explicites : val (mot clé)](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="8fff4-121">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="8fff4-122">Vous pouvez également définir des champs privés dans une classe en utilisant une définition de membre et en ajoutant le mot clé `private` à la définition.</span><span class="sxs-lookup"><span data-stu-id="8fff4-122">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="8fff4-123">Cela peut être utile si vous envisagez de modifier l’accessibilité d’un membre sans réécrire votre code.</span><span class="sxs-lookup"><span data-stu-id="8fff4-123">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="8fff4-124">Pour plus d’informations, consultez [Contrôle d’accès](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="8fff4-124">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8fff4-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fff4-125">See Also</span></span>
[<span data-ttu-id="8fff4-126">Membres</span><span class="sxs-lookup"><span data-stu-id="8fff4-126">Members</span></span>](index.md)

[<span data-ttu-id="8fff4-127">Liaisons `do` dans des classes</span><span class="sxs-lookup"><span data-stu-id="8fff4-127">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)

[<span data-ttu-id="8fff4-128">`let`Liaisons</span><span class="sxs-lookup"><span data-stu-id="8fff4-128">`let` Bindings</span></span>](../functions/let-bindings.md)
