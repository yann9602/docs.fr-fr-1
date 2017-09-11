---
title: "Classes génériques (guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 17ec9f5d26c01b7f7f7f95026bfdfaa88d709b60
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="9a796-102">Classes génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="9a796-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="9a796-103">Les classes génériques encapsulent des opérations qui ne sont pas spécifiques à un type de données particulier.</span><span class="sxs-lookup"><span data-stu-id="9a796-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="9a796-104">Les classes génériques sont le plus souvent utilisées avec les collections telles que les listes liées, les tables de hachage, les piles, les files d’attente, les arborescences, etc.</span><span class="sxs-lookup"><span data-stu-id="9a796-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="9a796-105">Les opérations telles que l’ajout et la suppression d’éléments dans la collection sont exécutées fondamentalement de la même manière quel que soit le type des données stockées.</span><span class="sxs-lookup"><span data-stu-id="9a796-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="9a796-106">Pour la plupart des scénarios qui nécessitent des classes de collections, l’approche recommandée consiste à utiliser celles fournies dans la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9a796-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET Framework class library.</span></span> <span data-ttu-id="9a796-107">Pour plus d’informations sur l’utilisation de ces classes, consultez [Génériques dans la bibliothèque de classes .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="9a796-107">For more information about using these classes, see [Generics in the .NET Framework Class Library](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span></span>  
  
 <span data-ttu-id="9a796-108">En général, vous créez des classes génériques en commençant par une classe concrète existante et en changeant des types en paramètres de type individuellement jusqu’à ce que vous atteigniez l’équilibre optimal au niveau de la généralisation et de la facilité d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="9a796-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="9a796-109">Lors de la création de vos propres classes génériques, les aspects importants à prendre en considération sont notamment les suivants :</span><span class="sxs-lookup"><span data-stu-id="9a796-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
-   <span data-ttu-id="9a796-110">Quels types généraliser en paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="9a796-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="9a796-111">En règle générale, plus le nombre de types que vous pouvez paramétrer est important, plus votre code est souple et réutilisable.</span><span class="sxs-lookup"><span data-stu-id="9a796-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="9a796-112">Toutefois, une généralisation excessive peut produire un code qui est difficile à lire ou à comprendre par d’autres développeurs.</span><span class="sxs-lookup"><span data-stu-id="9a796-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
-   <span data-ttu-id="9a796-113">Quelles contraintes, le cas échéant, appliquer aux paramètres de type (consultez [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="9a796-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="9a796-114">Il est pertinent d’appliquer le maximum de contraintes possible vous permettant néanmoins de gérer les types que vous devez gérer.</span><span class="sxs-lookup"><span data-stu-id="9a796-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="9a796-115">Par exemple, si vous savez que votre classe générique est destinée uniquement à être utilisée avec les types référence, appliquez la contrainte de classe.</span><span class="sxs-lookup"><span data-stu-id="9a796-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="9a796-116">Cela empêchera l’utilisation involontaire de votre classe avec les types valeur et vous permettra d’utiliser l’opérateur `as` sur `T` et de rechercher les valeurs nulles.</span><span class="sxs-lookup"><span data-stu-id="9a796-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
-   <span data-ttu-id="9a796-117">S’il convient de prendre en compte le comportement générique dans les sous-classes et les classes de base.</span><span class="sxs-lookup"><span data-stu-id="9a796-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="9a796-118">Les classes génériques pouvant servir de classes de base, les considérations de conception qui s’appliquent ici sont les mêmes que pour les classes non génériques.</span><span class="sxs-lookup"><span data-stu-id="9a796-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="9a796-119">Consultez les règles relatives à l’héritage à partir des classes de base génériques plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="9a796-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
-   <span data-ttu-id="9a796-120">S’il convient d’implémenter une ou plusieurs interfaces génériques.</span><span class="sxs-lookup"><span data-stu-id="9a796-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="9a796-121">Par exemple, si vous concevez une classe qui sera utilisée pour créer des éléments dans une collection basée sur les génériques, vous pouvez avoir besoin d’implémenter une interface comme <xref:System.IComparable%601>, où `T` est le type de votre classe.</span><span class="sxs-lookup"><span data-stu-id="9a796-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="9a796-122">Pour obtenir un exemple d’une classe générique simple, consultez [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="9a796-122">For an example of a simple generic class, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span>  
  
 <span data-ttu-id="9a796-123">Les règles pour les paramètres de type et les contraintes ont plusieurs conséquences sur le comportement de classe générique, surtout en ce qui concerne l’héritage et l’accessibilité des membres.</span><span class="sxs-lookup"><span data-stu-id="9a796-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="9a796-124">Avant de continuer, vous devez comprendre quelques termes.</span><span class="sxs-lookup"><span data-stu-id="9a796-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="9a796-125">Pour une classe générique `Node<T>,`, le code client peut référencer la classe soit en spécifiant un argument de type, pour créer un type construit fermé (`Node<int>`),</span><span class="sxs-lookup"><span data-stu-id="9a796-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="9a796-126">soit en laissant le paramètre de type non spécifié, par exemple quand vous spécifiez une classe de base générique, pour créer un type construit ouvert (`Node<T>`).</span><span class="sxs-lookup"><span data-stu-id="9a796-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="9a796-127">Les classes génériques peuvent hériter de classes de base concrètes, construites fermées ou construites ouvertes :</span><span class="sxs-lookup"><span data-stu-id="9a796-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 <span data-ttu-id="9a796-128">[!code-cs[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a796-128">[!code-cs[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]</span></span>  
  
 <span data-ttu-id="9a796-129">Les classes non génériques, également appelées concrètes, peuvent hériter des classes de base construites fermées, mais pas des classes construites ouvertes ni des paramètres de type parce que le code client ne peut en aucune façon fournir au moment de l’exécution l’argument de type requis pour instancier la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9a796-129">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 <span data-ttu-id="9a796-130">[!code-cs[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a796-130">[!code-cs[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]</span></span>  
  
 <span data-ttu-id="9a796-131">Les classes génériques qui héritent de types construits ouverts doivent fournir des arguments de type pour tout paramètre de type de classe de base qui n’est pas partagé par la classe qui hérite, comme cela est indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="9a796-131">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 <span data-ttu-id="9a796-132">[!code-cs[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a796-132">[!code-cs[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]</span></span>  
  
 <span data-ttu-id="9a796-133">Les classes génériques qui héritent des types construits ouverts doivent spécifier des contraintes qui sont un sur-ensemble, ou qui impliquent, des contraintes sur le type de base :</span><span class="sxs-lookup"><span data-stu-id="9a796-133">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 <span data-ttu-id="9a796-134">[!code-cs[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a796-134">[!code-cs[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]</span></span>  
  
 <span data-ttu-id="9a796-135">Les types génériques peuvent utiliser plusieurs paramètres de type et contraintes, comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a796-135">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 <span data-ttu-id="9a796-136">[!code-cs[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a796-136">[!code-cs[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]</span></span>  
  
 <span data-ttu-id="9a796-137">Les types construits ouverts et les types construits fermés peuvent être utilisés comme paramètres de méthode :</span><span class="sxs-lookup"><span data-stu-id="9a796-137">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 <span data-ttu-id="9a796-138">[!code-cs[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a796-138">[!code-cs[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]</span></span>  
  
 <span data-ttu-id="9a796-139">Si une classe générique implémente une interface, toutes les instances de cette classe peuvent être castées à cette interface.</span><span class="sxs-lookup"><span data-stu-id="9a796-139">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="9a796-140">Les classes génériques sont indifférentes.</span><span class="sxs-lookup"><span data-stu-id="9a796-140">Generic classes are invariant.</span></span> <span data-ttu-id="9a796-141">En d’autres termes, si un paramètre d’entrée spécifie un `List<BaseClass>`, vous obtiendrez une erreur de compilation si vous essayez de fournir un `List<DerivedClass>`.</span><span class="sxs-lookup"><span data-stu-id="9a796-141">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a796-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a796-142">See Also</span></span>  
 <span data-ttu-id="9a796-143"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="9a796-143"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="9a796-144">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a796-144">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9a796-145">[Génériques](../../../csharp/programming-guide/generics/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a796-145">[Generics](../../../csharp/programming-guide/generics/index.md) </span></span>  
 <span data-ttu-id="9a796-146">[Saving the State of Enumerators](http://go.microsoft.com/fwlink/?LinkId=112390) </span><span class="sxs-lookup"><span data-stu-id="9a796-146">[Saving the State of Enumerators](http://go.microsoft.com/fwlink/?LinkId=112390) </span></span>  
 [<span data-ttu-id="9a796-147">An Inheritance Puzzle, Part One</span><span class="sxs-lookup"><span data-stu-id="9a796-147">An Inheritance Puzzle, Part One</span></span>](http://go.microsoft.com/fwlink/?LinkId=112380)

