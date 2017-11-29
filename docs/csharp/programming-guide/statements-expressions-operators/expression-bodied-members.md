---
title: Membres expression-bodied (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ead1e474fe87bd9fbd0f972bc0f2fc4fefc12ecf
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="636c9-102">Membres expression-bodied (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="636c9-102">Expression-bodied members (C# programming guide)</span></span>
<span data-ttu-id="636c9-103">Les définitions de corps d’expression vous permettent de fournir l’implémentation d’un membre sous une forme lisible et très concise.</span><span class="sxs-lookup"><span data-stu-id="636c9-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="636c9-104">Vous pouvez utiliser une définition de corps d’expression chaque fois que la logique d’un membre pris en charge, comme une méthode ou une propriété, se compose d’une seule expression.</span><span class="sxs-lookup"><span data-stu-id="636c9-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="636c9-105">La syntaxe générale d’une définition de corps d’expression est la suivante :</span><span class="sxs-lookup"><span data-stu-id="636c9-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="636c9-106">où *expression* est une expression valide.</span><span class="sxs-lookup"><span data-stu-id="636c9-106">where *expression* is a valid expression.</span></span> 

<span data-ttu-id="636c9-107">La prise en charge des définitions de corps d’expression a été introduite pour les méthodes et les accesseurs get de propriétés dans C# 6, et a été étendue dans C# 7.</span><span class="sxs-lookup"><span data-stu-id="636c9-107">Support for expression body definitions was introduced for methods and property get accessors in C# 6 and was expanded in C# 7.</span></span> <span data-ttu-id="636c9-108">Vous pouvez utiliser des définitions de corps d’expression avec les membres de type listés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="636c9-108">Expression body definitions can be used with the type members listed in the following table:</span></span> 

|<span data-ttu-id="636c9-109">Membre</span><span class="sxs-lookup"><span data-stu-id="636c9-109">Member</span></span>  |<span data-ttu-id="636c9-110">Prise en charge à compter de</span><span class="sxs-lookup"><span data-stu-id="636c9-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="636c9-111">Méthode</span><span class="sxs-lookup"><span data-stu-id="636c9-111">Method</span></span>](#methods)  |<span data-ttu-id="636c9-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="636c9-112">C# 6</span></span> |
|[<span data-ttu-id="636c9-113">Constructeur</span><span class="sxs-lookup"><span data-stu-id="636c9-113">Constructor</span></span>](#constructors)   |<span data-ttu-id="636c9-114">C# 7</span><span class="sxs-lookup"><span data-stu-id="636c9-114">C# 7</span></span> |
|[<span data-ttu-id="636c9-115">Finaliseur</span><span class="sxs-lookup"><span data-stu-id="636c9-115">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="636c9-116">C# 7</span><span class="sxs-lookup"><span data-stu-id="636c9-116">C# 7</span></span> |
|[<span data-ttu-id="636c9-117">Accesseur get de propriété</span><span class="sxs-lookup"><span data-stu-id="636c9-117">Property Get</span></span>](#property-get-statements)  |<span data-ttu-id="636c9-118">C# 6</span><span class="sxs-lookup"><span data-stu-id="636c9-118">C# 6</span></span> |
|[<span data-ttu-id="636c9-119">Accesseur set de propriété</span><span class="sxs-lookup"><span data-stu-id="636c9-119">Property Set</span></span>](#property-set-statements)  |<span data-ttu-id="636c9-120">C# 7</span><span class="sxs-lookup"><span data-stu-id="636c9-120">C# 7</span></span> |
|[<span data-ttu-id="636c9-121">Indexeur</span><span class="sxs-lookup"><span data-stu-id="636c9-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="636c9-122">C# 7</span><span class="sxs-lookup"><span data-stu-id="636c9-122">C# 7</span></span> |

## <a name="methods"></a><span data-ttu-id="636c9-123">Méthodes</span><span class="sxs-lookup"><span data-stu-id="636c9-123">Methods</span></span>

<span data-ttu-id="636c9-124">Une méthode expression-bodied se compose d’une seule expression qui retourne une valeur dont le type correspond au type de retour de la méthode ou, pour les méthodes qui retournent `void`, qui effectue une opération.</span><span class="sxs-lookup"><span data-stu-id="636c9-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="636c9-125">Par exemple, les types qui substituent la méthode <xref:System.Object.ToString%2A> incluent généralement une expression unique qui retourne la représentation sous forme de chaîne de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="636c9-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span> 

<span data-ttu-id="636c9-126">L’exemple suivant définit une classe `Person` qui substitue la méthode <xref:System.Object.ToString%2A> avec une définition de corps d’expression.</span><span class="sxs-lookup"><span data-stu-id="636c9-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="636c9-127">Il définit également une méthode `Show` qui affiche un nom sur la console.</span><span class="sxs-lookup"><span data-stu-id="636c9-127">It also defines a `Show` method that displays a name to the console.</span></span> <span data-ttu-id="636c9-128">Notez que le mot clé `return` n’est pas utilisé dans la définition de corps d’expression `ToString`.</span><span class="sxs-lookup"><span data-stu-id="636c9-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="636c9-129">Pour plus d’informations, consultez [Méthodes (Guide de programmation C#)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="636c9-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>
 
## <a name="constructors"></a><span data-ttu-id="636c9-130">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="636c9-130">Constructors</span></span>

<span data-ttu-id="636c9-131">Une définition de corps d’expression pour un constructeur se compose généralement d’une seule expression d’assignation ou d’un appel de méthode qui gère les arguments du constructeur ou qui initialise l’état de l’instance.</span><span class="sxs-lookup"><span data-stu-id="636c9-131">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span> 

<span data-ttu-id="636c9-132">L’exemple suivant définit une classe `Location` dont le constructeur a un seul paramètre de chaîne nommé *name*.</span><span class="sxs-lookup"><span data-stu-id="636c9-132">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="636c9-133">La définition de corps d’expression assigne l’argument à la propriété `Name`.</span><span class="sxs-lookup"><span data-stu-id="636c9-133">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="636c9-134">Pour plus d’informations, consultez [Constructeurs (Guide de programmation C#)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="636c9-134">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="636c9-135">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="636c9-135">Finalizers</span></span>

<span data-ttu-id="636c9-136">Une définition de corps d’expression pour un finaliseur contient généralement des instructions de nettoyage, telles que des instructions qui libèrent les ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="636c9-136">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="636c9-137">L’exemple suivant définit un finaliseur qui utilise une définition de corps d’expression pour indiquer que le finaliseur a été appelé.</span><span class="sxs-lookup"><span data-stu-id="636c9-137">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="636c9-138">Pour plus d’informations, consultez [Finaliseurs (Guide de programmation C#)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="636c9-138">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="property-get-statements"></a><span data-ttu-id="636c9-139">Instructions get de propriété</span><span class="sxs-lookup"><span data-stu-id="636c9-139">Property get statements</span></span>

<span data-ttu-id="636c9-140">Si vous choisissez d’implémenter un accesseur get de propriété vous-même, vous pouvez utiliser une définition de corps d’expression pour les expressions uniques qui retournent simplement la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="636c9-140">If you choose to implement a property get accessor yourself, you can use an expression body definition for single expressions that simply return the property value.</span></span> <span data-ttu-id="636c9-141">Notez que l’instruction `return` n’est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="636c9-141">Note that the `return` statement isn't used.</span></span>

<span data-ttu-id="636c9-142">L’exemple suivant définit une propriété `Location.Name` dont l’accesseur get de propriété retourne la valeur du champ `locationName` privé qui stocke la propriété.</span><span class="sxs-lookup"><span data-stu-id="636c9-142">The following example defines a `Location.Name` property whose property get accessor returns the value of the private `locationName` field that backs the property.</span></span> 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="636c9-143">Les propriétés en lecture seule qui utilisent une définition de corps d’expression peuvent être implémentées sans instruction `set` explicite.</span><span class="sxs-lookup"><span data-stu-id="636c9-143">Read-only properties that use an expression body definition can be implemented without an explicit `set` statement.</span></span> <span data-ttu-id="636c9-144">La syntaxe est :</span><span class="sxs-lookup"><span data-stu-id="636c9-144">The syntax is:</span></span>

```csharp
PropertyName => returnValue;
```

<span data-ttu-id="636c9-145">L’exemple suivant définit une classe `Location` dont la propriété `Name` en lecture seule est implémentée en tant que définition de corps d’expression qui retourne la valeur du champ `locationName` privé.</span><span class="sxs-lookup"><span data-stu-id="636c9-145">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="636c9-146">Pour plus d’informations, consultez [Propriétés (Guide de programmation C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="636c9-146">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="property-set-statements"></a><span data-ttu-id="636c9-147">Instructions set de propriété</span><span class="sxs-lookup"><span data-stu-id="636c9-147">Property set statements</span></span>

<span data-ttu-id="636c9-148">Si vous choisissez d’implémenter un accesseur set de propriété vous-même, vous pouvez utiliser une définition de corps d’expression pour une expression à une ligne qui assigne une valeur au champ qui stocke la propriété.</span><span class="sxs-lookup"><span data-stu-id="636c9-148">If you choose to implement a property set accessor yourself, you can use an expression body definition for a single-line expression that assigns a value to the field that backs the property.</span></span>

<span data-ttu-id="636c9-149">L’exemple suivant définit une propriété `Location.Name` dont l’instruction set de propriété assigne son argument d’entrée au champ `locationName` privé qui stocke la propriété.</span><span class="sxs-lookup"><span data-stu-id="636c9-149">The following example defines a `Location.Name` property whose property set statement assigns its input argument to the private `locationName` field that backs the property.</span></span>

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="636c9-150">Pour plus d’informations, consultez [Propriétés (Guide de programmation C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="636c9-150">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="636c9-151">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="636c9-151">Indexers</span></span>

<span data-ttu-id="636c9-152">Comme les propriétés, les accesseurs get et set d’un indexeur sont composés de définitions de corps d’expression si l’accesseur get est constitué d’une seule instruction qui retourne une valeur ou si l’accesseur set effectue une assignation simple.</span><span class="sxs-lookup"><span data-stu-id="636c9-152">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="636c9-153">L’exemple suivant définit une classe nommée `Sports` qui inclut un tableau <xref:System.String> interne contenant les noms de plusieurs sports.</span><span class="sxs-lookup"><span data-stu-id="636c9-153">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="636c9-154">Les accesseurs get et set de l’indexeur sont implémentés en tant que définitions de corps d’expression.</span><span class="sxs-lookup"><span data-stu-id="636c9-154">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

<span data-ttu-id="636c9-155">Pour plus d’informations, consultez [Indexeurs (Guide de programmation C#)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="636c9-155">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>

