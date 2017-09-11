---
title: "Principes fondamentaux de l’héritage (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- derived classes, inheritance
- MyClass keyword, using
- MyBase keyword, using
- Inherits statement, inheritance
- overriding, Overridable keyword
- MustInherit keyword, using
- Overrides keyword, using
- inheritance
- MustInherit classes
- MustOverride keyword, using
- classes [Visual Basic], derived
- NotInheritable keyword, using
- base classes, extending properties and methods
- NotOverridable keyword, using
- base classes, inheritance
- abstract classes, inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4892ed6dcfb3843bd6cb2de2d3e032bfeb1efdf9
ms.openlocfilehash: 43b6505634b12f7f8353866e938151f1e00fb073
ms.contentlocale: fr-fr
ms.lasthandoff: 05/16/2017

---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="9ca04-102">Éléments fondamentaux de l'héritage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ca04-102">Inheritance Basics (Visual Basic)</span></span>
<span data-ttu-id="9ca04-103">Le `Inherits` instruction permet de déclarer une nouvelle classe, appelée une *classe dérivée*, basé sur une classe existante, appelée une *classe de base*.</span><span class="sxs-lookup"><span data-stu-id="9ca04-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="9ca04-104">Les classes dérivées héritent et peuvent étendre, propriétés, méthodes, événements, champs et constantes définies dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9ca04-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="9ca04-105">La section suivante décrit certaines des règles pour l’héritage et les modificateurs que vous pouvez utiliser pour modifier les façon dont les classes héritent ou être héritées :</span><span class="sxs-lookup"><span data-stu-id="9ca04-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>  
  
-   <span data-ttu-id="9ca04-106">Par défaut, toutes les classes peuvent être héritées, sauf si marqué avec la `NotInheritable` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="9ca04-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="9ca04-107">Les classes peuvent hériter d’autres classes dans votre projet ou de classes dans d’autres assemblys faisant référence à votre projet.</span><span class="sxs-lookup"><span data-stu-id="9ca04-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>  
  
-   <span data-ttu-id="9ca04-108">Contrairement aux langages qui permettent l’héritage multiple, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permet l’héritage unique uniquement dans des classes ; autrement dit, les classes dérivées peuvent avoir qu’une seule classe de base.</span><span class="sxs-lookup"><span data-stu-id="9ca04-108">Unlike languages that allow multiple inheritance, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="9ca04-109">Bien que l’héritage multiple n’est pas autorisée dans les classes, les classes peuvent implémenter plusieurs interfaces, qui peuvent accomplir efficacement les mêmes objectifs.</span><span class="sxs-lookup"><span data-stu-id="9ca04-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>  
  
-   <span data-ttu-id="9ca04-110">Pour empêcher l’exposition d’éléments restreints dans une classe de base, le type d’accès d’une classe dérivée doit être égal ou plus restrictif que sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="9ca04-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="9ca04-111">Par exemple, un `Public` classe ne peut pas hériter une `Friend` ou un `Private` (classe) et un `Friend` classe ne peut pas hériter un `Private` classe.</span><span class="sxs-lookup"><span data-stu-id="9ca04-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>  
  
## <a name="inheritance-modifiers"></a><span data-ttu-id="9ca04-112">Modificateur d’héritage</span><span class="sxs-lookup"><span data-stu-id="9ca04-112">Inheritance Modifiers</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="9ca04-113">présente les modificateurs pour prendre en charge l’héritage et les instructions de niveau classe suivantes :</span><span class="sxs-lookup"><span data-stu-id="9ca04-113"> introduces the following class-level statements and modifiers to support inheritance:</span></span>  
  
-   <span data-ttu-id="9ca04-114">`Inherits`instruction : Spécifie la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9ca04-114">`Inherits` statement — Specifies the base class.</span></span>  
  
-   <span data-ttu-id="9ca04-115">`NotInheritable`modificateur : empêche les programmeurs d’utiliser la classe comme une classe de base.</span><span class="sxs-lookup"><span data-stu-id="9ca04-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>  
  
-   <span data-ttu-id="9ca04-116">`MustInherit`modificateur — Spécifie que la classe est conçue pour une utilisation comme classe de base uniquement.</span><span class="sxs-lookup"><span data-stu-id="9ca04-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="9ca04-117">Instances de `MustInherit` classes ne peuvent pas être créées directement ; ils ne peuvent être créées des instances de classe comme base d’une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9ca04-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="9ca04-118">(Autres langages de programmation, tels que C++ et c#, utilisent le terme *classe abstraite* pour décrire une telle classe.)</span><span class="sxs-lookup"><span data-stu-id="9ca04-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="9ca04-119">Substitution de propriétés et méthodes des Classes dérivées</span><span class="sxs-lookup"><span data-stu-id="9ca04-119">Overriding Properties and Methods in Derived Classes</span></span>  
 <span data-ttu-id="9ca04-120">Par défaut, une classe dérivée hérite des propriétés et méthodes de sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="9ca04-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="9ca04-121">Si une propriété héritée ou une méthode doit se comporter différemment dans la classe dérivée peut être *substitué*.</span><span class="sxs-lookup"><span data-stu-id="9ca04-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="9ca04-122">Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9ca04-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="9ca04-123">Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :</span><span class="sxs-lookup"><span data-stu-id="9ca04-123">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
-   <span data-ttu-id="9ca04-124">`Overridable`: Permet à une propriété ou une méthode dans une classe soit substitué dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9ca04-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>  
  
-   <span data-ttu-id="9ca04-125">`Overrides`: Remplace une `Overridable` propriété ou méthode définie dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9ca04-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>  
  
-   <span data-ttu-id="9ca04-126">`NotOverridable`— Empêche une propriété ou méthode d’être substitué dans une classe qui hérite.</span><span class="sxs-lookup"><span data-stu-id="9ca04-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="9ca04-127">Par défaut, `Public` méthodes sont `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="9ca04-127">By default, `Public` methods are `NotOverridable`.</span></span>  
  
-   <span data-ttu-id="9ca04-128">`MustOverride`— Requiert qu’une classe dérivée de substituer la propriété ou méthode.</span><span class="sxs-lookup"><span data-stu-id="9ca04-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="9ca04-129">Lorsque le `MustOverride` mot clé est utilisé, la définition de méthode se compose uniquement le `Sub`, `Function`, ou `Property` instruction.</span><span class="sxs-lookup"><span data-stu-id="9ca04-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="9ca04-130">Aucune autre instruction n’est autorisées et, en particulier sans `End Sub` ou `End Function` instruction.</span><span class="sxs-lookup"><span data-stu-id="9ca04-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="9ca04-131">`MustOverride`les méthodes doivent être déclarées dans `MustInherit` classes.</span><span class="sxs-lookup"><span data-stu-id="9ca04-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>  
  
 <span data-ttu-id="9ca04-132">Supposons que vous souhaitez définir des classes pour gérer les salaires.</span><span class="sxs-lookup"><span data-stu-id="9ca04-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="9ca04-133">Vous pouvez définir un type générique `Payroll` classe contenant un `RunPayroll` méthode permettant de calculer les salaires pour une semaine type.</span><span class="sxs-lookup"><span data-stu-id="9ca04-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="9ca04-134">Vous pouvez ensuite utiliser `Payroll` en tant que classe de base pour le plus spécialisé `BonusPayroll` classe, qui peut être utilisée lors de la distribution de primes aux employés.</span><span class="sxs-lookup"><span data-stu-id="9ca04-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>  
  
 <span data-ttu-id="9ca04-135">Le `BonusPayroll` classe peut hériter et remplacer, le `PayEmployee` méthode définie dans la base de `Payroll` (classe).</span><span class="sxs-lookup"><span data-stu-id="9ca04-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>  
  
 <span data-ttu-id="9ca04-136">L’exemple suivant définit une classe de base, `Payroll,` et une classe dérivée, `BonusPayroll`, ce qui substitue une méthode héritée, `PayEmployee`.</span><span class="sxs-lookup"><span data-stu-id="9ca04-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="9ca04-137">Une procédure, `RunPayroll`, crée et passe ensuite un `Payroll` objet et un `BonusPayroll` objet à une fonction, `Pay`, qui exécute la `PayEmployee` méthode des deux objets.</span><span class="sxs-lookup"><span data-stu-id="9ca04-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>  
  
 <span data-ttu-id="9ca04-138">[!code-vb[VbVbalrOOP&#28;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9ca04-138">[!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]</span></span>  
  
## <a name="the-mybase-keyword"></a><span data-ttu-id="9ca04-139">Le mot clé MyBase</span><span class="sxs-lookup"><span data-stu-id="9ca04-139">The MyBase Keyword</span></span>  
 <span data-ttu-id="9ca04-140">Le `MyBase` (mot clé) se comporte comme une variable objet qui fait référence à la classe de base de l’instance actuelle d’une classe.</span><span class="sxs-lookup"><span data-stu-id="9ca04-140">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="9ca04-141">`MyBase`est fréquemment utilisé pour accéder aux membres de classe de base qui sont substitués ou occultés dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9ca04-141">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="9ca04-142">En particulier, `MyBase.New` est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9ca04-142">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
 <span data-ttu-id="9ca04-143">Par exemple, supposons que vous créez une classe dérivée qui substitue une méthode héritée de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9ca04-143">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="9ca04-144">La méthode substituée peut appeler la méthode dans la classe de base et modifiez la valeur de retour comme indiqué dans le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="9ca04-144">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>  
  
 <span data-ttu-id="9ca04-145">[!code-vb[VbVbalrOOP&#109;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="9ca04-145">[!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]</span></span>  
  
 <span data-ttu-id="9ca04-146">La liste suivante décrit les restrictions sur l’utilisation de `MyBase`:</span><span class="sxs-lookup"><span data-stu-id="9ca04-146">The following list describes restrictions on using `MyBase`:</span></span>  
  
-   <span data-ttu-id="9ca04-147">`MyBase`fait référence à la classe de base immédiate et à ses membres hérités.</span><span class="sxs-lookup"><span data-stu-id="9ca04-147">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="9ca04-148">Il ne peut pas être utilisé pour accéder à `Private` membres dans la classe.</span><span class="sxs-lookup"><span data-stu-id="9ca04-148">It cannot be used to access `Private` members in the class.</span></span>  
  
-   <span data-ttu-id="9ca04-149">`MyBase`est un mot clé, pas un objet réel.</span><span class="sxs-lookup"><span data-stu-id="9ca04-149">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="9ca04-150">`MyBase`ne peut pas être assigné à une variable, passé à des procédures ou utilisé dans un `Is` comparaison.</span><span class="sxs-lookup"><span data-stu-id="9ca04-150">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="9ca04-151">La méthode qui `MyBase` qualifie ne devra pas être définies dans la classe de base immédiate ; il peut être défini à la place dans une classe de base héritée indirectement.</span><span class="sxs-lookup"><span data-stu-id="9ca04-151">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="9ca04-152">Pour une référence qualifiée par `MyBase` pour compiler correctement, une classe de base doit contenir une méthode qui correspond au nom et aux types de paramètres qui apparaissent dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="9ca04-152">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>  
  
-   <span data-ttu-id="9ca04-153">Vous ne pouvez pas utiliser `MyBase` pour appeler `MustOverride` méthodes de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9ca04-153">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>  
  
-   <span data-ttu-id="9ca04-154">`MyBase`ne peut pas être utilisé pour se qualifier lui-même.</span><span class="sxs-lookup"><span data-stu-id="9ca04-154">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="9ca04-155">Par conséquent, le code suivant n’est pas valide :</span><span class="sxs-lookup"><span data-stu-id="9ca04-155">Therefore, the following code is not valid:</span></span>  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   <span data-ttu-id="9ca04-156">`MyBase`ne peut pas être utilisé dans des modules.</span><span class="sxs-lookup"><span data-stu-id="9ca04-156">`MyBase` cannot be used in modules.</span></span>  
  
-   <span data-ttu-id="9ca04-157">`MyBase`ne peut pas être utilisé pour accéder aux membres de classe de base qui sont marquées comme `Friend` si la classe de base se trouve dans un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="9ca04-157">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>  
  
 <span data-ttu-id="9ca04-158">Pour plus d’informations et un autre exemple, consultez [Comment : accéder à une Variable masquée par une classe dérivée de](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="9ca04-158">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
## <a name="the-myclass-keyword"></a><span data-ttu-id="9ca04-159">Le mot clé MyClass</span><span class="sxs-lookup"><span data-stu-id="9ca04-159">The MyClass Keyword</span></span>  
 <span data-ttu-id="9ca04-160">Le `MyClass` (mot clé) se comporte comme une variable objet qui fait référence à l’instance actuelle d’une classe implémentée comme à l’origine.</span><span class="sxs-lookup"><span data-stu-id="9ca04-160">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="9ca04-161">`MyClass`semblable à `Me`, mais chaque méthode et propriété appeler sur `MyClass` est traitée comme si la méthode ou propriété ont été [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="9ca04-161">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="9ca04-162">Par conséquent, la méthode ou propriété n’est pas affectée par la substitution dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9ca04-162">Therefore, the method or property is not affected by overriding in a derived class.</span></span>  
  
-   <span data-ttu-id="9ca04-163">`MyClass`est un mot clé, pas un objet réel.</span><span class="sxs-lookup"><span data-stu-id="9ca04-163">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="9ca04-164">`MyClass`ne peut pas être assigné à une variable, passé à des procédures ou utilisé dans un `Is` comparaison.</span><span class="sxs-lookup"><span data-stu-id="9ca04-164">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="9ca04-165">`MyClass`fait référence à la classe conteneur et à ses membres hérités.</span><span class="sxs-lookup"><span data-stu-id="9ca04-165">`MyClass` refers to the containing class and its inherited members.</span></span>  
  
-   <span data-ttu-id="9ca04-166">`MyClass`peut être utilisé en tant que qualificateur pour `Shared` membres.</span><span class="sxs-lookup"><span data-stu-id="9ca04-166">`MyClass` can be used as a qualifier for `Shared` members.</span></span>  
  
-   <span data-ttu-id="9ca04-167">`MyClass`ne peut pas être utilisé à l’intérieur d’un `Shared` (méthode), mais peut être utilisé à l’intérieur d’une méthode d’instance pour accéder à un membre partagé d’une classe.</span><span class="sxs-lookup"><span data-stu-id="9ca04-167">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>  
  
-   <span data-ttu-id="9ca04-168">`MyClass`ne peut pas être utilisé dans des modules standard.</span><span class="sxs-lookup"><span data-stu-id="9ca04-168">`MyClass` cannot be used in standard modules.</span></span>  
  
-   <span data-ttu-id="9ca04-169">`MyClass`peut être utilisé pour désigner une méthode définie dans une classe de base et ne possède aucune implémentation de la méthode fournie dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="9ca04-169">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="9ca04-170">Cette référence a la même signification que `MyBase.` *méthode*.</span><span class="sxs-lookup"><span data-stu-id="9ca04-170">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>  
  
 <span data-ttu-id="9ca04-171">L’exemple suivant compare `Me` et `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="9ca04-171">The following example compares `Me` and `MyClass`.</span></span>  
  
```vb
Class baseClass  
    Public Overridable Sub testMethod()  
        MsgBox("Base class string")  
    End Sub  
    Public Sub useMe()  
        ' The following call uses the calling class's method, even if   
        ' that method is an override.  
        Me.testMethod()  
    End Sub  
    Public Sub useMyClass()  
        ' The following call uses this instance's method and not any  
        ' override.  
        MyClass.testMethod()  
    End Sub  
End Class  
Class derivedClass : Inherits baseClass  
    Public Overrides Sub testMethod()  
        MsgBox("Derived class string")  
    End Sub  
End Class  
Class testClasses  
    Sub startHere()  
        Dim testObj As derivedClass = New derivedClass()  
        ' The following call displays "Derived class string".  
        testObj.useMe()  
        ' The following call displays "Base class string".  
        testObj.useMyClass()  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="9ca04-172">Même si `derivedClass` substitue `testMethod`, le `MyClass` mot-clé dans `useMyClass` annule les effets de substitution et le compilateur résout l’appel vers la version de classe de base de `testMethod`.</span><span class="sxs-lookup"><span data-stu-id="9ca04-172">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca04-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ca04-173">See Also</span></span>  
 <span data-ttu-id="9ca04-174">[Inherits (instruction)](../../../../visual-basic/language-reference/statements/inherits-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9ca04-174">[Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md) </span></span>  
<span data-ttu-id="9ca04-175"> [Me, My, MyBase et MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="9ca04-175"> [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>

