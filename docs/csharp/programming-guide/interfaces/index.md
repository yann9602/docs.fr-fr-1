---
title: "Interfaces (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
caps.latest.revision: 45
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
ms.openlocfilehash: 0552cea71f66ba8c299b1706cab6778c9e3367c9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="interfaces-c-programming-guide"></a><span data-ttu-id="95530-102">Interfaces (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="95530-102">Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="95530-103">Une interface contient des définitions pour un groupe de fonctionnalités connexes qu'une [classe](../../../csharp/language-reference/keywords/class.md) ou un [struct](../../../csharp/language-reference/keywords/struct.md) peuvent implémenter.</span><span class="sxs-lookup"><span data-stu-id="95530-103">An interface contains definitions for a group of related functionalities that a [class](../../../csharp/language-reference/keywords/class.md) or a [struct](../../../csharp/language-reference/keywords/struct.md) can implement.</span></span>  
  
 <span data-ttu-id="95530-104">En utilisant des interfaces, vous pouvez, par exemple, inclure le comportement de plusieurs sources dans une classe.</span><span class="sxs-lookup"><span data-stu-id="95530-104">By using interfaces, you can, for example, include behavior from multiple sources in a class.</span></span> <span data-ttu-id="95530-105">Cette fonctionnalité est importante en C#, car le langage ne prend pas en charge l'héritage multiple de classes.</span><span class="sxs-lookup"><span data-stu-id="95530-105">That capability is important in C# because the language doesn't support multiple inheritance of classes.</span></span> <span data-ttu-id="95530-106">De plus, vous devez utiliser une interface si vous voulez simuler l'héritage pour des structs, car ils ne peuvent en fait pas hériter d'un autre struct ou d'une autre classe.</span><span class="sxs-lookup"><span data-stu-id="95530-106">In addition, you must use an interface if you want to simulate inheritance for structs, because they can't actually inherit from another struct or class.</span></span>  
  
 <span data-ttu-id="95530-107">Vous définissez une interface à l'aide du mot clé [interface](../../../csharp/language-reference/keywords/interface.md), comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="95530-107">You define an interface by using the [interface](../../../csharp/language-reference/keywords/interface.md) keyword, as the following example shows.</span></span>  
  
 <span data-ttu-id="95530-108">[!code-cs[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="95530-108">[!code-cs[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]</span></span>  
  
 <span data-ttu-id="95530-109">Toute classe ou tout struct qui implémentent l'interface <xref:System.IEquatable%601> doivent contenir une définition pour une méthode <xref:System.IEquatable%601.Equals%2A> qui correspond à la signature spécifiée par l'interface.</span><span class="sxs-lookup"><span data-stu-id="95530-109">Any class or struct that implements the <xref:System.IEquatable%601> interface must contain a definition for an <xref:System.IEquatable%601.Equals%2A> method that matches the signature that the interface specifies.</span></span> <span data-ttu-id="95530-110">Ainsi, vous pouvez compter sur une classe qui implémente `IEquatable<T>` pour contenir une méthode `Equals` avec laquelle une instance de la classe peut déterminer si elle est égale à une autre instance de la même classe.</span><span class="sxs-lookup"><span data-stu-id="95530-110">As a result, you can count on a class that implements `IEquatable<T>` to contain an `Equals` method with which an instance of the class can determine whether it's equal to another instance of the same class.</span></span>  
  
 <span data-ttu-id="95530-111">La définition de `IEquatable<T>` ne fournit pas d'implémentation pour `Equals`.</span><span class="sxs-lookup"><span data-stu-id="95530-111">The definition of `IEquatable<T>` doesn’t provide an implementation for `Equals`.</span></span> <span data-ttu-id="95530-112">L'interface définit uniquement la signature.</span><span class="sxs-lookup"><span data-stu-id="95530-112">The interface defines only the signature.</span></span> <span data-ttu-id="95530-113">De cette façon, une interface en C# est semblable à une classe abstraite dans laquelle toutes les méthodes sont abstraites.</span><span class="sxs-lookup"><span data-stu-id="95530-113">In that way, an interface in C# is similar to an abstract class in which all the methods are abstract.</span></span> <span data-ttu-id="95530-114">En revanche, une classe ou un struct peuvent implémenter plusieurs interfaces, mais une classe peut uniquement hériter d'une seule classe, abstraite ou non.</span><span class="sxs-lookup"><span data-stu-id="95530-114">However, a class or struct can implement multiple interfaces, but a class can inherit only a single class, abstract or not.</span></span> <span data-ttu-id="95530-115">Ainsi, en utilisant des interfaces, vous pouvez inclure le comportement de plusieurs sources dans une classe.</span><span class="sxs-lookup"><span data-stu-id="95530-115">Therefore, by using interfaces, you can include behavior from multiple sources in a class.</span></span>  
  
 <span data-ttu-id="95530-116">Pour plus d'informations sur les classes abstraites, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="95530-116">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="95530-117">Les interfaces peuvent contenir des méthodes, propriétés, événements, indexeurs ou toute combinaison de ces quatre types de membres.</span><span class="sxs-lookup"><span data-stu-id="95530-117">Interfaces can contain methods, properties, events, indexers, or any combination of those four member types.</span></span> <span data-ttu-id="95530-118">Pour obtenir des liens vers des exemples, consultez les [Sections connexes](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="95530-118">For links to examples, see [Related Sections](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections).</span></span> <span data-ttu-id="95530-119">Une interface ne peut pas contenir de constantes, champs, opérateurs, constructeurs d'instance, finaliseurs ou types.</span><span class="sxs-lookup"><span data-stu-id="95530-119">An interface can't contain constants, fields, operators, instance constructors, finalizers, or types.</span></span> <span data-ttu-id="95530-120">Les membres d’interface sont automatiquement publics et ils ne peuvent pas inclure de modificateurs d’accès.</span><span class="sxs-lookup"><span data-stu-id="95530-120">Interface members are automatically public, and they can't include any access modifiers.</span></span> <span data-ttu-id="95530-121">Les membres ne peuvent pas non plus être [statiques](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="95530-121">Members also can't be [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
 <span data-ttu-id="95530-122">Pour implémenter un membre d'interface, le membre correspondant de la classe d'implémentation doit être public, non statique et porter le même nom et la même signature que le membre d'interface.</span><span class="sxs-lookup"><span data-stu-id="95530-122">To implement an interface member, the corresponding member of the implementing class must be public, non-static, and have the same name and signature as the interface member.</span></span>  
  
 <span data-ttu-id="95530-123">Quand une classe ou un struct implémentent une interface, la classe ou le struct doivent fournir une implémentation pour tous les membres que l'interface définit.</span><span class="sxs-lookup"><span data-stu-id="95530-123">When a class or struct implements an interface, the class or struct must provide an implementation for all of the members that the interface defines.</span></span> <span data-ttu-id="95530-124">L'interface elle-même n'offre aucune fonctionnalité dont une classe ou un struct peuvent hériter de la manière qu'ils peuvent hériter d'une fonctionnalité de classe de base.</span><span class="sxs-lookup"><span data-stu-id="95530-124">The interface itself provides no functionality that a class or struct can inherit in the way that it can inherit base class functionality.</span></span> <span data-ttu-id="95530-125">Toutefois, si une classe de base implémente une interface, toute classe dérivée de la classe de base hérite de cette implémentation.</span><span class="sxs-lookup"><span data-stu-id="95530-125">However, if a base class implements an interface, any class that's derived from the base class inherits that implementation.</span></span>  
  
 <span data-ttu-id="95530-126">L'exemple suivant illustre une implémentation de l'interface IEquatable<T\>.</span><span class="sxs-lookup"><span data-stu-id="95530-126">The following example shows an implementation of the IEquatable<T\> interface.</span></span> <span data-ttu-id="95530-127">La classe d'implémentation, `Car`, doit fournir une implémentation de la méthode <xref:System.IEquatable%601.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="95530-127">The implementing class, `Car`, must provide an implementation of the <xref:System.IEquatable%601.Equals%2A> method.</span></span>  
  
 <span data-ttu-id="95530-128">[!code-cs[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="95530-128">[!code-cs[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]</span></span>  
  
 <span data-ttu-id="95530-129">Les propriétés et indexeurs d’une classe peuvent définir des accesseurs supplémentaires pour une propriété ou un indexeur qui est défini dans une interface.</span><span class="sxs-lookup"><span data-stu-id="95530-129">Properties and indexers of a class can define extra accessors for a property or indexer that's defined in an interface.</span></span> <span data-ttu-id="95530-130">Par exemple, une interface peut déclarer une propriété qui a un accesseur [get](../../../csharp/language-reference/keywords/get.md).</span><span class="sxs-lookup"><span data-stu-id="95530-130">For example, an interface might declare a property that has a [get](../../../csharp/language-reference/keywords/get.md) accessor.</span></span> <span data-ttu-id="95530-131">La classe qui implémente l’interface peut déclarer la même propriété avec à la fois un accesseur `get` et un accesseur [set](../../../csharp/language-reference/keywords/set.md).</span><span class="sxs-lookup"><span data-stu-id="95530-131">The class that implements the interface can declare the same property with both a `get` and [set](../../../csharp/language-reference/keywords/set.md) accessor.</span></span> <span data-ttu-id="95530-132">Toutefois, si la propriété ou l’indexeur utilisent une implémentation explicite, les accesseurs doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="95530-132">However, if the property or indexer uses explicit implementation, the accessors must match.</span></span> <span data-ttu-id="95530-133">Pour plus d'informations sur l'implémentation explicite, consultez les pages [Implémentation d'interface explicite](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) et [Propriétés d'interface](../../../csharp/programming-guide/classes-and-structs/interface-properties.md).</span><span class="sxs-lookup"><span data-stu-id="95530-133">For more information about explicit implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) and [Interface Properties](../../../csharp/programming-guide/classes-and-structs/interface-properties.md).</span></span>  
  
 <span data-ttu-id="95530-134">Les interfaces peuvent implémenter d'autres interfaces.</span><span class="sxs-lookup"><span data-stu-id="95530-134">Interfaces can implement other interfaces.</span></span> <span data-ttu-id="95530-135">Une classe peut inclure une interface plusieurs fois par le biais de classes de base qu'elle hérite ou d'interfaces que d'autres interfaces implémentent.</span><span class="sxs-lookup"><span data-stu-id="95530-135">A class might include an interface multiple times through base classes that it inherits or through interfaces that other interfaces implement.</span></span> <span data-ttu-id="95530-136">Toutefois, la classe peut fournir une implémentation d'une interface une seule fois et uniquement si la classe déclare l'interface dans le cadre de la définition de la classe (`class ClassName : InterfaceName`).</span><span class="sxs-lookup"><span data-stu-id="95530-136">However, the class can provide an implementation of an interface only one time and only if the class declares the interface as part of the definition of the class (`class ClassName : InterfaceName`).</span></span> <span data-ttu-id="95530-137">Si l'interface est héritée car vous avez hérité d'une classe de base qui implémente l'interface, la classe de base fournit l'implémentation des membres de l'interface.</span><span class="sxs-lookup"><span data-stu-id="95530-137">If the interface is inherited because you inherited a base class that implements the interface, the base class provides the implementation of the members of the interface.</span></span> <span data-ttu-id="95530-138">Toutefois, la classe dérivée peut implémenter de nouveau les membres d'interface au lieu d'utiliser l'implémentation héritée.</span><span class="sxs-lookup"><span data-stu-id="95530-138">However, the derived class can reimplement the interface members instead of using the inherited implementation.</span></span>  
  
 <span data-ttu-id="95530-139">Une classe de base peut également implémenter des membres d'interface à l'aide de membres virtuels.</span><span class="sxs-lookup"><span data-stu-id="95530-139">A base class can also implement interface members by using virtual members.</span></span> <span data-ttu-id="95530-140">Dans ce cas, une classe dérivée peut modifier le comportement de l'interface en substituant les membres virtuels.</span><span class="sxs-lookup"><span data-stu-id="95530-140">In that case, a derived class can change the interface behavior by overriding the virtual members.</span></span> <span data-ttu-id="95530-141">Pour plus d'informations sur les membres virtuels, consultez la page [Polymorphisme](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span><span class="sxs-lookup"><span data-stu-id="95530-141">For more information about virtual members, see [Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span></span>  
  
## <a name="interfaces-summary"></a><span data-ttu-id="95530-142">Résumé des interfaces</span><span class="sxs-lookup"><span data-stu-id="95530-142">Interfaces Summary</span></span>  
 <span data-ttu-id="95530-143">Une interface possède les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="95530-143">An interface has the following properties:</span></span>  
  
-   <span data-ttu-id="95530-144">Une interface est comme une classe de base abstraite.</span><span class="sxs-lookup"><span data-stu-id="95530-144">An interface is like an abstract base class.</span></span> <span data-ttu-id="95530-145">Toute classe ou tout struct qui implémentent l'interface doivent implémenter tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="95530-145">Any class or struct that implements the interface must implement all its members.</span></span>  
  
-   <span data-ttu-id="95530-146">Une interface ne peut pas être instanciée directement.</span><span class="sxs-lookup"><span data-stu-id="95530-146">An interface can't be instantiated directly.</span></span> <span data-ttu-id="95530-147">Ses membres sont implémentées par une classe ou un struct qui implémentent l'interface.</span><span class="sxs-lookup"><span data-stu-id="95530-147">Its members are implemented by any class or struct that implements the interface.</span></span>  
  
-   <span data-ttu-id="95530-148">Les interfaces peuvent contenir des événements, des indexeurs, des méthodes et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="95530-148">Interfaces can contain events, indexers, methods, and properties.</span></span>  
  
-   <span data-ttu-id="95530-149">Les interfaces ne contiennent aucune implémentation de méthodes.</span><span class="sxs-lookup"><span data-stu-id="95530-149">Interfaces contain no implementation of methods.</span></span>  
  
-   <span data-ttu-id="95530-150">Une classe ou un struct peuvent implémenter plusieurs interfaces.</span><span class="sxs-lookup"><span data-stu-id="95530-150">A class or struct can implement multiple interfaces.</span></span> <span data-ttu-id="95530-151">Une classe peut hériter d'une classe de base et également implémenter une ou plusieurs interfaces.</span><span class="sxs-lookup"><span data-stu-id="95530-151">A class can inherit a base class and also implement one or more interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="95530-152">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="95530-152">In This Section</span></span>  
 [<span data-ttu-id="95530-153">Implémentation d’interface explicite</span><span class="sxs-lookup"><span data-stu-id="95530-153">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 <span data-ttu-id="95530-154">Explique comment créer un membre de classe spécifique à une interface.</span><span class="sxs-lookup"><span data-stu-id="95530-154">Explains how to create a class member that’s specific to an interface.</span></span>  
  
 [<span data-ttu-id="95530-155">Comment : implémenter de manière explicite des membres d’interface</span><span class="sxs-lookup"><span data-stu-id="95530-155">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)  
 <span data-ttu-id="95530-156">Fournit un exemple montrant comment implémenter explicitement des membres d'interface.</span><span class="sxs-lookup"><span data-stu-id="95530-156">Provides an example of how to explicitly implement members of interfaces.</span></span>  
  
 [<span data-ttu-id="95530-157">Comment : implémenter de manière explicite des membres de deux interfaces</span><span class="sxs-lookup"><span data-stu-id="95530-157">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)  
 <span data-ttu-id="95530-158">Fournit un exemple montrant comment implémenter explicitement des membres d'interface avec héritage.</span><span class="sxs-lookup"><span data-stu-id="95530-158">Provides an example of how to explicitly implement members of interfaces with inheritance.</span></span>  
  
##  <span data-ttu-id="95530-159"><a name="BKMK_RelatedSections"></a> Sections connexes</span><span class="sxs-lookup"><span data-stu-id="95530-159"><a name="BKMK_RelatedSections"></a> Related Sections</span></span>  
  
-   [<span data-ttu-id="95530-160">Propriétés de l’interface</span><span class="sxs-lookup"><span data-stu-id="95530-160">Interface Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [<span data-ttu-id="95530-161">Indexeurs dans les interfaces</span><span class="sxs-lookup"><span data-stu-id="95530-161">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [<span data-ttu-id="95530-162">Guide pratique d’implémentation d’événements d’interface</span><span class="sxs-lookup"><span data-stu-id="95530-162">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="95530-163">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="95530-163">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [<span data-ttu-id="95530-164">Héritage</span><span class="sxs-lookup"><span data-stu-id="95530-164">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
  
-   [<span data-ttu-id="95530-165">Méthodes</span><span class="sxs-lookup"><span data-stu-id="95530-165">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="95530-166">Polymorphisme</span><span class="sxs-lookup"><span data-stu-id="95530-166">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
  
-   [<span data-ttu-id="95530-167">Classes abstract et sealed et membres de classe</span><span class="sxs-lookup"><span data-stu-id="95530-167">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
  
-   [<span data-ttu-id="95530-168">Propriétés</span><span class="sxs-lookup"><span data-stu-id="95530-168">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [<span data-ttu-id="95530-169">Événements</span><span class="sxs-lookup"><span data-stu-id="95530-169">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
  
-   [<span data-ttu-id="95530-170">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="95530-170">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="95530-171">Chapitre proposé</span><span class="sxs-lookup"><span data-stu-id="95530-171">Featured Book Chapter</span></span>  
 <span data-ttu-id="95530-172">[Interfaces](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx) dans [Learning C# 3.0: Master the Fundamentals of C# 3.0](http://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span><span class="sxs-lookup"><span data-stu-id="95530-172">[Interfaces](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx) in [Learning C# 3.0: Master the Fundamentals of C# 3.0](http://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95530-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95530-173">See Also</span></span>  
 <span data-ttu-id="95530-174">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="95530-174">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="95530-175">Héritage</span><span class="sxs-lookup"><span data-stu-id="95530-175">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)

