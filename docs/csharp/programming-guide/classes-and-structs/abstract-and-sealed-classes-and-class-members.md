---
title: Classes abstract et sealed et membres de classe (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
caps.latest.revision: 14
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
ms.openlocfilehash: 0788ea0778b3f8b846231fc2408938b2236314c9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="872ee-102">Classes abstract et sealed et membres de classe (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="872ee-102">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="872ee-103">Le mot clé [abstract](../../../csharp/language-reference/keywords/abstract.md) vous permet de créer des classes et des membres de [class](../../../csharp/language-reference/keywords/class.md) qui sont incomplets et doivent être implémentés dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="872ee-103">The [abstract](../../../csharp/language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../../csharp/language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="872ee-104">Le mot clé [sealed](../../../csharp/language-reference/keywords/sealed.md) vous permet d’empêcher l’héritage d’une classe ou de certains membres de classe qui étaient précédemment marqués comme [virtual](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="872ee-104">The [sealed](../../../csharp/language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="872ee-105">Classes abstraites et membres de classe</span><span class="sxs-lookup"><span data-stu-id="872ee-105">Abstract Classes and Class Members</span></span>  
 <span data-ttu-id="872ee-106">Les classes peuvent être déclarées comme abstraites en plaçant le mot clé `abstract` avant la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="872ee-106">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="872ee-107">Exemple :</span><span class="sxs-lookup"><span data-stu-id="872ee-107">For example:</span></span>  
  
 <span data-ttu-id="872ee-108">[!code-cs[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="872ee-108">[!code-cs[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]</span></span>  
  
 <span data-ttu-id="872ee-109">Une classe abstraite ne peut pas être instanciée.</span><span class="sxs-lookup"><span data-stu-id="872ee-109">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="872ee-110">Le but d'une classe abstraite est de fournir une définition commune d'une classe de base pouvant être partagée par plusieurs classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="872ee-110">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="872ee-111">Par exemple, une bibliothèque de classes peut définir une classe abstraite qui est utilisée comme un paramètre pour beaucoup de ses fonctions, et exiger des programmeurs qui l'utilisent de fournir leur propre implémentation de la classe en créant une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="872ee-111">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="872ee-112">Les classes abstraites peuvent également définir des méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="872ee-112">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="872ee-113">Pour ce faire, ajoutez le mot clé `abstract` avant le type de retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="872ee-113">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="872ee-114">Exemple :</span><span class="sxs-lookup"><span data-stu-id="872ee-114">For example:</span></span>  
  
 <span data-ttu-id="872ee-115">[!code-cs[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="872ee-115">[!code-cs[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]</span></span>  
  
 <span data-ttu-id="872ee-116">Les méthodes abstraites n'ont pas d'implémentation. Ainsi, la définition de la méthode est suivie d'un point-virgule au lieu d'un bloc de méthode normal.</span><span class="sxs-lookup"><span data-stu-id="872ee-116">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="872ee-117">Les classes dérivées de la classe abstraite doivent implémenter toutes les méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="872ee-117">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="872ee-118">Lorsqu'une classe abstraite hérite d'une méthode virtuelle d'une classe de base, la classe abstraite peut substituer la méthode virtuelle par une méthode abstraite.</span><span class="sxs-lookup"><span data-stu-id="872ee-118">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="872ee-119">Exemple :</span><span class="sxs-lookup"><span data-stu-id="872ee-119">For example:</span></span>  
  
 <span data-ttu-id="872ee-120">[!code-cs[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="872ee-120">[!code-cs[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]</span></span>  
  
 <span data-ttu-id="872ee-121">Si une méthode `virtual` est déclarée `abstract`, elle demeure virtuelle pour toutes les classes qui héritent de la classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="872ee-121">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="872ee-122">Une classe qui hérite d’une méthode abstraite ne peut pas accéder à l’implémentation d’origine de la méthode. Dans l’exemple précédent, `DoWork` sur la classe F ne peut pas appeler `DoWork` sur la classe D. De cette manière, une classe abstraite peut forcer les classes dérivées à fournir de nouvelles implémentations de méthode pour les méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="872ee-122">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="872ee-123">Classes sealed et membres de classe</span><span class="sxs-lookup"><span data-stu-id="872ee-123">Sealed Classes and Class Members</span></span>  
 <span data-ttu-id="872ee-124">Les classes peuvent être déclarées comme [sealed](../../../csharp/language-reference/keywords/sealed.md) en plaçant le mot clé `sealed` avant la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="872ee-124">Classes can be declared as [sealed](../../../csharp/language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="872ee-125">Exemple :</span><span class="sxs-lookup"><span data-stu-id="872ee-125">For example:</span></span>  
  
 <span data-ttu-id="872ee-126">[!code-cs[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="872ee-126">[!code-cs[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]</span></span>  
  
 <span data-ttu-id="872ee-127">Une classe sealed ne peut pas être utilisée comme une classe de base.</span><span class="sxs-lookup"><span data-stu-id="872ee-127">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="872ee-128">Pour cette raison, elle ne peut pas également être une classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="872ee-128">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="872ee-129">Les classes sealed empêchent la dérivation.</span><span class="sxs-lookup"><span data-stu-id="872ee-129">Sealed classes prevent derivation.</span></span> <span data-ttu-id="872ee-130">Étant donné qu'elles ne peuvent pas être utilisées comme une classe de base, quelques optimisations au moment de l'exécution permettent d'accélérer un peu les appels aux membres des classes sealed.</span><span class="sxs-lookup"><span data-stu-id="872ee-130">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="872ee-131">Une méthode, un indexeur, une propriété ou un événement sur une classe dérivée qui substitue un membre virtuel de la classe de base peut déclarer ce membre comme sealed.</span><span class="sxs-lookup"><span data-stu-id="872ee-131">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="872ee-132">Cela nie l'aspect virtuel du membre pour toute classe dérivée ultérieure.</span><span class="sxs-lookup"><span data-stu-id="872ee-132">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="872ee-133">Pour ce faire, mettez le mot clé `sealed` avant le mot clé [override](../../../csharp/language-reference/keywords/override.md) dans la déclaration de membre de classe.</span><span class="sxs-lookup"><span data-stu-id="872ee-133">This is accomplished by putting the `sealed` keyword before the [override](../../../csharp/language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="872ee-134">Exemple :</span><span class="sxs-lookup"><span data-stu-id="872ee-134">For example:</span></span>  
  
 <span data-ttu-id="872ee-135">[!code-cs[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="872ee-135">[!code-cs[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="872ee-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="872ee-136">See Also</span></span>  
 <span data-ttu-id="872ee-137">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="872ee-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="872ee-138">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="872ee-138">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="872ee-139">[Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="872ee-139">[Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span></span>  
 <span data-ttu-id="872ee-140">[Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md) </span><span class="sxs-lookup"><span data-stu-id="872ee-140">[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md) </span></span>  
 <span data-ttu-id="872ee-141">[Champs](../../../csharp/programming-guide/classes-and-structs/fields.md) </span><span class="sxs-lookup"><span data-stu-id="872ee-141">[Fields](../../../csharp/programming-guide/classes-and-structs/fields.md) </span></span>  
 [<span data-ttu-id="872ee-142">Guide pratique pour définir des propriétés abstraites</span><span class="sxs-lookup"><span data-stu-id="872ee-142">How to: Define Abstract Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)

