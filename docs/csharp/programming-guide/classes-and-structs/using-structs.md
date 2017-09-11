---
title: Utilisation de structs (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
caps.latest.revision: 28
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
ms.openlocfilehash: 67fa4f764e6e40041e4b8e37eccbd1adb2b509d3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-structs-c-programming-guide"></a><span data-ttu-id="d57b7-102">Utilisation de structs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="d57b7-102">Using Structs (C# Programming Guide)</span></span>
<span data-ttu-id="d57b7-103">Le type `struct` est approprié pour représenter des objets légers tels que `Point`, `Rectangle`et `Color`.</span><span class="sxs-lookup"><span data-stu-id="d57b7-103">The `struct` type is suitable for representing lightweight objects such as `Point`, `Rectangle`, and `Color`.</span></span> <span data-ttu-id="d57b7-104">Bien qu’il soit aussi pratique de représenter un point comme [classe](../../../csharp/language-reference/keywords/class.md) avec des [propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), un [struct](../../../csharp/language-reference/keywords/struct.md) peut être plus efficace dans certains scénarios.</span><span class="sxs-lookup"><span data-stu-id="d57b7-104">Although it is just as convenient to represent a point as a [class](../../../csharp/language-reference/keywords/class.md) with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), a [struct](../../../csharp/language-reference/keywords/struct.md) might be more efficient in some scenarios.</span></span> <span data-ttu-id="d57b7-105">Par exemple, si vous déclarez un tableau de 1 000 objets `Point` , vous devez allouer de la mémoire supplémentaire pour faire référence à chacun des objets. Dans ce cas, un struct est moins onéreux.</span><span class="sxs-lookup"><span data-stu-id="d57b7-105">For example, if you declare an array of 1000 `Point` objects, you will allocate additional memory for referencing each object; in this case, a struct would be less expensive.</span></span> <span data-ttu-id="d57b7-106">Étant donné que le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] contient un objet appelé <xref:System.Drawing.Point>, le struct dans cet exemple est nommé à la place « CoOrds ».</span><span class="sxs-lookup"><span data-stu-id="d57b7-106">Because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] contains an object called <xref:System.Drawing.Point>, the struct in this example is named "CoOrds" instead.</span></span>  
  
 <span data-ttu-id="d57b7-107">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d57b7-107">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span></span>  
  
 <span data-ttu-id="d57b7-108">Définir un constructeur par défaut (sans paramètre) pour un struct constitue une erreur.</span><span class="sxs-lookup"><span data-stu-id="d57b7-108">It is an error to define a default (parameterless) constructor for a struct.</span></span> <span data-ttu-id="d57b7-109">Vous ne devez pas non plus initialiser un champ d'instance dans le corps d'un struct.</span><span class="sxs-lookup"><span data-stu-id="d57b7-109">It is also an error to initialize an instance field in a struct body.</span></span> <span data-ttu-id="d57b7-110">Vous pouvez initialiser des membres de struct uniquement en utilisant un constructeur paramétrable ou en accédant individuellement aux membres après que le struct a été déclaré.</span><span class="sxs-lookup"><span data-stu-id="d57b7-110">You can initialize struct members only by using a parameterized constructor or by accessing the members individually after the struct is declared.</span></span> <span data-ttu-id="d57b7-111">Tout membre privé (ou inaccessible) peut uniquement être initialisé dans un constructeur.</span><span class="sxs-lookup"><span data-stu-id="d57b7-111">Any private or otherwise inaccessible members can be initialized only in a constructor.</span></span>  
  
 <span data-ttu-id="d57b7-112">Quand vous employez l’opérateur [new](../../../csharp/language-reference/keywords/new.md) pour créer un objet struct, celui-ci est créé et le constructeur approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="d57b7-112">When you create a struct object using the [new](../../../csharp/language-reference/keywords/new.md) operator, it gets created and the appropriate constructor is called.</span></span> <span data-ttu-id="d57b7-113">Contrairement aux classes, les structs peuvent être instanciés sans avoir recours à l’opérateur `new` .</span><span class="sxs-lookup"><span data-stu-id="d57b7-113">Unlike classes, structs can be instantiated without using the `new` operator.</span></span> <span data-ttu-id="d57b7-114">Dans un tel cas, il n’y a pas d’appel au constructeur, ce qui rend l’allocation plus efficace.</span><span class="sxs-lookup"><span data-stu-id="d57b7-114">In such a case, there is no constructor call, which makes the allocation more efficient.</span></span> <span data-ttu-id="d57b7-115">Toutefois, les champs ne sont pas assignés et l’objet ne peut pas être utilisé tant que tous les champs ne sont pas initialisés.</span><span class="sxs-lookup"><span data-stu-id="d57b7-115">However, the fields will remain unassigned and the object cannot be used until all of the fields are initialized.</span></span>  
  
 <span data-ttu-id="d57b7-116">Lorsqu'un struct contient un type référence en tant que membre, le constructeur par défaut du membre doit être appelé explicitement, sinon le membre reste non assigné et le struct ne peut pas être utilisé.</span><span class="sxs-lookup"><span data-stu-id="d57b7-116">When a struct contains a reference type as a member, the default constructor of the member must be invoked explicitly, otherwise the member remains unassigned and the struct cannot be used.</span></span> <span data-ttu-id="d57b7-117">(Cela provoque l’erreur du compilateur CS0171.)</span><span class="sxs-lookup"><span data-stu-id="d57b7-117">(This results in compiler error CS0171.)</span></span>  
  
 <span data-ttu-id="d57b7-118">Il n'existe pas d'héritage pour un struct comme il en existe pour une classe.</span><span class="sxs-lookup"><span data-stu-id="d57b7-118">There is no inheritance for structs as there is for classes.</span></span> <span data-ttu-id="d57b7-119">Un struct ne peut pas hériter d'un autre struct ou d'une classe ; il ne peut pas non plus servir de base à une classe.</span><span class="sxs-lookup"><span data-stu-id="d57b7-119">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="d57b7-120">Toutefois, les structs héritent de la classe de base <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="d57b7-120">Structs, however, inherit from the base class <xref:System.Object>.</span></span> <span data-ttu-id="d57b7-121">Un struct peut implémenter des interfaces exactement de la même manière que les classes.</span><span class="sxs-lookup"><span data-stu-id="d57b7-121">A struct can implement interfaces, and it does that exactly as classes do.</span></span>  
  
 <span data-ttu-id="d57b7-122">Vous ne pouvez pas déclarer une classe à l’aide du mot clé `struct`.</span><span class="sxs-lookup"><span data-stu-id="d57b7-122">You cannot declare a class using the keyword `struct`.</span></span> <span data-ttu-id="d57b7-123">En C#, les classes et les structs ont une sémantique différente.</span><span class="sxs-lookup"><span data-stu-id="d57b7-123">In C#, classes and structs are semantically different.</span></span> <span data-ttu-id="d57b7-124">Un struct est un type valeur, alors qu'une classe est un type référence.</span><span class="sxs-lookup"><span data-stu-id="d57b7-124">A struct is a value type, while a class is a reference type.</span></span> <span data-ttu-id="d57b7-125">Pour plus d’informations, consultez [Types valeur](../../../csharp/language-reference/keywords/value-types.md).</span><span class="sxs-lookup"><span data-stu-id="d57b7-125">For more information, see [Value Types](../../../csharp/language-reference/keywords/value-types.md).</span></span>  
  
 <span data-ttu-id="d57b7-126">Sauf si vous avez besoin d’une sémantique de type référence, une petite classe peut être gérée plus efficacement par le système si vous la déclarez plutôt sous forme de struct.</span><span class="sxs-lookup"><span data-stu-id="d57b7-126">Unless you need reference-type semantics, a small class may be more efficiently handled by the system if you declare it as a struct instead.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="d57b7-127">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="d57b7-127">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="d57b7-128">Description</span><span class="sxs-lookup"><span data-stu-id="d57b7-128">Description</span></span>  
 <span data-ttu-id="d57b7-129">Cet exemple illustre l’initialisation du type `struct` à l’aide des constructeurs par défaut et des constructeurs paramétrables.</span><span class="sxs-lookup"><span data-stu-id="d57b7-129">This example demonstrates `struct` initialization using both default and parameterized constructors.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d57b7-130">Code</span><span class="sxs-lookup"><span data-stu-id="d57b7-130">Code</span></span>  
 <span data-ttu-id="d57b7-131">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d57b7-131">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span></span>  
  
 <span data-ttu-id="d57b7-132">[!code-cs[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="d57b7-132">[!code-cs[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="d57b7-133">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="d57b7-133">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="d57b7-134">Description</span><span class="sxs-lookup"><span data-stu-id="d57b7-134">Description</span></span>  
 <span data-ttu-id="d57b7-135">Cet exemple montre une caractéristique propre aux structs.</span><span class="sxs-lookup"><span data-stu-id="d57b7-135">This example demonstrates a feature that is unique to structs.</span></span> <span data-ttu-id="d57b7-136">Il crée un objet CoOrds sans utiliser l’opérateur `new` .</span><span class="sxs-lookup"><span data-stu-id="d57b7-136">It creates a CoOrds object without using the `new` operator.</span></span> <span data-ttu-id="d57b7-137">Si vous remplacez le mot `struct` par le mot `class`, le programme ne peut pas se compiler.</span><span class="sxs-lookup"><span data-stu-id="d57b7-137">If you replace the word `struct` with the word `class`, the program will not compile.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d57b7-138">Code</span><span class="sxs-lookup"><span data-stu-id="d57b7-138">Code</span></span>  
 <span data-ttu-id="d57b7-139">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d57b7-139">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span></span>  
  
 <span data-ttu-id="d57b7-140">[!code-cs[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="d57b7-140">[!code-cs[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d57b7-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d57b7-141">See Also</span></span>  
 <span data-ttu-id="d57b7-142">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d57b7-142">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d57b7-143">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="d57b7-143">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 [<span data-ttu-id="d57b7-144">Structs</span><span class="sxs-lookup"><span data-stu-id="d57b7-144">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)

