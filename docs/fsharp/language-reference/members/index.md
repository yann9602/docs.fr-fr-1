---
title: Membres (F#)
description: "En savoir plus sur les membres de l’objet dans le langage de programmation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e472f50a-4939-4e62-abbc-471f8f265790
ms.openlocfilehash: ca34c8d073594791ec268a85ad56f50cc6d9e435
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="members"></a><span data-ttu-id="8b15a-104">Membres</span><span class="sxs-lookup"><span data-stu-id="8b15a-104">Members</span></span>

<span data-ttu-id="8b15a-105">Cette section décrit les membres de types d’objet F#.</span><span class="sxs-lookup"><span data-stu-id="8b15a-105">This section describes members of F# object types.</span></span>


## <a name="remarks"></a><span data-ttu-id="8b15a-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="8b15a-106">Remarks</span></span>
<span data-ttu-id="8b15a-107">Les *membres* sont des fonctionnalités qui font partie d’une définition de type et qui sont déclarées avec le mot clé `member`.</span><span class="sxs-lookup"><span data-stu-id="8b15a-107">*Members* are features that are part of a type definition and are declared with the `member` keyword.</span></span> <span data-ttu-id="8b15a-108">Les types d’objet F#, comme les enregistrements, les classes, les unions discriminées, les interfaces et les structures, prennent en charge les membres.</span><span class="sxs-lookup"><span data-stu-id="8b15a-108">F# object types such as records, classes, discriminated unions, interfaces, and structures support members.</span></span> <span data-ttu-id="8b15a-109">Pour plus d’informations, consultez [Enregistrements](../records.md), [Classes](../classes.md), [Unions discriminées](../discriminated-Unions.md), [Interfaces](../interfaces.md) et [Structures](../structures.md).</span><span class="sxs-lookup"><span data-stu-id="8b15a-109">For more information, see [Records](../records.md), [Classes](../classes.md), [Discriminated Unions](../discriminated-Unions.md), [Interfaces](../interfaces.md), and [Structures](../structures.md).</span></span>

<span data-ttu-id="8b15a-110">Les membres constituent en général l’interface publique d’un type ; c’est pourquoi ils sont publics, sauf spécification contraire.</span><span class="sxs-lookup"><span data-stu-id="8b15a-110">Members typically make up the public interface for a type, which is why they are public unless otherwise specified.</span></span> <span data-ttu-id="8b15a-111">Les membres peuvent également être déclarés comme privés ou internes.</span><span class="sxs-lookup"><span data-stu-id="8b15a-111">Members can also be declared private or internal.</span></span> <span data-ttu-id="8b15a-112">Pour plus d’informations, consultez [Contrôle d’accès](../access-Control.md).</span><span class="sxs-lookup"><span data-stu-id="8b15a-112">For more information, see [Access Control](../access-Control.md).</span></span> <span data-ttu-id="8b15a-113">Des signatures peuvent également être utilisées pour les types pour exposer ou ne pas exposer certains membres d’un type.</span><span class="sxs-lookup"><span data-stu-id="8b15a-113">Signatures for types can also be used to expose or not expose certain members of a type.</span></span> <span data-ttu-id="8b15a-114">Pour plus d’informations, consultez [Signatures](../signatures.md).</span><span class="sxs-lookup"><span data-stu-id="8b15a-114">For more information, see [Signatures](../signatures.md).</span></span>

<span data-ttu-id="8b15a-115">Les champs privés et les liaisons `do`, qui sont uniquement utilisés avec des classes, ne sont pas de vrais membres parce qu’ils ne font jamais partie de l’interface publique d’un type et ne sont pas déclarés avec le mot clé `member`. Toutefois, ils sont décrits dans cette section.</span><span class="sxs-lookup"><span data-stu-id="8b15a-115">Private fields and `do` bindings, which are used only with classes, are not true members, because they are never part of the public interface of a type and are not declared with the `member` keyword, but they are described in this section also.</span></span>


## <a name="related-topics"></a><span data-ttu-id="8b15a-116">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="8b15a-116">Related Topics</span></span>


|<span data-ttu-id="8b15a-117">Rubrique</span><span class="sxs-lookup"><span data-stu-id="8b15a-117">Topic</span></span>|<span data-ttu-id="8b15a-118">Description</span><span class="sxs-lookup"><span data-stu-id="8b15a-118">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="8b15a-119">Liaisons `let` dans des classes</span><span class="sxs-lookup"><span data-stu-id="8b15a-119">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)|<span data-ttu-id="8b15a-120">Décrit la définition de champs et de fonctions privés dans des classes.</span><span class="sxs-lookup"><span data-stu-id="8b15a-120">Describes the definition of private fields and functions in classes.</span></span>|
|[<span data-ttu-id="8b15a-121">Liaisons `do` dans des classes</span><span class="sxs-lookup"><span data-stu-id="8b15a-121">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)|<span data-ttu-id="8b15a-122">Décrit la spécification du code d’initialisation d’objet.</span><span class="sxs-lookup"><span data-stu-id="8b15a-122">Describes the specification of object initialization code.</span></span>|
|[<span data-ttu-id="8b15a-123">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8b15a-123">Properties</span></span>](properties.md)|<span data-ttu-id="8b15a-124">Décrit les membres de propriété dans les classes et d’autres types.</span><span class="sxs-lookup"><span data-stu-id="8b15a-124">Describes property members in classes and other types.</span></span>|
|[<span data-ttu-id="8b15a-125">Propriétés indexées</span><span class="sxs-lookup"><span data-stu-id="8b15a-125">Indexed Properties</span></span>](indexed-properties.md)|<span data-ttu-id="8b15a-126">Décrit les propriétés de type tableau dans des classes et d’autres types.</span><span class="sxs-lookup"><span data-stu-id="8b15a-126">Describes array-like properties in classes and other types.</span></span>|
|[<span data-ttu-id="8b15a-127">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8b15a-127">Methods</span></span>](methods.md)|<span data-ttu-id="8b15a-128">Décrit les fonctions qui sont membres d’un type.</span><span class="sxs-lookup"><span data-stu-id="8b15a-128">Describes functions that are members of a type.</span></span>|
|[<span data-ttu-id="8b15a-129">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="8b15a-129">Constructors</span></span>](constructors.md)|<span data-ttu-id="8b15a-130">Décrit les fonctions spéciales qui initialisent des objets d’un type.</span><span class="sxs-lookup"><span data-stu-id="8b15a-130">Describes special functions that initialize objects of a type.</span></span>|
|[<span data-ttu-id="8b15a-131">Surcharge d'opérateur</span><span class="sxs-lookup"><span data-stu-id="8b15a-131">Operator Overloading</span></span>](../operator-overloading.md)|<span data-ttu-id="8b15a-132">Décrit la définition d’opérateurs personnalisés pour les types.</span><span class="sxs-lookup"><span data-stu-id="8b15a-132">Describes the definition of customized operators for types.</span></span>|
|[<span data-ttu-id="8b15a-133">Événements</span><span class="sxs-lookup"><span data-stu-id="8b15a-133">Events</span></span>](events.md)|<span data-ttu-id="8b15a-134">Décrit la définition d’événements et la prise en charge de la gestion des événements en F#.</span><span class="sxs-lookup"><span data-stu-id="8b15a-134">Describes the definition of events and event handling support in F#.</span></span>|
|[<span data-ttu-id="8b15a-135">Champs explicites : mot clé `val`</span><span class="sxs-lookup"><span data-stu-id="8b15a-135">Explicit Fields: The `val` Keyword</span></span>](explicit-fields-the-val-keyword.md)|<span data-ttu-id="8b15a-136">Décrit la définition de champs non initialisés dans un type.</span><span class="sxs-lookup"><span data-stu-id="8b15a-136">Describes the definition of uninitialized fields in a type.</span></span>|
