---
title: "abstract (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9c6dbb03a05ff1c86752983d130691ce23e341d7
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="abstract-c-reference"></a><span data-ttu-id="d25f4-102">abstract (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d25f4-102">abstract (C# Reference)</span></span>
<span data-ttu-id="d25f4-103">Le modificateur `abstract` indique que l’élément en cours de modification a une implémentation manquante ou incomplète.</span><span class="sxs-lookup"><span data-stu-id="d25f4-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="d25f4-104">Le modificateur abstract peut être utilisé avec des classes, des méthodes, des propriétés, des indexeurs et des événements.</span><span class="sxs-lookup"><span data-stu-id="d25f4-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="d25f4-105">Dans une déclaration de classe, utilisez le modificateur `abstract` pour indiquer qu’une classe doit uniquement servir de classe de base pour d’autres classes.</span><span class="sxs-lookup"><span data-stu-id="d25f4-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes.</span></span> <span data-ttu-id="d25f4-106">Les membres définis comme abstraits, ou inclus dans une classe abstraite, doivent être implémentés par des classes dérivées de la classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="d25f4-106">Members marked as abstract, or included in an abstract class, must be implemented by classes that derive from the abstract class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d25f4-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="d25f4-107">Example</span></span>  
 <span data-ttu-id="d25f4-108">Dans cet exemple, la classe `Square` doit fournir une implémentation de `Area`, car elle dérive de la classe `ShapesClass` :</span><span class="sxs-lookup"><span data-stu-id="d25f4-108">In this example, the class `Square` must provide an implementation of `Area` because it derives from `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]  
  
 <span data-ttu-id="d25f4-109">Les classes abstraites présentent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d25f4-109">Abstract classes have the following features:</span></span>  
  
-   <span data-ttu-id="d25f4-110">Une classe abstraite ne peut pas être instanciée.</span><span class="sxs-lookup"><span data-stu-id="d25f4-110">An abstract class cannot be instantiated.</span></span>  
  
-   <span data-ttu-id="d25f4-111">Une classe abstraite peut contenir des méthodes et accesseurs abstraits.</span><span class="sxs-lookup"><span data-stu-id="d25f4-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
-   <span data-ttu-id="d25f4-112">Il n’est pas possible de modifier une classe abstraite à l’aide du modificateur [sealed](../../../csharp/language-reference/keywords/sealed.md), car les deux modificateurs ont des significations opposées.</span><span class="sxs-lookup"><span data-stu-id="d25f4-112">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifers have opposite meanings.</span></span> <span data-ttu-id="d25f4-113">Le modificateur `sealed` empêche qu’une classe soit héritée et le modificateur `abstract` exige qu’une classe soit héritée.</span><span class="sxs-lookup"><span data-stu-id="d25f4-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
-   <span data-ttu-id="d25f4-114">Une classe non abstraite dérivée d’une classe abstraite doit inclure des implémentations réelles de tous les accesseurs et méthodes abstraits hérités.</span><span class="sxs-lookup"><span data-stu-id="d25f4-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="d25f4-115">Dans une déclaration de méthode ou de propriété, utilisez le modificateur `abstract` pour indiquer que la méthode ou la propriété ne contient pas d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="d25f4-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="d25f4-116">Les méthodes abstraites présentent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d25f4-116">Abstract methods have the following features:</span></span>  
  
-   <span data-ttu-id="d25f4-117">Une méthode abstraite est implicitement une méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="d25f4-117">An abstract method is implicitly a virtual method.</span></span>  
  
-   <span data-ttu-id="d25f4-118">Les déclarations de méthodes abstraites sont autorisées uniquement dans les classes abstraites.</span><span class="sxs-lookup"><span data-stu-id="d25f4-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
-   <span data-ttu-id="d25f4-119">Comme une déclaration de méthode abstraite ne fournit pas d’implémentation réelle, il n’y a pas de corps de méthode ; la déclaration de méthode se termine simplement par un point-virgule, et la signature n’est pas suivie d’accolades ({ }).</span><span class="sxs-lookup"><span data-stu-id="d25f4-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="d25f4-120">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d25f4-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="d25f4-121">L’implémentation est fournie par une méthode de substitution ([override](../../../csharp/language-reference/keywords/override.md)), qui est membre d’une classe non abstraite.</span><span class="sxs-lookup"><span data-stu-id="d25f4-121">The implementation is provided by an method [override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
-   <span data-ttu-id="d25f4-122">L’utilisation des modificateurs [static](../../../csharp/language-reference/keywords/static.md) ou [virtual](../../../csharp/language-reference/keywords/virtual.md) dans une déclaration de méthode abstraite serait une erreur.</span><span class="sxs-lookup"><span data-stu-id="d25f4-122">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="d25f4-123">Les propriétés abstraites se comportent comme les méthodes abstraites, à l’exception des différences dans la syntaxe de déclaration et d’appel.</span><span class="sxs-lookup"><span data-stu-id="d25f4-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="d25f4-124">L’utilisation du modificateur `abstract` sur une propriété statique serait une erreur.</span><span class="sxs-lookup"><span data-stu-id="d25f4-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="d25f4-125">Une propriété abstraite héritée peut être substituée dans une classe dérivée en incluant une déclaration de propriété qui utilise le modificateur [override](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="d25f4-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="d25f4-126">Pour plus d’informations sur les classes abstraites, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="d25f4-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="d25f4-127">Une classe abstraite doit fournir une implémentation pour tous les membres d’interface.</span><span class="sxs-lookup"><span data-stu-id="d25f4-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="d25f4-128">Une classe abstraite qui implémente une interface peut mapper les méthodes d’interface à des méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="d25f4-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="d25f4-129">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d25f4-129">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="d25f4-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="d25f4-130">Example</span></span>  
 <span data-ttu-id="d25f4-131">Dans cet exemple, la classe `DerivedClass` est dérivée de la classe abstraite `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="d25f4-132">La classe abstraite contient une méthode abstraite, `AbstractMethod`, et deux propriétés abstraites, `X` et `Y`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]  
  
 <span data-ttu-id="d25f4-133">Dans l’exemple précédent, si vous tentez d’instancier la classe abstraite en utilisant une instruction comme celle-ci :</span><span class="sxs-lookup"><span data-stu-id="d25f4-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="d25f4-134">Vous obtenez une erreur indiquant que le compilateur ne peut pas créer une instance de la classe abstraite BaseClass.</span><span class="sxs-lookup"><span data-stu-id="d25f4-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d25f4-135">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d25f4-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d25f4-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d25f4-136">See Also</span></span>  
 [<span data-ttu-id="d25f4-137">Référence C#</span><span class="sxs-lookup"><span data-stu-id="d25f4-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d25f4-138">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d25f4-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d25f4-139">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="d25f4-139">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="d25f4-140">virtual</span><span class="sxs-lookup"><span data-stu-id="d25f4-140">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="d25f4-141">override</span><span class="sxs-lookup"><span data-stu-id="d25f4-141">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="d25f4-142">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="d25f4-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
