---
title: "Approfondissement du système de type commun"
description: "Approfondissement du système de type commun"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: b5482a1d-7bdc-40fe-aa45-10df930ceb5b
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 6be672acc84a76106e25b82574acad16beb4a8ac
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="common-type-system-in-depth"></a><span data-ttu-id="a084c-104">Approfondissement du système de type commun</span><span class="sxs-lookup"><span data-stu-id="a084c-104">Common type system in depth</span></span>

<span data-ttu-id="a084c-105">Cette rubrique contient les sections suivantes qui explorent le système de type commun de manière approfondie :</span><span class="sxs-lookup"><span data-stu-id="a084c-105">This topic contains the following sections that explore the common type system in depth:</span></span>

* [<span data-ttu-id="a084c-106">Types dans .NET</span><span class="sxs-lookup"><span data-stu-id="a084c-106">Types in .NET</span></span>](#types-in-net)

* [<span data-ttu-id="a084c-107">Définitions de types</span><span class="sxs-lookup"><span data-stu-id="a084c-107">Type definitions</span></span>](#type-definitions)

* [<span data-ttu-id="a084c-108">Membres de type</span><span class="sxs-lookup"><span data-stu-id="a084c-108">Type members</span></span>](#type-members)

* [<span data-ttu-id="a084c-109">Caractéristiques des membres de type</span><span class="sxs-lookup"><span data-stu-id="a084c-109">Characteristics of type members</span></span>](#characteristics-of-type-members)


## <a name="types-in-net"></a><span data-ttu-id="a084c-110">Types dans .NET</span><span class="sxs-lookup"><span data-stu-id="a084c-110">Types in .NET</span></span>

<span data-ttu-id="a084c-111">Tous les types dans .NET sont soit des types valeur, soit des types référence.</span><span class="sxs-lookup"><span data-stu-id="a084c-111">All types in .NET are either value types or reference types.</span></span> 

<span data-ttu-id="a084c-112">Les types valeur sont des types de données dont les objets sont représentés par la valeur réelle de l'objet.</span><span class="sxs-lookup"><span data-stu-id="a084c-112">Value types are data types whose objects are represented by the object's actual value.</span></span> <span data-ttu-id="a084c-113">Si une instance d'un type valeur est assignée à une variable, cette variable reçoit une copie actualisée de la valeur.</span><span class="sxs-lookup"><span data-stu-id="a084c-113">If an instance of a value type is assigned to a variable, that variable is given a fresh copy of the value.</span></span>

<span data-ttu-id="a084c-114">Les types référence sont des types de données dont les objets sont représentés par une référence (identique à un pointeur) à la valeur réelle de l'objet.</span><span class="sxs-lookup"><span data-stu-id="a084c-114">Reference types are data types whose objects are represented by a reference (similar to a pointer) to the object's actual value.</span></span> <span data-ttu-id="a084c-115">Si un type référence est assigné à une variable, celle-ci référence (ou pointe vers) la valeur d'origine.</span><span class="sxs-lookup"><span data-stu-id="a084c-115">If a reference type is assigned to a variable, that variable references (points to) the original value.</span></span> <span data-ttu-id="a084c-116">Aucune copie n'est effectuée.</span><span class="sxs-lookup"><span data-stu-id="a084c-116">No copy is made.</span></span> 

<span data-ttu-id="a084c-117">Le système de type commun (CTS, Common Type System) dans .NET prend en charge les cinq catégories de types suivantes :</span><span class="sxs-lookup"><span data-stu-id="a084c-117">The common type system in .NET supports the following five categories of types:</span></span>

* [<span data-ttu-id="a084c-118">Classes</span><span class="sxs-lookup"><span data-stu-id="a084c-118">Classes</span></span>](#classes)

* [<span data-ttu-id="a084c-119">Structures</span><span class="sxs-lookup"><span data-stu-id="a084c-119">Structures</span></span>](#structures)

* [<span data-ttu-id="a084c-120">Énumérations</span><span class="sxs-lookup"><span data-stu-id="a084c-120">Enumerations</span></span>](#enumerations)

* [<span data-ttu-id="a084c-121">Interfaces</span><span class="sxs-lookup"><span data-stu-id="a084c-121">Interfaces</span></span>](#interfaces)

* [<span data-ttu-id="a084c-122">Délégués</span><span class="sxs-lookup"><span data-stu-id="a084c-122">Delegates</span></span>](#delegates)

### <a name="classes"></a><span data-ttu-id="a084c-123">Classes</span><span class="sxs-lookup"><span data-stu-id="a084c-123">Classes</span></span>

<span data-ttu-id="a084c-124">Une classe est un type référence qui peut être dérivé directement d’une autre classe et qui est implicitement dérivé de [System.Object](xref:System.Object).</span><span class="sxs-lookup"><span data-stu-id="a084c-124">A class is a reference type that can be derived directly from another class and that is derived implicitly from [System.Object](xref:System.Object).</span></span> <span data-ttu-id="a084c-125">Une classe définit les opérations qu'un objet (qui est une instance de la classe) peut effectuer (méthodes, événements ou propriétés) et les données que l'objet contient (champs).</span><span class="sxs-lookup"><span data-stu-id="a084c-125">The class defines the operations that an object (which is an instance of the class) can perform (methods, events, or properties) and the data that the object contains (fields).</span></span> <span data-ttu-id="a084c-126">Bien qu'une classe inclue généralement la définition et l'implémentation (contrairement aux interfaces, par exemple, qui contiennent uniquement la définition sans l'implémentation), elle peut comporter un ou plusieurs membres dépourvus d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="a084c-126">Although a class generally includes both definition and implementation (unlike interfaces, for example, which contain only definition without implementation), it can have one or more members that have no implementation.</span></span>

<span data-ttu-id="a084c-127">Le tableau suivant décrit certaines des caractéristiques qu'une classe peut avoir.</span><span class="sxs-lookup"><span data-stu-id="a084c-127">The following table describes some of the characteristics that a class may have.</span></span> <span data-ttu-id="a084c-128">Chaque langage prenant en charge le runtime fournit un moyen d'indiquer qu'une classe ou qu'un membre d'une classe a une ou plusieurs de ces caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="a084c-128">Each language that supports the runtime provides a way to indicate that a class or class member has one or more of these characteristics.</span></span> <span data-ttu-id="a084c-129">Cependant, il se peut que des langages de programmation individuels qui ciblent .NET ne mettent pas toutes ces caractéristiques à disposition.</span><span class="sxs-lookup"><span data-stu-id="a084c-129">However, individual programming languages that target .NET may not make all these characteristics available.</span></span>

<span data-ttu-id="a084c-130">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="a084c-130">Characteristic</span></span> | <span data-ttu-id="a084c-131">Description</span><span class="sxs-lookup"><span data-stu-id="a084c-131">Description</span></span>
-------------- | -----------
<span data-ttu-id="a084c-132">sealed</span><span class="sxs-lookup"><span data-stu-id="a084c-132">sealed</span></span> | <span data-ttu-id="a084c-133">Spécifie qu'une autre classe ne peut pas être dérivée de ce type.</span><span class="sxs-lookup"><span data-stu-id="a084c-133">Specifies that another class cannot be derived from this type.</span></span>
<span data-ttu-id="a084c-134">implémente</span><span class="sxs-lookup"><span data-stu-id="a084c-134">implements</span></span> | <span data-ttu-id="a084c-135">Indique que la classe utilise une ou plusieurs interfaces en fournissant des implémentations des membres d'interface.</span><span class="sxs-lookup"><span data-stu-id="a084c-135">Indicates that the class uses one or more interfaces by providing implementations of interface members.</span></span>
<span data-ttu-id="a084c-136">abstract</span><span class="sxs-lookup"><span data-stu-id="a084c-136">abstract</span></span> | <span data-ttu-id="a084c-137">Indique que la classe ne peut pas être instanciée.</span><span class="sxs-lookup"><span data-stu-id="a084c-137">Indicates that the class cannot be instantiated.</span></span> <span data-ttu-id="a084c-138">Pour l'utiliser, vous devez dériver une autre classe de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="a084c-138">To use it, you must derive another class from it.</span></span>
<span data-ttu-id="a084c-139">hérite</span><span class="sxs-lookup"><span data-stu-id="a084c-139">inherits</span></span> | <span data-ttu-id="a084c-140">Indique que des instances de la classe peuvent être utilisées partout où la classe de base est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a084c-140">Indicates that instances of the class can be used anywhere the base class is specified.</span></span> <span data-ttu-id="a084c-141">Une classe dérivée qui hérite d'une classe de base peut utiliser l'implémentation de n'importe quel membre public fourni par la classe de base, ou la classe dérivée peut remplacer l'implémentation des membres publics par sa propre implémentation.</span><span class="sxs-lookup"><span data-stu-id="a084c-141">A derived class that inherits from a base class can use the implementation of any public members provided by the base class, or the derived class can override the implementation of the public members with its own implementation.</span></span>
<span data-ttu-id="a084c-142">exported ou not exported</span><span class="sxs-lookup"><span data-stu-id="a084c-142">exported or not exported</span></span> | <span data-ttu-id="a084c-143">Indique si une classe est visible à l'extérieur de l'assembly dans lequel elle est définie.</span><span class="sxs-lookup"><span data-stu-id="a084c-143">Indicates whether a class is visible outside the assembly in which it is defined.</span></span> <span data-ttu-id="a084c-144">Cette caractéristique s'applique uniquement aux classes de niveau supérieur, et pas aux classes imbriquées.</span><span class="sxs-lookup"><span data-stu-id="a084c-144">This characteristic applies only to top-level classes and not to nested classes.</span></span>

> [!NOTE]
> <span data-ttu-id="a084c-145">Une classe peut également être imbriquée dans une structure ou une classe parente.</span><span class="sxs-lookup"><span data-stu-id="a084c-145">A class can also be nested in a parent class or structure.</span></span> <span data-ttu-id="a084c-146">Les classes imbriquées ont également des caractéristiques de membre.</span><span class="sxs-lookup"><span data-stu-id="a084c-146">Nested classes also have member characteristics.</span></span> <span data-ttu-id="a084c-147">Pour plus d’informations, consultez [Types imbriqués](#nested-types).</span><span class="sxs-lookup"><span data-stu-id="a084c-147">For more information, see [Nested types](#nested-types).</span></span>

<span data-ttu-id="a084c-148">Les membres de classe sans implémentation sont des membres abstraits.</span><span class="sxs-lookup"><span data-stu-id="a084c-148">Class members that have no implementation are abstract members.</span></span> <span data-ttu-id="a084c-149">Une classe qui possède un ou plusieurs membres abstraits est elle-même abstraite ; il n'est pas possible d'en créer de nouvelles instances.</span><span class="sxs-lookup"><span data-stu-id="a084c-149">A class that has one or more abstract members is itself abstract; new instances of it cannot be created.</span></span> <span data-ttu-id="a084c-150">Certains langages qui ciblent le runtime vous permettent de marquer une classe comme abstraite même si aucun de ses membres n'est abstrait.</span><span class="sxs-lookup"><span data-stu-id="a084c-150">Some languages that target the runtime let you mark a class as abstract even if none of its members are abstract.</span></span> <span data-ttu-id="a084c-151">Vous pouvez utiliser une classe abstraite lorsque vous voulez encapsuler un ensemble de fonctionnalités de base dont des classes dérivées peuvent hériter ou qu'elles peuvent substituer lorsque cela est approprié.</span><span class="sxs-lookup"><span data-stu-id="a084c-151">You can use an abstract class when you want to encapsulate a basic set of functionality that derived classes can inherit or override when appropriate.</span></span> <span data-ttu-id="a084c-152">Les classes qui ne sont pas abstraites sont qualifiées de classes concrètes.</span><span class="sxs-lookup"><span data-stu-id="a084c-152">Classes that are not abstract are referred to as concrete classes.</span></span>

<span data-ttu-id="a084c-153">Une classe peut implémenter n’importe quel nombre d’interfaces, mais elle ne peut hériter que d’une seule classe de base en plus de la classe [System.Object](xref:System.Object), de laquelle toutes les classes héritent implicitement.</span><span class="sxs-lookup"><span data-stu-id="a084c-153">A class can implement any number of interfaces, but it can inherit from only one base class in addition to [System.Object](xref:System.Object), from which all classes inherit implicitly.</span></span> <span data-ttu-id="a084c-154">Toutes les classes doivent avoir au moins un constructeur qui initialise de nouvelles instances de la classe.</span><span class="sxs-lookup"><span data-stu-id="a084c-154">All classes must have at least one constructor, which initializes new instances of the class.</span></span> <span data-ttu-id="a084c-155">Si vous ne définissez pas explicitement un constructeur, la plupart des compilateurs fourniront automatiquement un constructeur par défaut (sans paramètre).</span><span class="sxs-lookup"><span data-stu-id="a084c-155">If you do not explicitly define a constructor, most compilers will automatically provide a default (parameterless) constructor.</span></span>

### <a name="structures"></a><span data-ttu-id="a084c-156">Structures</span><span class="sxs-lookup"><span data-stu-id="a084c-156">Structures</span></span>

<span data-ttu-id="a084c-157">Une structure est un type valeur qui dérive implicitement de [System.ValueType](xref:System.ValueType) qui, à son tour, est dérivé de [System.Object](xref:System.Object).</span><span class="sxs-lookup"><span data-stu-id="a084c-157">A structure is a value type that derives implicitly from [System.ValueType](xref:System.ValueType), which in turn is derived from [System.Object](xref:System.Object).</span></span> <span data-ttu-id="a084c-158">Une structure est très utile pour représenter des valeurs dont les besoins en ressources mémoire sont faibles, ainsi que pour passer des valeurs en tant que paramètres par valeur à des méthodes qui ont des paramètres fortement typés.</span><span class="sxs-lookup"><span data-stu-id="a084c-158">A structure is very useful for representing values whose memory requirements are small, and for passing values as by-value parameters to methods that have strongly typed parameters.</span></span> <span data-ttu-id="a084c-159">Dans .NET, tous les types de données primitifs ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32) et [UInt64](xref:System.UInt64)) sont définis comme structures.</span><span class="sxs-lookup"><span data-stu-id="a084c-159">In .NET, all primitive data types ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), and [UInt64](xref:System.UInt64)) are defined as structures.</span></span>

<span data-ttu-id="a084c-160">Comme les classes, les structures définissent à la fois les données (les champs de la structure) et les opérations qui peuvent être exécutées sur ces données (les méthodes de la structure).</span><span class="sxs-lookup"><span data-stu-id="a084c-160">Like classes, structures define both data (the fields of the structure) and the operations that can be performed on that data (the methods of the structure).</span></span> <span data-ttu-id="a084c-161">Cela signifie que vous pouvez appeler des méthodes sur des structures, notamment les méthodes virtuelles définies sur les classes [System.Object](xref:System.Object) et [System.ValueType](xref:System.ValueType), ainsi que toute méthode définie sur le type valeur lui-même.</span><span class="sxs-lookup"><span data-stu-id="a084c-161">This means that you can call methods on structures, including the virtual methods defined on the [System.Object](xref:System.Object) and [System.ValueType](xref:System.ValueType) classes, and any methods defined on the value type itself.</span></span> <span data-ttu-id="a084c-162">En d'autres termes, les structures peuvent comporter des champs, des propriétés et des événements, ainsi que des méthodes statiques et non statiques.</span><span class="sxs-lookup"><span data-stu-id="a084c-162">In other words, structures can have fields, properties, and events, as well as static and nonstatic methods.</span></span> <span data-ttu-id="a084c-163">Vous pouvez créer des instances de structures, les passer en tant que paramètres, les stocker en tant que variables locales ou les stocker dans un champ d'un autre type valeur ou type référence.</span><span class="sxs-lookup"><span data-stu-id="a084c-163">You can create instances of structures, pass them as parameters, store them as local variables, or store them in a field of another value type or reference type.</span></span> <span data-ttu-id="a084c-164">Les structures peuvent aussi implémenter des interfaces.</span><span class="sxs-lookup"><span data-stu-id="a084c-164">Structures can also implement interfaces.</span></span>

<span data-ttu-id="a084c-165">Les types valeur diffèrent également des classes par plusieurs aspects.</span><span class="sxs-lookup"><span data-stu-id="a084c-165">Value types also differ from classes in several respects.</span></span> <span data-ttu-id="a084c-166">Tout d’abord, bien qu’ils héritent implicitement de [System.ValueType](xref:System.ValueType), ils ne peuvent pas hériter directement de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="a084c-166">First, although they implicitly inherit from [System.ValueType](xref:System.ValueType), they cannot directly inherit from any type.</span></span> <span data-ttu-id="a084c-167">De même, tous les types valeur sont sealed, ce qui signifie qu'aucun autre type ne peut en être dérivé.</span><span class="sxs-lookup"><span data-stu-id="a084c-167">Similarly, all value types are sealed, which means that no other type can be derived from them.</span></span> <span data-ttu-id="a084c-168">De plus, ils ne nécessitent pas de constructeurs.</span><span class="sxs-lookup"><span data-stu-id="a084c-168">They also do not require constructors.</span></span>

<span data-ttu-id="a084c-169">Pour chaque type valeur, le Common Language Runtime fournit un type boxed correspondant qui est une classe ayant le même état et le même comportement que le type valeur.</span><span class="sxs-lookup"><span data-stu-id="a084c-169">For each value type, the common language runtime supplies a corresponding boxed type, which is a class that has the same state and behavior as the value type.</span></span> <span data-ttu-id="a084c-170">Une instance d’un type valeur est boxed lorsqu’elle est passée à une méthode qui accepte un paramètre de type [System.Object](xref:System.Object).</span><span class="sxs-lookup"><span data-stu-id="a084c-170">An instance of a value type is boxed when it is passed to a method that accepts a parameter of type [System.Object](xref:System.Object).</span></span> <span data-ttu-id="a084c-171">Elle est unboxed (c'est-à-dire reconvertie d'une instance d'une classe en instance d'un type valeur) lorsque le contrôle retourne d'un appel de méthode qui accepte un type valeur comme paramètre par référence.</span><span class="sxs-lookup"><span data-stu-id="a084c-171">It is unboxed (that is, converted from an instance of a class back to an instance of a value type) when control returns from a method call that accepts a value type as a by-reference parameter.</span></span> <span data-ttu-id="a084c-172">Certains langages imposent l'utilisation d'une syntaxe spéciale lorsque le type boxed est requis ; d'autres utilisent automatiquement le type boxed lorsqu'il est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a084c-172">Some languages require that you use special syntax when the boxed type is required; others automatically use the boxed type when it is needed.</span></span> <span data-ttu-id="a084c-173">Lorsque vous définissez un type valeur, vous définissez le type boxed et le type unboxed.</span><span class="sxs-lookup"><span data-stu-id="a084c-173">When you define a value type, you are defining both the boxed and the unboxed type.</span></span>

### <a name="enumerations"></a><span data-ttu-id="a084c-174">Énumérations</span><span class="sxs-lookup"><span data-stu-id="a084c-174">Enumerations</span></span>

<span data-ttu-id="a084c-175">Une énumération (enum) est un type valeur qui hérite directement de [System.Enum](xref:System.Enum) et qui fournit des noms de remplacement pour les valeurs d’un type primitif sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="a084c-175">An enumeration (enum) is a value type that inherits directly from [System.Enum](xref:System.Enum) and that supplies alternate names for the values of an underlying primitive type.</span></span> <span data-ttu-id="a084c-176">Un type énumération a un nom, un type sous-jacent qui doit être l’un des types d’entiers signés ou non signés intégrés (tels que [Byte](xref:System.Byte), [Int32](xref:System.Int32) ou [UInt64](xref:System.UInt64)) et un ensemble de champs.</span><span class="sxs-lookup"><span data-stu-id="a084c-176">An enumeration type has a name, an underlying type that must be one of the built-in signed or unsigned integer types (such as [Byte](xref:System.Byte), [Int32](xref:System.Int32), or [UInt64](xref:System.UInt64)), and a set of fields.</span></span> <span data-ttu-id="a084c-177">Les champs sont des champs statiques de type Literal, chacun représentant une constante.</span><span class="sxs-lookup"><span data-stu-id="a084c-177">The fields are static literal fields, each of which represents a constant.</span></span> <span data-ttu-id="a084c-178">La même valeur peut être assignée à plusieurs champs.</span><span class="sxs-lookup"><span data-stu-id="a084c-178">The same value can be assigned to multiple fields.</span></span> <span data-ttu-id="a084c-179">Dans ce cas, vous devez marquer l'une des valeurs comme valeur d'énumération primaire pour la réflexion et la conversion de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a084c-179">When this occurs, you must mark one of the values as the primary enumeration value for reflection and string conversion.</span></span>

<span data-ttu-id="a084c-180">Vous pouvez assigner une valeur du type sous-jacent à une énumération et vice-versa (aucun cast n'est requis par le runtime).</span><span class="sxs-lookup"><span data-stu-id="a084c-180">You can assign a value of the underlying type to an enumeration and vice versa (no cast is required by the runtime).</span></span> <span data-ttu-id="a084c-181">Vous pouvez créer une instance d’une énumération et appeler les méthodes de [System.Enum](xref:System.Enum), ainsi que toute méthode définie sur le type sous-jacent de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="a084c-181">You can create an instance of an enumeration and call the methods of [System.Enum](xref:System.Enum), as well as any methods defined on the enumeration's underlying type.</span></span> <span data-ttu-id="a084c-182">Cependant, il est possible que certains langages ne vous permettent pas de passer une énumération en tant que paramètre lorsqu'une instance du type sous-jacent est requise (ou vice versa).</span><span class="sxs-lookup"><span data-stu-id="a084c-182">However, some languages might not let you pass an enumeration as a parameter when an instance of the underlying type is required (or vice versa).</span></span>

<span data-ttu-id="a084c-183">Les restrictions supplémentaires suivantes s'appliquent aux énumérations :</span><span class="sxs-lookup"><span data-stu-id="a084c-183">The following additional restrictions apply to enumerations:</span></span> 

* <span data-ttu-id="a084c-184">Elles ne peuvent pas définir leurs propres méthodes.</span><span class="sxs-lookup"><span data-stu-id="a084c-184">They cannot define their own methods.</span></span>

* <span data-ttu-id="a084c-185">Elles ne peuvent pas implémenter d'interfaces.</span><span class="sxs-lookup"><span data-stu-id="a084c-185">They cannot implement interfaces.</span></span>

* <span data-ttu-id="a084c-186">Elles ne peuvent pas définir des propriétés ou des événements.</span><span class="sxs-lookup"><span data-stu-id="a084c-186">They cannot define properties or events.</span></span>

* <span data-ttu-id="a084c-187">Elles ne peuvent pas être génériques, à moins qu'elles le soient uniquement parce qu'elles sont imbriquées dans un type générique.</span><span class="sxs-lookup"><span data-stu-id="a084c-187">They cannot be generic, unless they are generic only because they are nested within a generic type.</span></span> <span data-ttu-id="a084c-188">Par conséquent, une énumération ne peut pas avoir de paramètres de type propres.</span><span class="sxs-lookup"><span data-stu-id="a084c-188">That is, an enumeration cannot have type parameters of its own.</span></span> 

> [!NOTE]
> <span data-ttu-id="a084c-189">Les types imbriqués (y compris les énumérations) créés avec C# incluent les paramètres de type de tous les types génériques englobants, et sont donc génériques, même s’ils n’ont pas de paramètres de type propres.</span><span class="sxs-lookup"><span data-stu-id="a084c-189">Nested types (including enumerations) created with C# include the type parameters of all enclosing generic types, and are therefore generic even if they do not have type parameters of their own.</span></span> <span data-ttu-id="a084c-190">Pour plus d’informations, consultez la rubrique de référence [Type.MakeGenericType](xref:System.Type.MakeGenericType(System.Type[])).</span><span class="sxs-lookup"><span data-stu-id="a084c-190">For more information, see the [Type.MakeGenericType](xref:System.Type.MakeGenericType(System.Type[])) reference topic.</span></span> 

<span data-ttu-id="a084c-191">L’attribut [FlagsAttribute](xref:System.FlagsAttribute) désigne un genre particulier d’énumération appelé « champ de bits ».</span><span class="sxs-lookup"><span data-stu-id="a084c-191">The [FlagsAttribute](xref:System.FlagsAttribute) attribute denotes a special kind of enumeration called a bit field.</span></span> <span data-ttu-id="a084c-192">Le runtime lui-même ne fait pas de distinction entre les énumérations traditionnelles et les champs de bits, mais votre langage pourrait le faire.</span><span class="sxs-lookup"><span data-stu-id="a084c-192">The runtime itself does not distinguish between traditional enumerations and bit fields, but your language might do so.</span></span> <span data-ttu-id="a084c-193">Lorsque cette distinction est effectuée, les opérateurs binaires peuvent être utilisés sur les champs de bits, mais pas sur les énumérations, pour générer des valeurs sans nom.</span><span class="sxs-lookup"><span data-stu-id="a084c-193">When this distinction is made, bitwise operators can be used on bit fields, but not on enumerations, to generate unnamed values.</span></span> <span data-ttu-id="a084c-194">Les énumérations sont généralement utilisées pour des listes d'éléments uniques, tels que les jours de la semaine, des noms de pays ou de région, etc.</span><span class="sxs-lookup"><span data-stu-id="a084c-194">Enumerations are generally used for lists of unique elements, such as days of the week, country or region names, and so on.</span></span> <span data-ttu-id="a084c-195">Les champs de bits sont généralement utilisés pour des listes de qualités ou de quantités pouvant être utilisées en combinaison, telle que `Red And Big And Fast`.</span><span class="sxs-lookup"><span data-stu-id="a084c-195">Bit fields are generally used for lists of qualities or quantities that might occur in combination, such as `Red And Big And Fast`.</span></span>

<span data-ttu-id="a084c-196">L'exemple suivant montre comment utiliser les champs de bits et les énumérations traditionnelles.</span><span class="sxs-lookup"><span data-stu-id="a084c-196">The following example shows how to use both bit fields and traditional enumerations.</span></span>

```csharp
using System;
using System.Collections.Generic;

// A traditional enumeration of some root vegetables.
public enum SomeRootVegetables
{
    HorseRadish,
    Radish,
    Turnip
}

// A bit field or flag enumeration of harvesting seasons.
[Flags]
public enum Seasons
{
    None = 0,
    Summer = 1,
    Autumn = 2,
    Winter = 4,
    Spring = 8,
    All = Summer | Autumn | Winter | Spring
}

public class Example
{
   public static void Main()
   {
       // Hash table of when vegetables are available.
       Dictionary<SomeRootVegetables, Seasons> AvailableIn = new Dictionary<SomeRootVegetables, Seasons>();

       AvailableIn[SomeRootVegetables.HorseRadish] = Seasons.All;
       AvailableIn[SomeRootVegetables.Radish] = Seasons.Spring;
       AvailableIn[SomeRootVegetables.Turnip] = Seasons.Spring | 
            Seasons.Autumn;

       // Array of the seasons, using the enumeration.
       Seasons[] theSeasons = new Seasons[] { Seasons.Summer, Seasons.Autumn, 
            Seasons.Winter, Seasons.Spring };

       // Print information of what vegetables are available each season.
       foreach (Seasons season in theSeasons)
       {
          Console.Write(String.Format(
              "The following root vegetables are harvested in {0}:\n", 
              season.ToString("G")));
          foreach (KeyValuePair<SomeRootVegetables, Seasons> item in AvailableIn)
          {
             // A bitwise comparison.
             if (((Seasons)item.Value & season) > 0)
                 Console.Write(String.Format("  {0:G}\n", 
                      (SomeRootVegetables)item.Key));
          }
       }
   }
}
// The example displays the following output:
//    The following root vegetables are harvested in Summer:
//      HorseRadish
//    The following root vegetables are harvested in Autumn:
//      Turnip
//      HorseRadish
//    The following root vegetables are harvested in Winter:
//      HorseRadish
//    The following root vegetables are harvested in Spring:
//      Turnip
//      Radish
//      HorseRadish
```

```vb
Imports System.Collections.Generic

' A traditional enumeration of some root vegetables.
Public Enum SomeRootVegetables
   HorseRadish
   Radish
   Turnip
End Enum 

' A bit field or flag enumeration of harvesting seasons.
<Flags()> Public Enum Seasons
   None = 0
   Summer = 1
   Autumn = 2
   Winter = 4
   Spring = 8
   All = Summer Or Autumn Or Winter Or Spring
End Enum 

' Entry point.
Public Class Example
   Public Shared Sub Main()
      ' Hash table of when vegetables are available.
      Dim AvailableIn As New Dictionary(Of SomeRootVegetables, Seasons)()

      AvailableIn(SomeRootVegetables.HorseRadish) = Seasons.All
      AvailableIn(SomeRootVegetables.Radish) = Seasons.Spring
      AvailableIn(SomeRootVegetables.Turnip) = Seasons.Spring Or _
                                               Seasons.Autumn

      ' Array of the seasons, using the enumeration.
      Dim theSeasons() As Seasons = {Seasons.Summer, Seasons.Autumn, _
                                     Seasons.Winter, Seasons.Spring}

      ' Print information of what vegetables are available each season.
      For Each season As Seasons In theSeasons
         Console.WriteLine(String.Format( _
              "The following root vegetables are harvested in {0}:", _
              season.ToString("G")))
         For Each item As KeyValuePair(Of SomeRootVegetables, Seasons) In AvailableIn
            ' A bitwise comparison.
            If(CType(item.Value, Seasons) And season) > 0 Then
               Console.WriteLine("  " + _
                     CType(item.Key, SomeRootVegetables).ToString("G"))
            End If
         Next
      Next
   End Sub 
End Class 
' The example displays the following output:
'    The following root vegetables are harvested in Summer:
'      HorseRadish
'    The following root vegetables are harvested in Autumn:
'      Turnip
'      HorseRadish
'    The following root vegetables are harvested in Winter:
'      HorseRadish
'    The following root vegetables are harvested in Spring:
'      Turnip
'      Radish
'      HorseRadish
```

### <a name="interfaces"></a><span data-ttu-id="a084c-197">Interfaces</span><span class="sxs-lookup"><span data-stu-id="a084c-197">Interfaces</span></span>

<span data-ttu-id="a084c-198">Une interface définit un contrat qui spécifie une relation « peut faire » ou « a un ».</span><span class="sxs-lookup"><span data-stu-id="a084c-198">An interface defines a contract that specifies a "can do" relationship or a "has a" relationship.</span></span> <span data-ttu-id="a084c-199">Les interfaces sont souvent utilisées pour implémenter des fonctionnalités, comme la comparaison et le tri (interfaces [IComparable](xref:System.IComparable) et [IComparable&lt;T&gt;](xref:System.IComparable%601)), le test de l’égalité (interface [IEquatable&lt;T&gt;](xref:System.IEquatable%601)) ou l’énumération d’éléments dans une collection (interfaces [IEnumerable](xref:System.Collections.IEnumerable) et [IEnumerable&lt;T&gt;](xref:System.Collections.Generic.IEnumerable%601)).</span><span class="sxs-lookup"><span data-stu-id="a084c-199">Interfaces are often used to implement functionality, such as comparing and sorting (the [IComparable](xref:System.IComparable) and [IComparable&lt;T&gt;](xref:System.IComparable%601) interfaces), testing for equality (the [IEquatable&lt;T&gt;](xref:System.IEquatable%601) interface), or enumerating items in a collection (the [IEnumerable](xref:System.Collections.IEnumerable) and [IEnumerable&lt;T&gt;](xref:System.Collections.Generic.IEnumerable%601) interfaces).</span></span> <span data-ttu-id="a084c-200">Les interfaces peuvent avoir des propriétés, des méthodes et des événements qui sont tous des membres abstraits, c'est-à-dire que bien que l'interface définisse les membres et leurs signatures, elle laisse le type qui implémente l'interface définir la fonctionnalité de chaque membre d'interface.</span><span class="sxs-lookup"><span data-stu-id="a084c-200">Interfaces can have properties, methods, and events, all of which are abstract members; that is, although the interface defines the members and their signatures, it leaves it to the type that implements the interface to define the functionality of each interface member.</span></span> <span data-ttu-id="a084c-201">En d'autres termes, toute classe ou structure qui implémente une interface doit fournir des définitions pour les membres abstraits déclarés dans l'interface.</span><span class="sxs-lookup"><span data-stu-id="a084c-201">This means that any class or structure that implements an interface must supply definitions for the abstract members declared in the interface.</span></span> <span data-ttu-id="a084c-202">Une interface peut imposer à une classe ou à une structure d'implémentation d'implémenter une ou plusieurs autres interfaces.</span><span class="sxs-lookup"><span data-stu-id="a084c-202">An interface can require any implementing class or structure to also implement one or more other interfaces.</span></span>

<span data-ttu-id="a084c-203">Les restrictions suivantes s'appliquent aux interfaces :</span><span class="sxs-lookup"><span data-stu-id="a084c-203">The following restrictions apply to interfaces:</span></span> 

* <span data-ttu-id="a084c-204">Une interface peut être déclarée avec n'importe quelle accessibilité, mais les membres d'interface doivent tous avoir une accessibilité publique.</span><span class="sxs-lookup"><span data-stu-id="a084c-204">An interface can be declared with any accessibility, but interface members must all have public accessibility.</span></span>

* <span data-ttu-id="a084c-205">Les interfaces ne peuvent pas définir de constructeurs.</span><span class="sxs-lookup"><span data-stu-id="a084c-205">Interfaces cannot define constructors.</span></span>

* <span data-ttu-id="a084c-206">Les interfaces ne peuvent pas définir de champs.</span><span class="sxs-lookup"><span data-stu-id="a084c-206">Interfaces cannot define fields.</span></span>

* <span data-ttu-id="a084c-207">Les interfaces peuvent définir uniquement des membres d'instance.</span><span class="sxs-lookup"><span data-stu-id="a084c-207">Interfaces can define only instance members.</span></span> <span data-ttu-id="a084c-208">Elles ne peuvent pas définir des membres statiques.</span><span class="sxs-lookup"><span data-stu-id="a084c-208">They cannot define static members.</span></span>

<span data-ttu-id="a084c-209">Chaque langage doit fournir des règles de mappage d'une implémentation à l'interface qui nécessite le membre, car plusieurs interfaces peuvent déclarer un membre avec la même signature, et ces membres peuvent avoir des implémentations séparées.</span><span class="sxs-lookup"><span data-stu-id="a084c-209">Each language must provide rules for mapping an implementation to the interface that requires the member, because more than one interface can declare a member with the same signature, and these members can have separate implementations.</span></span>

### <a name="delegates"></a><span data-ttu-id="a084c-210">Délégués</span><span class="sxs-lookup"><span data-stu-id="a084c-210">Delegates</span></span>

<span data-ttu-id="a084c-211">Les délégués sont des types référence qui jouent un rôle similaire à celui des pointeurs fonction en C++.</span><span class="sxs-lookup"><span data-stu-id="a084c-211">Delegates are reference types that serve a purpose similar to that of function pointers in C++.</span></span> <span data-ttu-id="a084c-212">Ils sont utilisés pour les gestionnaires d’événements et les fonctions de rappel dans .NET.</span><span class="sxs-lookup"><span data-stu-id="a084c-212">They are used for event handlers and callback functions in .NET.</span></span> <span data-ttu-id="a084c-213">Contrairement aux pointeurs fonction, les délégués sont de type sécurisé, sûr et vérifiable.</span><span class="sxs-lookup"><span data-stu-id="a084c-213">Unlike function pointers, delegates are secure, verifiable, and type safe.</span></span> <span data-ttu-id="a084c-214">Un type délégué peut représenter n'importe quelle méthode d'instance ou méthode statique ayant une signature compatible.</span><span class="sxs-lookup"><span data-stu-id="a084c-214">A delegate type can represent any instance method or static method that has a compatible signature.</span></span> 

<span data-ttu-id="a084c-215">Le paramètre d'un délégué est compatible avec le paramètre correspondant d'une méthode si le type de paramètre du délégué est plus restrictif que le type de paramètre de la méthode. En effet, cela garantit qu'un argument transmis au délégué peut être transmis à la méthode en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="a084c-215">A parameter of a delegate is compatible with the corresponding parameter of a method if the type of the delegate parameter is more restrictive than the type of the method parameter, because this guarantees that an argument passed to the delegate can be passed safely to the method.</span></span>

<span data-ttu-id="a084c-216">De même, le type de retour d’un délégué est compatible avec le type de retour d’une méthode si le type de retour de la méthode est plus restrictif que le type de retour du délégué, car cela garantit que le cast de la valeur de retour de la méthode peut être effectué sans risque au type de retour du délégué.</span><span class="sxs-lookup"><span data-stu-id="a084c-216">Similarly, the return type of a delegate is compatible with the return type of a method if the return type of the method is more restrictive than the return type of the delegate, because this guarantees that the return value of the method can be cast safely to the return type of the delegate.</span></span>

<span data-ttu-id="a084c-217">Par exemple, un délégué ayant un paramètre de type [IEnumerable](xref:System.Collections.IEnumerable) et un type de retour [Object](xref:System.Object) peut représenter une méthode ayant un paramètre de type [Object](xref:System.Object) et une valeur de retour de type [IEnumerable](xref:System.Collections.IEnumerable).</span><span class="sxs-lookup"><span data-stu-id="a084c-217">For example, a delegate that has a parameter of type [IEnumerable](xref:System.Collections.IEnumerable) and a return type of [Object](xref:System.Object) can represent a method that has a parameter of type [Object](xref:System.Object) and a return value of type [IEnumerable](xref:System.Collections.IEnumerable).</span></span> 

 <span data-ttu-id="a084c-218">On dit qu'un délégué est lié à la méthode qu'il représente.</span><span class="sxs-lookup"><span data-stu-id="a084c-218">A delegate is said to be bound to the method it represents.</span></span> <span data-ttu-id="a084c-219">Outre cette liaison, un délégué peut être lié à un objet.</span><span class="sxs-lookup"><span data-stu-id="a084c-219">In addition to being bound to the method, a delegate can be bound to an object.</span></span> <span data-ttu-id="a084c-220">L'objet représente le premier paramètre de la méthode, et est passé à cette dernière chaque fois que le délégué est appelé.</span><span class="sxs-lookup"><span data-stu-id="a084c-220">The object represents the first parameter of the method, and is passed to the method every time the delegate is invoked.</span></span> <span data-ttu-id="a084c-221">Si la méthode est une méthode d'instance, l'objet dépendant est passé en tant que paramètre `this` implicite (`Me` en Visual Basic) ; si la méthode est statique, l'objet est passé en tant que premier paramètre formel de la méthode, et la signature du délégué doit correspondre aux paramètres restants.</span><span class="sxs-lookup"><span data-stu-id="a084c-221">If the method is an instance method, the bound object is passed as the implicit `this` parameter (`Me` in Visual Basic); if the method is static, the object is passed as the first formal parameter of the method, and the delegate signature must match the remaining parameters.</span></span> 
 
 <span data-ttu-id="a084c-222">Tous les délégués héritent de [System.MulticastDelegate](xref:System.MulticastDelegate), qui hérite de [System.Delegate](xref:System.Delegate).</span><span class="sxs-lookup"><span data-stu-id="a084c-222">All delegates inherit from [System.MulticastDelegate](xref:System.MulticastDelegate), which inherits from [System.Delegate](xref:System.Delegate).</span></span> <span data-ttu-id="a084c-223">Les langages C# et Visual Basic n’autorisent pas l’héritage à partir de ces types.</span><span class="sxs-lookup"><span data-stu-id="a084c-223">The C# and Visual Basic languages don't allow inheritance from these types.</span></span> <span data-ttu-id="a084c-224">Ils fournissent à la place des mots clés pour la déclaration des délégués.</span><span class="sxs-lookup"><span data-stu-id="a084c-224">Instead, they provide keywords for declaring delegates.</span></span>
 
 <span data-ttu-id="a084c-225">Étant donné que les délégués héritent de [MulticastDelegate](xref:System.MulticastDelegate), un délégué dispose d’une liste d’appel, qui est la liste des méthodes représentées par le délégué et exécutées lorsque celui-ci est appelé.</span><span class="sxs-lookup"><span data-stu-id="a084c-225">Because delegates inherit from [MulticastDelegate](xref:System.MulticastDelegate), a delegate has an invocation list, which is a list of methods that the delegate represents and that are executed when the delegate is invoked.</span></span> <span data-ttu-id="a084c-226">Toutes les méthodes de la liste reçoivent les arguments fournis lorsque le délégué est appelé.</span><span class="sxs-lookup"><span data-stu-id="a084c-226">All methods in the list receive the arguments supplied when the delegate is invoked.</span></span>

> [!NOTE]
> <span data-ttu-id="a084c-227">La valeur de retour n'est pas définie pour un délégué dont la liste d'appel comprend plusieurs méthodes, même si le délégué dispose d'un type de retour.</span><span class="sxs-lookup"><span data-stu-id="a084c-227">The return value is not defined for a delegate that has more than one method in its invocation list, even if the delegate has a return type.</span></span>

<span data-ttu-id="a084c-228">Dans la plupart des cas, comme avec les méthodes de rappel, un délégué représente une seule méthode, et les mesures que vous devez prendre se limitent à la création et l'appel du délégué.</span><span class="sxs-lookup"><span data-stu-id="a084c-228">In many cases, such as with callback methods, a delegate represents only one method, and the only actions you have to take are creating the delegate and invoking it.</span></span> 

<span data-ttu-id="a084c-229">Pour les délégués qui représentent plusieurs méthodes, .NET fournit les méthodes des classes de délégué [Delegate](xref:System.Delegate) et [MulticastDelegate](xref:System.MulticastDelegate) pour prendre en charge les opérations telles que l’ajout d’une méthode à la liste d’appel d’un délégué (méthode [Delegate.Combine](xref:System.Delegate.Combine(System.Delegate,System.Delegate))), la suppression d’une méthode (méthode [Delegate.Remove](xref:System.Delegate.Remove(System.Delegate,System.Delegate))) et l’obtention de la liste d’appel (méthode [Delegate.GetInvocationList](xref:System.Delegate.GetInvocationList)).</span><span class="sxs-lookup"><span data-stu-id="a084c-229">For delegates that represent multiple methods, .NET provides methods of the [Delegate](xref:System.Delegate) and [MulticastDelegate](xref:System.MulticastDelegate) delegate classes to support operations such as adding a method to a delegate's invocation list (the [Delegate.Combine](xref:System.Delegate.Combine(System.Delegate,System.Delegate)) method), removing a method (the [Delegate.Remove](xref:System.Delegate.Remove(System.Delegate,System.Delegate)) method), and getting the invocation list (the [Delegate.GetInvocationList](xref:System.Delegate.GetInvocationList) method).</span></span>

> [!NOTE]
> <span data-ttu-id="a084c-230">Il n’est pas nécessaire d’utiliser ces méthodes pour les délégués de gestionnaires d’événements en C# ou Visual Basic, car ces langages fournissent une syntaxe pour l’ajout et la suppression des gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="a084c-230">It is not necessary to use these methods for event-handler delegates in C# or Visual Basic, because these languages provide syntax for adding and removing event handlers.</span></span>

## <a name="type-definitions"></a><span data-ttu-id="a084c-231">Définitions de type</span><span class="sxs-lookup"><span data-stu-id="a084c-231">Type definitions</span></span>

<span data-ttu-id="a084c-232">Une définition de type inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a084c-232">A type definition includes the following:</span></span> 

* <span data-ttu-id="a084c-233">les attributs définis sur le type ;</span><span class="sxs-lookup"><span data-stu-id="a084c-233">Any attributes defined on the type.</span></span>

* <span data-ttu-id="a084c-234">L'accessibilité du type (visibilité).</span><span class="sxs-lookup"><span data-stu-id="a084c-234">The type's accessibility (visibility).</span></span>

* <span data-ttu-id="a084c-235">le nom du type ;</span><span class="sxs-lookup"><span data-stu-id="a084c-235">The type's name.</span></span>

* <span data-ttu-id="a084c-236">le type de base du type ;</span><span class="sxs-lookup"><span data-stu-id="a084c-236">The type's base type.</span></span>

* <span data-ttu-id="a084c-237">les interfaces implémentées par le type ;</span><span class="sxs-lookup"><span data-stu-id="a084c-237">Any interfaces implemented by the type.</span></span>

* <span data-ttu-id="a084c-238">les définitions de chacun des membres du type.</span><span class="sxs-lookup"><span data-stu-id="a084c-238">Definitions for each of the type's members.</span></span>

### <a name="attributes"></a><span data-ttu-id="a084c-239">Attributs</span><span class="sxs-lookup"><span data-stu-id="a084c-239">Attributes</span></span>

<span data-ttu-id="a084c-240">Les attributs fournissent des métadonnées définies par l'utilisateur supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="a084c-240">Attributes provide additional user-defined metadata.</span></span> <span data-ttu-id="a084c-241">La plupart du temps, ils sont utilisés pour stocker les informations supplémentaires relatives à un type de l’assembly, ou pour modifier le comportement d’un membre de type dans l’environnement au moment du design ou dans l’environnement d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a084c-241">Most commonly, they are used to store additional information about a type in its assembly, or to modify the behavior of a type member in either the design-time or run-time environment.</span></span> 

<span data-ttu-id="a084c-242">Les attributs sont eux-mêmes des classes qui héritent de [System.Attribute](xref:System.Attribute).</span><span class="sxs-lookup"><span data-stu-id="a084c-242">Attributes are themselves classes that inherit from [System.Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="a084c-243">Les langages qui prennent en charge l'utilisation d'attributs ont chacun leur propre syntaxe pour l'application d'attributs à un élément du langage.</span><span class="sxs-lookup"><span data-stu-id="a084c-243">Languages that support the use of attributes each have their own syntax for applying attributes to a language element.</span></span> <span data-ttu-id="a084c-244">Les attributs peuvent être appliqués à presque n’importe quel élément de langage ; les éléments spécifiques auxquels un attribut peut être appliqué sont définis par l’attribut [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) qui est appliqué à cette classe d’attributs.</span><span class="sxs-lookup"><span data-stu-id="a084c-244">Attributes can be applied to almost any language element; the specific elements to which an attribute can be applied are defined by the [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) that is applied to that attribute class.</span></span>

### <a name="type-accessibility"></a><span data-ttu-id="a084c-245">Accessibilité des types</span><span class="sxs-lookup"><span data-stu-id="a084c-245">Type accessibility</span></span>

<span data-ttu-id="a084c-246">Tous les types ont un modificateur qui régit leur accessibilité à partir d'autres types.</span><span class="sxs-lookup"><span data-stu-id="a084c-246">All types have a modifier that governs their accessibility from other types.</span></span> <span data-ttu-id="a084c-247">Le tableau suivant décrit les accessibilités de type prises en charge par le runtime.</span><span class="sxs-lookup"><span data-stu-id="a084c-247">The following table describes the type accessibilities supported by the runtime.</span></span>

<span data-ttu-id="a084c-248">Accessibilité</span><span class="sxs-lookup"><span data-stu-id="a084c-248">Accessibility</span></span> | <span data-ttu-id="a084c-249">Description</span><span class="sxs-lookup"><span data-stu-id="a084c-249">Description</span></span>
------------- | -----------
<span data-ttu-id="a084c-250">public</span><span class="sxs-lookup"><span data-stu-id="a084c-250">public</span></span> | <span data-ttu-id="a084c-251">Le type est accessible par tous les assemblys.</span><span class="sxs-lookup"><span data-stu-id="a084c-251">The type is accessible by all assemblies.</span></span>
<span data-ttu-id="a084c-252">assembly</span><span class="sxs-lookup"><span data-stu-id="a084c-252">assembly</span></span> | <span data-ttu-id="a084c-253">Le type est accessible uniquement à partir de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="a084c-253">The type is accessible only from within its assembly.</span></span>

<span data-ttu-id="a084c-254">L'accessibilité d'un type imbriqué dépend de son domaine d'accessibilité, qui est déterminé par l'accessibilité déclarée du membre et le domaine d'accessibilité du type conteneur immédiat.</span><span class="sxs-lookup"><span data-stu-id="a084c-254">The accessibility of a nested type depends on its accessibility domain, which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="a084c-255">Toutefois, le domaine d'accessibilité d'un type imbriqué ne peut pas dépasser celui du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="a084c-255">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>

<span data-ttu-id="a084c-256">Le domaine d’accessibilité d’un membre imbriqué `M` déclaré dans un type `T` à l’intérieur d’un programme `P` est défini de la manière suivante (en notant que `M` pourrait lui-même être un type) :</span><span class="sxs-lookup"><span data-stu-id="a084c-256">The accessibility domain of a nested member `M` declared in a type `T`within a program `P` is defined as follows (noting that `M` might itself be a type):</span></span> 

* <span data-ttu-id="a084c-257">Si l'accessibilité déclarée de `M` est `public`, le domaine d'accessibilité de `M` correspond à celui de `T`.</span><span class="sxs-lookup"><span data-stu-id="a084c-257">If the declared accessibility of `M` is `public`, the accessibility domain of `M` is the accessibility domain of `T`.</span></span>

* <span data-ttu-id="a084c-258">Si l'accessibilité déclarée de `M` est `protected internal`, le domaine d'accessibilité de `M` correspond à l'intersection du domaine d'accessibilité de `T` avec le texte de programme de `P` et le texte de programme de n'importe quel type dérivé de `T` déclaré en dehors de `P`.</span><span class="sxs-lookup"><span data-stu-id="a084c-258">If the declared accessibility of `M` is `protected internal`, the accessibility domain of `M` is the intersection of the accessibility domain of `T` with the program text of `P` and the program text of any type derived from `T` declared outside `P`.</span></span>

* <span data-ttu-id="a084c-259">Si l'accessibilité déclarée de `M` est `protected`, le domaine d'accessibilité de `M` correspond à l'intersection du domaine d'accessibilité de `T` avec le texte de programme de `T` et n'importe quel type dérivé de `T`.</span><span class="sxs-lookup"><span data-stu-id="a084c-259">If the declared accessibility of `M` is `protected`, the accessibility domain of `M` is the intersection of the accessibility domain of `T` with the program text of `T` and any type derived from `T`.</span></span>

* <span data-ttu-id="a084c-260">Si l’accessibilité déclarée de `M` est `internal`, le domaine d’accessibilité de `M` correspond à l’intersection du domaine d’accessibilité de `T` avec le texte de programme de `P`.</span><span class="sxs-lookup"><span data-stu-id="a084c-260">If the declared accessibility of `M` is `internal`, the accessibility domain of `M` is the intersection of the accessibility domain of `T` with the program text of`P`.</span></span>

* <span data-ttu-id="a084c-261">Si l'accessibilité déclarée de `M` est `private`, le domaine d'accessibilité de `M` correspond au texte de programme de `T`.</span><span class="sxs-lookup"><span data-stu-id="a084c-261">If the declared accessibility of `M` is `private`, the accessibility domain of `M` is the program text of `T`.</span></span>

### <a name="type-names"></a><span data-ttu-id="a084c-262">Noms de types</span><span class="sxs-lookup"><span data-stu-id="a084c-262">Type names</span></span>

<span data-ttu-id="a084c-263">Le système de type commun (CTS, Common Type System) impose uniquement deux restrictions sur les noms :</span><span class="sxs-lookup"><span data-stu-id="a084c-263">The common type system imposes only two restrictions on names:</span></span> 

* <span data-ttu-id="a084c-264">Tous les noms sont encodés comme des chaînes de caractères Unicode (16 bits).</span><span class="sxs-lookup"><span data-stu-id="a084c-264">All names are encoded as strings of Unicode (16-bit) characters.</span></span>

* <span data-ttu-id="a084c-265">Les noms ne peuvent pas incorporer la valeur (16 bits) 0x0000.</span><span class="sxs-lookup"><span data-stu-id="a084c-265">Names are not permitted to have an embedded (16-bit) value of 0x0000.</span></span>

<span data-ttu-id="a084c-266">Toutefois, la plupart des langages imposent des restrictions supplémentaires sur les noms de types.</span><span class="sxs-lookup"><span data-stu-id="a084c-266">However, most languages impose additional restrictions on type names.</span></span> <span data-ttu-id="a084c-267">Toutes les comparaisons sont effectuées octet par octet ; elles respectent donc la casse et sont indépendantes des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="a084c-267">All comparisons are done on a byte-by-byte basis, and are therefore case-sensitive and locale-independent.</span></span>

<span data-ttu-id="a084c-268">Bien qu’un type puisse référencer des types d’autres modules et assemblys, il doit être entièrement défini à l’intérieur d’un seul module .NET.</span><span class="sxs-lookup"><span data-stu-id="a084c-268">Although a type might reference types from other modules and assemblies, a type must be fully defined within one .NET module.</span></span> <span data-ttu-id="a084c-269">(Cependant, en fonction de la prise en charge du compilateur, il peut être divisé en plusieurs fichiers de code source.) Les noms de types doivent être uniques seulement à l'intérieur d'un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="a084c-269">(Depending on compiler support, however, it can be divided into multiple source code files.) Type names need be unique only within a namespace.</span></span> <span data-ttu-id="a084c-270">Pour identifier complètement un type, le nom du type doit être qualifié par l'espace de noms qui contient l'implémentation du type.</span><span class="sxs-lookup"><span data-stu-id="a084c-270">To fully identify a type, the type name must be qualified by the namespace that contains the implementation of the type.</span></span>

### <a name="base-types-and-interfaces"></a><span data-ttu-id="a084c-271">Types de base et interfaces</span><span class="sxs-lookup"><span data-stu-id="a084c-271">Base types and interfaces</span></span>

<span data-ttu-id="a084c-272">Un type peut hériter des valeurs et des comportements d'un autre type.</span><span class="sxs-lookup"><span data-stu-id="a084c-272">A type can inherit values and behaviors from another type.</span></span> <span data-ttu-id="a084c-273">Le système de type commun (CTS, Common Type System) ne permet pas à des types d'hériter de plusieurs types de base.</span><span class="sxs-lookup"><span data-stu-id="a084c-273">The common type system does not allow types to inherit from more than one base type.</span></span>

<span data-ttu-id="a084c-274">Un type peut implémenter n'importe quel nombre d'interfaces.</span><span class="sxs-lookup"><span data-stu-id="a084c-274">A type can implement any number of interfaces.</span></span> <span data-ttu-id="a084c-275">Pour implémenter une interface, un type doit implémenter tous les membres virtuels de cette interface.</span><span class="sxs-lookup"><span data-stu-id="a084c-275">To implement an interface, a type must implement all the virtual members of that interface.</span></span> <span data-ttu-id="a084c-276">Une méthode virtuelle peut être implémentée par un type dérivé et peut être appelée de manière statique ou dynamique.</span><span class="sxs-lookup"><span data-stu-id="a084c-276">A virtual method can be implemented by a derived type and can be invoked either statically or dynamically.</span></span>

## <a name="type-members"></a><span data-ttu-id="a084c-277">Membres de type</span><span class="sxs-lookup"><span data-stu-id="a084c-277">Type members</span></span>

<span data-ttu-id="a084c-278">Le runtime vous permet de définir les membres de votre type, ce qui spécifie le comportement et l'état d'un type.</span><span class="sxs-lookup"><span data-stu-id="a084c-278">The runtime enables you to define members of your type, which specifies the behavior and state of a type.</span></span> <span data-ttu-id="a084c-279">Les membres de type incluent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a084c-279">Type members include the following:</span></span>

* [<span data-ttu-id="a084c-280">Champs</span><span class="sxs-lookup"><span data-stu-id="a084c-280">Fields</span></span>](#fields)

* [<span data-ttu-id="a084c-281">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a084c-281">Properties</span></span>](#properties)

* [<span data-ttu-id="a084c-282">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a084c-282">Methods</span></span>](#methods)

* [<span data-ttu-id="a084c-283">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="a084c-283">Constructors</span></span>](#constructors)

* [<span data-ttu-id="a084c-284">Événements</span><span class="sxs-lookup"><span data-stu-id="a084c-284">Events</span></span>](#events)

* [<span data-ttu-id="a084c-285">Types imbriqués</span><span class="sxs-lookup"><span data-stu-id="a084c-285">Nested types</span></span>](#nested-types)

### <a name="fields"></a><span data-ttu-id="a084c-286">Champs</span><span class="sxs-lookup"><span data-stu-id="a084c-286">Fields</span></span>

<span data-ttu-id="a084c-287">Un champ décrit et contient une partie de l'état du type.</span><span class="sxs-lookup"><span data-stu-id="a084c-287">A field describes and contains part of the type's state.</span></span> <span data-ttu-id="a084c-288">Les champs peuvent correspondre à n'importe quel type pris en charge par le runtime.</span><span class="sxs-lookup"><span data-stu-id="a084c-288">Fields can be of any type supported by the runtime.</span></span> <span data-ttu-id="a084c-289">La plupart du temps, les champs sont soit `private`, soit `protected`, de sorte qu'ils sont accessibles uniquement à partir de la classe ou d'une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="a084c-289">Most commonly, fields are either `private` or `protected`, so that they are accessible only from within the class or from a derived class.</span></span> <span data-ttu-id="a084c-290">Si la valeur d'un champ peut être modifiée en dehors de son type, un accesseur set de propriété est en général utilisé.</span><span class="sxs-lookup"><span data-stu-id="a084c-290">If the value of a field can be modified from outside its type, a property set accessor is typically used.</span></span> <span data-ttu-id="a084c-291">Les champs exposés publiquement sont généralement en lecture seule et peuvent être de deux types :</span><span class="sxs-lookup"><span data-stu-id="a084c-291">Publicly exposed fields are usually read-only and can be of two types:</span></span> 

* <span data-ttu-id="a084c-292">Constantes, dont la valeur est assignée au moment du design.</span><span class="sxs-lookup"><span data-stu-id="a084c-292">Constants, whose value is assigned at design time.</span></span> <span data-ttu-id="a084c-293">Ce sont des membres statiques d'une classe, bien qu'ils ne soient pas définis à l'aide du mot clé `static` (`Shared` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a084c-293">These are static members of a class, although they are not defined using the `static` (`Shared` in Visual Basic) keyword.</span></span>

* <span data-ttu-id="a084c-294">Des variables en lecture seule, dont les valeurs peuvent être assignées dans le constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="a084c-294">Read-only variables, whose values can be assigned in the class constructor.</span></span>

<span data-ttu-id="a084c-295">L'exemple ci-dessous illustre ces deux utilisations de champs en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="a084c-295">The following example illustrates these two usages of read-only fields.</span></span>

```csharp
using System;

public class Constants
{
   public const double Pi = 3.1416;
   public readonly DateTime BirthDate;

   public Constants(DateTime birthDate)
   {
      this.BirthDate = birthDate;
   }
}

public class Example
{
   public static void Main()
   {
      Constants con = new Constants(new DateTime(1974, 8, 18));
      Console.Write(Constants.Pi + "\n");
      Console.Write(con.BirthDate.ToString("d") + "\n");
   }
}
// The example displays the following output if run on a system whose current
// culture is en-US:
//    3.1417
//    8/18/1974
```

```vb
Public Class Constants
   Public Const Pi As Double = 3.1416
   Public ReadOnly BirthDate As Date

   Public Sub New(birthDate As Date)
      Me.BirthDate = birthDate
   End Sub
End Class

Public Module Example
   Public Sub Main()
      Dim con As New Constants(#8/18/1974#)
      Console.WriteLine(Constants.Pi.ToString())
      Console.WriteLine(con.BirthDate.ToString("d"))
   End Sub
End Module
' The example displays the following output if run on a system whose current
' culture is en-US:
'    3.1417
'    8/18/1974
```

### <a name="properties"></a><span data-ttu-id="a084c-296">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a084c-296">Properties</span></span>

<span data-ttu-id="a084c-297">Une propriété nomme une valeur ou un état du type et définit des méthodes pour obtenir ou définir la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="a084c-297">A property names a value or state of the type and defines methods for getting or setting the property's value.</span></span> <span data-ttu-id="a084c-298">Les propriétés peuvent être des types primitifs, des collections de types primitifs, des types définis par l'utilisateur ou des collections de types définis par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a084c-298">Properties can be primitive types, collections of primitive types, user-defined types, or collections of user-defined types.</span></span> <span data-ttu-id="a084c-299">Les propriétés sont souvent utilisées pour maintenir l'interface publique d'un type indépendante de la représentation réelle du type.</span><span class="sxs-lookup"><span data-stu-id="a084c-299">Properties are often used to keep the public interface of a type independent from the type's actual representation.</span></span> <span data-ttu-id="a084c-300">Cela permet aux propriétés de refléter des valeurs qui ne sont pas directement stockées dans la classe (par exemple, lorsqu'une propriété retourne une valeur calculée) ou d'effectuer une validation avant que des valeurs soient assignées à des champs privés.</span><span class="sxs-lookup"><span data-stu-id="a084c-300">This enables properties to reflect values that are not directly stored in the class (for example, when a property returns a computed value) or to perform validation before values are assigned to private fields.</span></span> <span data-ttu-id="a084c-301">L’exemple suivant illustre ce dernier modèle.</span><span class="sxs-lookup"><span data-stu-id="a084c-301">The following example illustrates the latter pattern.</span></span>

```csharp
using System;

public class Person
{
   private int m_Age;

   public int Age
   { 
      get { return m_Age; }
      set {
         if (value < 0 || value > 125)
         {
            throw new ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.");
         }
         else
         {
            m_Age = value;
         }         
      }
   }
}
```

```vb
Public Class Person
   Private m_Age As Integer

   Public Property Age As Integer
      Get
         Return m_Age
      End Get
      Set
         If value < 0 Or value > 125 Then
            Throw New ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.")
         Else
            m_Age = value
         End If
      End Set
   End Property
End Class
```

<span data-ttu-id="a084c-302">En plus d’inclure la propriété elle-même, le langage MSIL (Microsoft Intermediate Language) pour un type qui contient une propriété lisible inclut une méthode `get`*_nompropriété*, et le MSIL pour un type qui contient une propriété accessible en écriture inclut une méthode `set`*_nompropriété*.</span><span class="sxs-lookup"><span data-stu-id="a084c-302">In addition to including the property itself, the Microsoft intermediate language (MSIL) for a type that contains a readable property includes a `get`*_propertyname* method, and the MSIL for a type that contains a writable property includes a `set`*_propertyname* method.</span></span>

### <a name="methods"></a><span data-ttu-id="a084c-303">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a084c-303">Methods</span></span>

<span data-ttu-id="a084c-304">Une méthode décrit les opérations qui sont disponibles sur le type.</span><span class="sxs-lookup"><span data-stu-id="a084c-304">A method describes operations that are available on the type.</span></span> <span data-ttu-id="a084c-305">La signature d'une méthode spécifie les types autorisés de tous ses paramètres et de sa valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="a084c-305">A method's signature specifies the allowable types of all its parameters and of its return value.</span></span>

<span data-ttu-id="a084c-306">Bien que la plupart des méthodes définissent le nombre précis de paramètres requis pour les appels de méthode, certaines méthodes acceptent un nombre variable de paramètres.</span><span class="sxs-lookup"><span data-stu-id="a084c-306">Although most methods define the precise number of parameters required for method calls, some methods support a variable number of parameters.</span></span> <span data-ttu-id="a084c-307">Le dernier paramètre déclaré de ces méthodes est marqué avec l'attribut [ParamArrayAttribute](xref:System.ParamArrayAttribute).</span><span class="sxs-lookup"><span data-stu-id="a084c-307">The final declared parameter of these methods is marked with the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute.</span></span> <span data-ttu-id="a084c-308">Les compilateurs de langage fournissent généralement un mot clé, tel que `params` en C# et `ParamArray` en Visual Basic, qui rendent l’utilisation explicite de [ParamArrayAttribute](xref:System.ParamArrayAttribute) inutile.</span><span class="sxs-lookup"><span data-stu-id="a084c-308">Language compilers typically provide a keyword, such as `params` in C# and `ParamArray` in Visual Basic, that makes explicit use of [ParamArrayAttribute](xref:System.ParamArrayAttribute) unnecessary.</span></span>

### <a name="constructors"></a><span data-ttu-id="a084c-309">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="a084c-309">Constructors</span></span>

<span data-ttu-id="a084c-310">Un constructeur est un genre de méthode particulier qui crée de nouvelles instances d'une classe ou d'une structure.</span><span class="sxs-lookup"><span data-stu-id="a084c-310">A constructor is a special kind of method that creates new instances of a class or structure.</span></span> <span data-ttu-id="a084c-311">Comme n'importe quelle autre méthode, un constructeur peut inclure des paramètres ; toutefois, les constructeurs n'ont pas de valeur de retour (en d'autres termes, ils retournent `void`).</span><span class="sxs-lookup"><span data-stu-id="a084c-311">Like any other method, a constructor can include parameters; however, constructors have no return value (that is, they return `void`).</span></span> 

<span data-ttu-id="a084c-312">Si le code source d'une classe ne définit pas explicitement un constructeur, le compilateur inclut un constructeur par défaut (sans paramètre).</span><span class="sxs-lookup"><span data-stu-id="a084c-312">If the source code for a class does not explicitly define a constructor, the compiler includes a default (parameterless) constructor.</span></span> <span data-ttu-id="a084c-313">Toutefois, si le code source d’une classe définit uniquement des constructeurs paramétrables, le compilateur C# ne génère pas de constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="a084c-313">However, if the source code for a class defines only parameterized constructors, the C# compiler doesn't generate a parameterless constructor.</span></span>

<span data-ttu-id="a084c-314">Si le code source d'une structure définit des constructeurs, ils doivent être paramétrables ; une structure ne peut pas définir un constructeur (sans paramètre) par défaut et les compilateurs ne génèrent pas de constructeur sans paramètre pour les structures ou les autres types valeurs.</span><span class="sxs-lookup"><span data-stu-id="a084c-314">If the source code for a structure defines constructors, they must be parameterized; a structure cannot define a default (parameterless) constructor, and compilers do not generate parameterless constructors for structures or other value types.</span></span> <span data-ttu-id="a084c-315">Tous les types valeurs disposent d'un constructeur implicite par défaut.</span><span class="sxs-lookup"><span data-stu-id="a084c-315">All value types do have an implicit default constructor.</span></span> <span data-ttu-id="a084c-316">Ce constructeur est implémenté par le Common Language Runtime et initialise tous les champs de la structure avec leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="a084c-316">This constructor is implemented by the common language runtime and initializes all fields of the structure to their default values.</span></span> 

### <a name="events"></a><span data-ttu-id="a084c-317">Événements</span><span class="sxs-lookup"><span data-stu-id="a084c-317">Events</span></span>

<span data-ttu-id="a084c-318">Un événement définit un incident auquel il est possible de répondre, et définit les méthodes permettant de s'abonner à l'événement, d'annuler cet abonnement et de déclencher l'événement.</span><span class="sxs-lookup"><span data-stu-id="a084c-318">An event defines an incident that can be responded to, and defines methods for subscribing to, unsubscribing from, and raising the event.</span></span> <span data-ttu-id="a084c-319">Les événements sont souvent utilisés pour signaler d'autres types de changements d'état.</span><span class="sxs-lookup"><span data-stu-id="a084c-319">Events are often used to inform other types of state changes.</span></span>

### <a name="nested-types"></a><span data-ttu-id="a084c-320">Types imbriqués</span><span class="sxs-lookup"><span data-stu-id="a084c-320">Nested types</span></span>

<span data-ttu-id="a084c-321">Un type imbriqué est un type qui est un membre d'un autre type.</span><span class="sxs-lookup"><span data-stu-id="a084c-321">A nested type is a type that is a member of some other type.</span></span> <span data-ttu-id="a084c-322">Un type imbriqué doit être fortement couplé avec le type qui le contient et ne doit pas être utilisé en tant que type à usage général.</span><span class="sxs-lookup"><span data-stu-id="a084c-322">Nested types should be tightly coupled to their containing type and must not be useful as a general-purpose type.</span></span> <span data-ttu-id="a084c-323">Ceux-ci sont utiles lorsque le type de déclaration utilise et crée des instances du type imbriqué et que l'utilisation du type imbriqué n'est pas exposée dans des membres publics.</span><span class="sxs-lookup"><span data-stu-id="a084c-323">Nested types are useful when the declaring type uses and creates instances of the nested type, and use of the nested type is not exposed in public members.</span></span>

<span data-ttu-id="a084c-324">Certains développeurs éprouvent des difficultés à appréhender correctement les types imbriqués. Il faut savoir qu'ils ne doivent pas être publiquement visibles sauf s'il existe une bonne raison à cela.</span><span class="sxs-lookup"><span data-stu-id="a084c-324">Nested types are confusing to some developers and should not be publicly visible unless there is a compelling reason for visibility.</span></span> <span data-ttu-id="a084c-325">Dans une bibliothèque bien conçue, les développeurs doivent rarement avoir à utiliser des types imbriqués pour instancier des objets ou déclarer des variables.</span><span class="sxs-lookup"><span data-stu-id="a084c-325">In a well-designed library, developers should rarely have to use nested types to instantiate objects or declare variables.</span></span>

## <a name="characteristics-of-type-members"></a><span data-ttu-id="a084c-326">Caractéristiques des membres de type</span><span class="sxs-lookup"><span data-stu-id="a084c-326">Characteristics of type members</span></span>

<span data-ttu-id="a084c-327">Le système de type commun (CTS, Common Type System) permet aux membres de type d'avoir diverses caractéristiques ; toutefois, les langages ne doivent pas obligatoirement prendre en charge toutes ces caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="a084c-327">The common type system allows type members to have a variety of characteristics; however, languages are not required to support all these characteristics.</span></span> <span data-ttu-id="a084c-328">Le tableau suivant décrit les caractéristiques des membres.</span><span class="sxs-lookup"><span data-stu-id="a084c-328">The following table describes member characteristics.</span></span>

<span data-ttu-id="a084c-329">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="a084c-329">Characteristic</span></span> | <span data-ttu-id="a084c-330">Applicable à</span><span class="sxs-lookup"><span data-stu-id="a084c-330">Can apply to</span></span> | <span data-ttu-id="a084c-331">Description</span><span class="sxs-lookup"><span data-stu-id="a084c-331">Description</span></span>
-------------- | ------------ | -----------
<span data-ttu-id="a084c-332">abstract</span><span class="sxs-lookup"><span data-stu-id="a084c-332">abstract</span></span> | <span data-ttu-id="a084c-333">Méthodes, propriétés et événements</span><span class="sxs-lookup"><span data-stu-id="a084c-333">Methods, properties, and events</span></span> | <span data-ttu-id="a084c-334">Le type n'assure pas l'implémentation de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a084c-334">The type does not supply the method's implementation.</span></span> <span data-ttu-id="a084c-335">Les types qui héritent de méthodes abstraites ou qui en implémentent doivent fournir une implémentation pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="a084c-335">Types that inherit or implement abstract methods must supply an implementation for the method.</span></span> <span data-ttu-id="a084c-336">Une exception : le type dérivé est lui-même un type abstrait.</span><span class="sxs-lookup"><span data-stu-id="a084c-336">The only exception is when the derived type is itself an abstract type.</span></span> <span data-ttu-id="a084c-337">Toutes les méthodes abstraites sont virtuelles.</span><span class="sxs-lookup"><span data-stu-id="a084c-337">All abstract methods are virtual.</span></span>
<span data-ttu-id="a084c-338">private</span><span class="sxs-lookup"><span data-stu-id="a084c-338">private</span></span> | <span data-ttu-id="a084c-339">Tous</span><span class="sxs-lookup"><span data-stu-id="a084c-339">All</span></span> | <span data-ttu-id="a084c-340">Accessible uniquement à partir du même type que le membre ou à l'intérieur d'un type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="a084c-340">Accessible only from within the same type as the member, or within a nested type.</span></span>
<span data-ttu-id="a084c-341">family</span><span class="sxs-lookup"><span data-stu-id="a084c-341">family</span></span> | <span data-ttu-id="a084c-342">Tous</span><span class="sxs-lookup"><span data-stu-id="a084c-342">All</span></span> | <span data-ttu-id="a084c-343">Accessible à partir du même type que le membre et à partir des types dérivés qui en héritent.</span><span class="sxs-lookup"><span data-stu-id="a084c-343">Accessible from within the same type as the member, and from derived types that inherit from it.</span></span>
<span data-ttu-id="a084c-344">assemby</span><span class="sxs-lookup"><span data-stu-id="a084c-344">assemby</span></span> | <span data-ttu-id="a084c-345">Tous</span><span class="sxs-lookup"><span data-stu-id="a084c-345">All</span></span> | <span data-ttu-id="a084c-346">Accessible uniquement dans l'assembly dans lequel le type est défini.</span><span class="sxs-lookup"><span data-stu-id="a084c-346">Accessible only in the assembly in which the type is defined.</span></span>
<span data-ttu-id="a084c-347">family et assembly</span><span class="sxs-lookup"><span data-stu-id="a084c-347">family and assembly</span></span> | <span data-ttu-id="a084c-348">Tous</span><span class="sxs-lookup"><span data-stu-id="a084c-348">All</span></span> | <span data-ttu-id="a084c-349">Accessible uniquement à partir des types qui se qualifient pour un accès family et assembly.</span><span class="sxs-lookup"><span data-stu-id="a084c-349">Accessible only from types that qualify for both family and assembly access.</span></span>
<span data-ttu-id="a084c-350">family ou assembly</span><span class="sxs-lookup"><span data-stu-id="a084c-350">family or assemby</span></span> | <span data-ttu-id="a084c-351">Tous</span><span class="sxs-lookup"><span data-stu-id="a084c-351">All</span></span> | <span data-ttu-id="a084c-352">Accessible uniquement à partir des types qui se qualifient pour un accès family ou assembly.</span><span class="sxs-lookup"><span data-stu-id="a084c-352">Accessible only from types that qualify for either family or assembly access.</span></span>
<span data-ttu-id="a084c-353">public</span><span class="sxs-lookup"><span data-stu-id="a084c-353">public</span></span> | <span data-ttu-id="a084c-354">Tous</span><span class="sxs-lookup"><span data-stu-id="a084c-354">All</span></span> | <span data-ttu-id="a084c-355">Accessible à partir de n'importe quel type.</span><span class="sxs-lookup"><span data-stu-id="a084c-355">Accessible from any type.</span></span>
<span data-ttu-id="a084c-356">final</span><span class="sxs-lookup"><span data-stu-id="a084c-356">final</span></span> | <span data-ttu-id="a084c-357">Méthodes, propriétés et événements</span><span class="sxs-lookup"><span data-stu-id="a084c-357">Methods, properties, and events</span></span> | <span data-ttu-id="a084c-358">La méthode virtuelle ne peut pas être substituée dans un type dérivé.</span><span class="sxs-lookup"><span data-stu-id="a084c-358">The virtual method cannot be overridden in a derived type.</span></span>
<span data-ttu-id="a084c-359">initialize-only</span><span class="sxs-lookup"><span data-stu-id="a084c-359">initialize-only</span></span> | <span data-ttu-id="a084c-360">Champs</span><span class="sxs-lookup"><span data-stu-id="a084c-360">Fields</span></span> | <span data-ttu-id="a084c-361">La valeur peut seulement être initialisée et ne peut pas être écrite après initialisation.</span><span class="sxs-lookup"><span data-stu-id="a084c-361">The value can only be initialized, and cannot be written after initialization.</span></span>
<span data-ttu-id="a084c-362">instance</span><span class="sxs-lookup"><span data-stu-id="a084c-362">instance</span></span> | <span data-ttu-id="a084c-363">Champs, méthodes, propriétés et événements</span><span class="sxs-lookup"><span data-stu-id="a084c-363">Fields, methods, properties, and events</span></span> | <span data-ttu-id="a084c-364">Si un membre n’est pas marqué comme `static` (C#), `Shared` (Visual Basic), `virtual` (C#) ou `Overridable` (Visual Basic), il est membre d’instance (il n’y a pas de mot clé d’instance).</span><span class="sxs-lookup"><span data-stu-id="a084c-364">If a member is not marked as `static` (C#), `Shared` (Visual Basic), `virtual` (C#), or `Overridable` (Visual Basic),  it is an instance member (there is no instance keyword).</span></span> <span data-ttu-id="a084c-365">La mémoire comptera autant de copies de tels membres que d'objets qui les utilisent.</span><span class="sxs-lookup"><span data-stu-id="a084c-365">There will be as many copies of such members in memory as there are objects that use it.</span></span>
<span data-ttu-id="a084c-366">littéral</span><span class="sxs-lookup"><span data-stu-id="a084c-366">literal</span></span> | <span data-ttu-id="a084c-367">Champs</span><span class="sxs-lookup"><span data-stu-id="a084c-367">Fields</span></span> | <span data-ttu-id="a084c-368">La valeur assignée au champ est une valeur fixe, connue au moment de la compilation, d'un type valeur intégré.</span><span class="sxs-lookup"><span data-stu-id="a084c-368">The value assigned to the field is a fixed value, known at compile time, of a built-in value type.</span></span> <span data-ttu-id="a084c-369">Les champs de type Literal sont parfois qualifiés de constantes.</span><span class="sxs-lookup"><span data-stu-id="a084c-369">Literal fields are sometimes referred to as constants.</span></span>
<span data-ttu-id="a084c-370">newslot ou override</span><span class="sxs-lookup"><span data-stu-id="a084c-370">newslot or override</span></span> | <span data-ttu-id="a084c-371">Tous</span><span class="sxs-lookup"><span data-stu-id="a084c-371">All</span></span> | <span data-ttu-id="a084c-372">Définit la façon dont le membre interagit avec des membres hérités ayant la même signature : `newslot` masque les membres hérités ayant la même signature ; `override` remplace la définition d’une méthode virtuelle héritée.</span><span class="sxs-lookup"><span data-stu-id="a084c-372">Defines how the member interacts with inherited members that have the same signature: `newslot` hides inherited members that have the same signature; `override` replaces the definition of an inherited virtual method.</span></span> <span data-ttu-id="a084c-373">La valeur par défaut est newslot.</span><span class="sxs-lookup"><span data-stu-id="a084c-373">The default is newslot.</span></span>
<span data-ttu-id="a084c-374">statique</span><span class="sxs-lookup"><span data-stu-id="a084c-374">static</span></span> | <span data-ttu-id="a084c-375">Champs, méthodes, propriétés et événements</span><span class="sxs-lookup"><span data-stu-id="a084c-375">Fields, methods, properties, and events</span></span> | <span data-ttu-id="a084c-376">Le membre appartient au type sur lequel il est défini, et non à une instance particulière du type ; le membre existe même si une instance du type n'est pas créée, et il est partagé entre toutes les instances du type.</span><span class="sxs-lookup"><span data-stu-id="a084c-376">The member belongs to the type it is defined on, not to a particular instance of the type; the member exists even if an instance of the type is not created, and it is shared among all instances of the type.</span></span>
<span data-ttu-id="a084c-377">virtual</span><span class="sxs-lookup"><span data-stu-id="a084c-377">virtual</span></span> | <span data-ttu-id="a084c-378">Méthodes, propriétés et événements</span><span class="sxs-lookup"><span data-stu-id="a084c-378">Methods, properties, and events</span></span> | <span data-ttu-id="a084c-379">La méthode peut être implémentée par un type dérivé et peut être appelée de manière statique ou dynamique.</span><span class="sxs-lookup"><span data-stu-id="a084c-379">The method can be implemented by a derived type and can be invoked either statically or dynamically.</span></span> <span data-ttu-id="a084c-380">Si un appel dynamique est utilisé, le type de l'instance qui effectue l'appel au moment de l'exécution détermine quelle implémentation de la méthode est appelée (plutôt que le type connu au moment de la compilation).</span><span class="sxs-lookup"><span data-stu-id="a084c-380">If dynamic invocation is used, the type of the instance that makes the call at run time (rather than the type known at compile time) determines which implementation of the method is called.</span></span> <span data-ttu-id="a084c-381">Pour appeler une méthode virtuelle de manière statique, un cast en un type qui utilise la version désirée de la méthode devra éventuellement être effectué sur la variable.</span><span class="sxs-lookup"><span data-stu-id="a084c-381">To invoke a virtual method statically, the variable might have to be cast to a type that uses the desired version of the method.</span></span>

### <a name="overloading"></a><span data-ttu-id="a084c-382">Surcharge</span><span class="sxs-lookup"><span data-stu-id="a084c-382">Overloading</span></span>

<span data-ttu-id="a084c-383">Chaque membre de type a une signature unique.</span><span class="sxs-lookup"><span data-stu-id="a084c-383">Each type member has a unique signature.</span></span> <span data-ttu-id="a084c-384">Les signatures de méthode sont composées du nom de la méthode, d'une liste de paramètres (l'ordre et les types des arguments de la méthode).</span><span class="sxs-lookup"><span data-stu-id="a084c-384">Method signatures consist of the method name and a parameter list (the order and types of the method's arguments).</span></span> <span data-ttu-id="a084c-385">Plusieurs méthodes du même nom peuvent être définies dans un type à condition que leurs signatures diffèrent.</span><span class="sxs-lookup"><span data-stu-id="a084c-385">Multiple methods with the same name can be defined within a type as long as their signatures differ.</span></span> <span data-ttu-id="a084c-386">Lorsque plusieurs méthodes du même nom sont définies, la méthode est dite surchargée.</span><span class="sxs-lookup"><span data-stu-id="a084c-386">When two or more methods with the same name are defined, the method is said to be overloaded.</span></span> <span data-ttu-id="a084c-387">Par exemple, dans [System.Char](xref:System.Char), la méthode `IsDigit` est surchargée.</span><span class="sxs-lookup"><span data-stu-id="a084c-387">For example, in [System.Char](xref:System.Char), the `IsDigit` method is overloaded.</span></span> <span data-ttu-id="a084c-388">Une seule méthode accepte un [Char](xref:System.Char).</span><span class="sxs-lookup"><span data-stu-id="a084c-388">One method takes a [Char](xref:System.Char).</span></span> <span data-ttu-id="a084c-389">L’autre méthode prend un [String](xref:System.String) et un [Int32](xref:System.Int32).</span><span class="sxs-lookup"><span data-stu-id="a084c-389">The other method takes a [String](xref:System.String) and an [Int32](xref:System.Int32).</span></span> 

> [!NOTE]
> <span data-ttu-id="a084c-390">Le type de retour n’est pas considéré comme une partie de la signature d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="a084c-390">The return type is not considered part of a method's signature.</span></span> <span data-ttu-id="a084c-391">En d'autres termes, les méthodes ne peuvent pas être surchargées si seul le type de retour les différencie.</span><span class="sxs-lookup"><span data-stu-id="a084c-391">That is, methods cannot be overloaded if they differ only by return type.</span></span>

### <a name="inheriting-overriding-and-hiding-members"></a><span data-ttu-id="a084c-392">Héritage, substitution et masquage de membres</span><span class="sxs-lookup"><span data-stu-id="a084c-392">Inheriting, overriding, and hiding members</span></span>

<span data-ttu-id="a084c-393">Un type dérivé hérite de tous les membres de son type de base ; c'est-à-dire que ces membres sont définis sur le type dérivé et disponibles pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="a084c-393">A derived type inherits all members of its base type; that is, these members are defined on, and available to, the derived type.</span></span> <span data-ttu-id="a084c-394">Le comportement ou les qualités de membres hérités peuvent être modifiés de deux manières :</span><span class="sxs-lookup"><span data-stu-id="a084c-394">The behavior or qualities of inherited members can be modified in two ways:</span></span> 

* <span data-ttu-id="a084c-395">Un type dérivé peut masquer un membre hérité en définissant un nouveau membre avec la même signature.</span><span class="sxs-lookup"><span data-stu-id="a084c-395">A derived type can hide an inherited member by defining a new member with the same signature.</span></span> <span data-ttu-id="a084c-396">Cela permet notamment de rendre privé un membre précédemment public ou de définir un nouveau comportement pour une méthode héritée marquée comme `final`.</span><span class="sxs-lookup"><span data-stu-id="a084c-396">This might be done to make a previously public member private or to define new behavior for an inherited method that is marked as `final`.</span></span>

* <span data-ttu-id="a084c-397">Un type dérivé peut substituer une méthode virtuelle héritée.</span><span class="sxs-lookup"><span data-stu-id="a084c-397">A derived type can override an inherited virtual method.</span></span> <span data-ttu-id="a084c-398">La méthode de substitution fournit une nouvelle définition de la méthode qui sera appelée en fonction du type de la valeur au moment de l'exécution et non du type de la variable connue au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="a084c-398">The overriding method provides a new definition of the method that will be invoked based on the type of the value at run time rather than the type of the variable known at compile time.</span></span> <span data-ttu-id="a084c-399">Une méthode peut substituer une méthode virtuelle uniquement si la méthode virtuelle n'est pas marquée comme `final` et si la nouvelle méthode est au moins aussi accessible que la méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="a084c-399">A method can override a virtual method only if the virtual method is not marked as `final` and the new method is at least as accessible as the virtual method.</span></span>

## <a name="see-also"></a><span data-ttu-id="a084c-400">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a084c-400">See also</span></span>

[<span data-ttu-id="a084c-401">Conversion de type dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a084c-401">Type conversion in the .NET Framework</span></span>](type-conversion.md)
