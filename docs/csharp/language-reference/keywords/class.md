---
title: "class (référence C#)"
ms.date: 2017-07-18
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- class_CSharpKeyword
- class
dev_langs:
- CSharp
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cd4fbca0ce7148c571075d31a0e1e4a986d75149
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="class-c-reference"></a><span data-ttu-id="a1af4-102">class (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a1af4-102">class (C# Reference)</span></span>

<span data-ttu-id="a1af4-103">Les classes sont déclarées à l’aide du mot clé `class`, comme l’illustre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a1af4-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates 
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="a1af4-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="a1af4-104">Remarks</span></span>
<span data-ttu-id="a1af4-105">Le langage C# ne permet qu'un seul héritage.</span><span class="sxs-lookup"><span data-stu-id="a1af4-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="a1af4-106">Cela signifie qu’une classe peut uniquement hériter de l’implémentation d’une seule classe de base.</span><span class="sxs-lookup"><span data-stu-id="a1af4-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="a1af4-107">Toutefois, une classe peut implémenter plusieurs interfaces.</span><span class="sxs-lookup"><span data-stu-id="a1af4-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="a1af4-108">Le tableau suivant répertorie des exemples d’héritage de classe et d’implémentation d’interface :</span><span class="sxs-lookup"><span data-stu-id="a1af4-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="a1af4-109">Héritage</span><span class="sxs-lookup"><span data-stu-id="a1af4-109">Inheritance</span></span>|<span data-ttu-id="a1af4-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1af4-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="a1af4-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a1af4-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="a1af4-112">Single</span><span class="sxs-lookup"><span data-stu-id="a1af4-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="a1af4-113">Aucun, implémente deux interfaces</span><span class="sxs-lookup"><span data-stu-id="a1af4-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="a1af4-114">Unique, implémente une seule interface</span><span class="sxs-lookup"><span data-stu-id="a1af4-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="a1af4-115">Les classes que vous déclarez directement dans un espace de noms, non imbriquées dans d’autres classes, peuvent être [public](../../../csharp/language-reference/keywords/public.md) ou [internal](../../../csharp/language-reference/keywords/internal.md).</span><span class="sxs-lookup"><span data-stu-id="a1af4-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](../../../csharp/language-reference/keywords/public.md) or [internal](../../../csharp/language-reference/keywords/internal.md).</span></span> <span data-ttu-id="a1af4-116">Par défaut, les classes sont `internal`.</span><span class="sxs-lookup"><span data-stu-id="a1af4-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="a1af4-117">Les membres de classe, notamment les classes imbriquées, peuvent être [public](../../../csharp/language-reference/keywords/public.md), `protected internal`, [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou [private](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="a1af4-117">Class members, including nested classes, can be [public](../../../csharp/language-reference/keywords/public.md), `protected internal`, [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md).</span></span> <span data-ttu-id="a1af4-118">Par défaut, les membres sont [private](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="a1af4-118">Members are [private](../../../csharp/language-reference/keywords/private.md) by default.</span></span>

<span data-ttu-id="a1af4-119">Pour plus d’informations, consultez [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="a1af4-119">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="a1af4-120">Vous pouvez déclarer des classes génériques qui ont des paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="a1af4-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="a1af4-121">Pour plus d’informations, consultez [Classes génériques](../../../csharp/programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a1af4-121">For more information, see [Generic Classes](../../../csharp/programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="a1af4-122">Une classe peut contenir les déclarations des membres suivants :</span><span class="sxs-lookup"><span data-stu-id="a1af4-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="a1af4-123">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="a1af4-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="a1af4-124">Constantes</span><span class="sxs-lookup"><span data-stu-id="a1af4-124">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="a1af4-125">Champs</span><span class="sxs-lookup"><span data-stu-id="a1af4-125">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="a1af4-126">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="a1af4-126">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="a1af4-127">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a1af4-127">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="a1af4-128">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a1af4-128">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="a1af4-129">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="a1af4-129">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)

- [<span data-ttu-id="a1af4-130">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="a1af4-130">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [<span data-ttu-id="a1af4-131">Événements</span><span class="sxs-lookup"><span data-stu-id="a1af4-131">Events</span></span>](../../../csharp/programming-guide/events/index.md)

- [<span data-ttu-id="a1af4-132">Délégués</span><span class="sxs-lookup"><span data-stu-id="a1af4-132">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

- [<span data-ttu-id="a1af4-133">Classes</span><span class="sxs-lookup"><span data-stu-id="a1af4-133">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="a1af4-134">Interfaces</span><span class="sxs-lookup"><span data-stu-id="a1af4-134">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

- [<span data-ttu-id="a1af4-135">Structs</span><span class="sxs-lookup"><span data-stu-id="a1af4-135">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)

## <a name="example"></a><span data-ttu-id="a1af4-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1af4-136">Example</span></span>
<span data-ttu-id="a1af4-137">L’exemple suivant explique comment déclarer des champs, des constructeurs et des méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="a1af4-137">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="a1af4-138">Il illustre également l’instanciation d’un objet et l’impression des données d’une instance.</span><span class="sxs-lookup"><span data-stu-id="a1af4-138">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="a1af4-139">Dans cet exemple, deux classes sont déclarées.</span><span class="sxs-lookup"><span data-stu-id="a1af4-139">In this example, two classes are declared.</span></span> <span data-ttu-id="a1af4-140">La première, `Child`, contient deux champs privés (`name` et `age`), deux constructeurs publics et une méthode publique.</span><span class="sxs-lookup"><span data-stu-id="a1af4-140">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="a1af4-141">La deuxième, `StringTest`, contient `Main`.</span><span class="sxs-lookup"><span data-stu-id="a1af4-141">The second class, `StringTest`, is used to contain `Main`.</span></span>

<span data-ttu-id="a1af4-142">[!code-cs[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a1af4-142">[!code-cs[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]</span></span>

## <a name="comments"></a><span data-ttu-id="a1af4-143">Commentaires</span><span class="sxs-lookup"><span data-stu-id="a1af4-143">Comments</span></span>
<span data-ttu-id="a1af4-144">Notez que, dans l’exemple précédant, les champs privés (`name` et `age`) ne sont accessibles que par le biais de la méthode publique de la classe `Child`.</span><span class="sxs-lookup"><span data-stu-id="a1af4-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="a1af4-145">Par exemple, vous ne pouvez pas imprimer le nom de l’enfant à partir de la méthode `Main` en utilisant une instruction comme celle-ci :</span><span class="sxs-lookup"><span data-stu-id="a1af4-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="a1af4-146">L’accès aux membres privés de `Child` à partir de `Main` est uniquement possible si `Main` est un membre de la classe.</span><span class="sxs-lookup"><span data-stu-id="a1af4-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="a1af4-147">Du fait que les types déclarés dans une classe sans modificateur d’accès sont par défaut `private`, les données membres dans cet exemple sont toujours `private` si le mot clé est supprimé.</span><span class="sxs-lookup"><span data-stu-id="a1af4-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="a1af4-148">Notez enfin que pour l’objet créé à l’aide du constructeur par défaut (`child3`), le champ de l’âge est initialisé par défaut à la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="a1af4-148">Finally, notice that for the object created using the default constructor (`child3`), the age field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a1af4-149">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a1af4-149">C# Language Specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a1af4-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1af4-150">See Also</span></span>
 <span data-ttu-id="a1af4-151">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="a1af4-151">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="a1af4-152">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a1af4-152">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="a1af4-153">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="a1af4-153">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="a1af4-154">Types référence</span><span class="sxs-lookup"><span data-stu-id="a1af4-154">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)

