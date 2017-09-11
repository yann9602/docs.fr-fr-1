---
title: "abstract (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- abstract
- abstract_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: 24
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
ms.openlocfilehash: a109a8e37f84a2e91229bfce789a69cdc26adba9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="abstract-c-reference"></a><span data-ttu-id="e8392-102">abstract (référence C#)</span><span class="sxs-lookup"><span data-stu-id="e8392-102">abstract (C# Reference)</span></span>
<span data-ttu-id="e8392-103">Le modificateur `abstract` indique que l’élément en cours de modification a une implémentation manquante ou incomplète.</span><span class="sxs-lookup"><span data-stu-id="e8392-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="e8392-104">Le modificateur abstract peut être utilisé avec des classes, des méthodes, des propriétés, des indexeurs et des événements.</span><span class="sxs-lookup"><span data-stu-id="e8392-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="e8392-105">Dans une déclaration de classe, utilisez le modificateur `abstract` pour indiquer qu’une classe doit uniquement servir de classe de base pour d’autres classes.</span><span class="sxs-lookup"><span data-stu-id="e8392-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes.</span></span> <span data-ttu-id="e8392-106">Les membres définis comme abstraits, ou inclus dans une classe abstraite, doivent être implémentés par des classes dérivées de la classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="e8392-106">Members marked as abstract, or included in an abstract class, must be implemented by classes that derive from the abstract class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8392-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="e8392-107">Example</span></span>  
 <span data-ttu-id="e8392-108">Dans cet exemple, la classe `Square` doit fournir une implémentation de `Area`, car elle dérive de la classe `ShapesClass` :</span><span class="sxs-lookup"><span data-stu-id="e8392-108">In this example, the class `Square` must provide an implementation of `Area` because it derives from `ShapesClass`:</span></span>  
  
 <span data-ttu-id="e8392-109">[!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e8392-109">[!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]</span></span>  
  
 <span data-ttu-id="e8392-110">Les classes abstraites présentent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8392-110">Abstract classes have the following features:</span></span>  
  
-   <span data-ttu-id="e8392-111">Une classe abstraite ne peut pas être instanciée.</span><span class="sxs-lookup"><span data-stu-id="e8392-111">An abstract class cannot be instantiated.</span></span>  
  
-   <span data-ttu-id="e8392-112">Une classe abstraite peut contenir des méthodes et accesseurs abstraits.</span><span class="sxs-lookup"><span data-stu-id="e8392-112">An abstract class may contain abstract methods and accessors.</span></span>  
  
-   <span data-ttu-id="e8392-113">Il n’est pas possible de modifier une classe abstraite à l’aide du modificateur [sealed](../../../csharp/language-reference/keywords/sealed.md), car les deux modificateurs ont des significations opposées.</span><span class="sxs-lookup"><span data-stu-id="e8392-113">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifers have opposite meanings.</span></span> <span data-ttu-id="e8392-114">Le modificateur `sealed` empêche qu’une classe soit héritée et le modificateur `abstract` exige qu’une classe soit héritée.</span><span class="sxs-lookup"><span data-stu-id="e8392-114">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
-   <span data-ttu-id="e8392-115">Une classe non abstraite dérivée d’une classe abstraite doit inclure des implémentations réelles de tous les accesseurs et méthodes abstraits hérités.</span><span class="sxs-lookup"><span data-stu-id="e8392-115">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="e8392-116">Dans une déclaration de méthode ou de propriété, utilisez le modificateur `abstract` pour indiquer que la méthode ou la propriété ne contient pas d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="e8392-116">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="e8392-117">Les méthodes abstraites présentent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8392-117">Abstract methods have the following features:</span></span>  
  
-   <span data-ttu-id="e8392-118">Une méthode abstraite est implicitement une méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="e8392-118">An abstract method is implicitly a virtual method.</span></span>  
  
-   <span data-ttu-id="e8392-119">Les déclarations de méthodes abstraites sont autorisées uniquement dans les classes abstraites.</span><span class="sxs-lookup"><span data-stu-id="e8392-119">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
-   <span data-ttu-id="e8392-120">Comme une déclaration de méthode abstraite ne fournit pas d’implémentation réelle, il n’y a pas de corps de méthode ; la déclaration de méthode se termine simplement par un point-virgule, et la signature n’est pas suivie d’accolades ({ }).</span><span class="sxs-lookup"><span data-stu-id="e8392-120">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="e8392-121">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e8392-121">For example:</span></span>  
  
    ```  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="e8392-122">L’implémentation est fournie par une méthode de substitution ([override](../../../csharp/language-reference/keywords/override.md)), qui est membre d’une classe non abstraite.</span><span class="sxs-lookup"><span data-stu-id="e8392-122">The implementation is provided by an overriding method[override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
-   <span data-ttu-id="e8392-123">L’utilisation des modificateurs [static](../../../csharp/language-reference/keywords/static.md) ou [virtual](../../../csharp/language-reference/keywords/virtual.md) dans une déclaration de méthode abstraite serait une erreur.</span><span class="sxs-lookup"><span data-stu-id="e8392-123">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="e8392-124">Les propriétés abstraites se comportent comme les méthodes abstraites, à l’exception des différences dans la syntaxe de déclaration et d’appel.</span><span class="sxs-lookup"><span data-stu-id="e8392-124">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="e8392-125">L’utilisation du modificateur `abstract` sur une propriété statique serait une erreur.</span><span class="sxs-lookup"><span data-stu-id="e8392-125">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="e8392-126">Une propriété abstraite héritée peut être substituée dans une classe dérivée en incluant une déclaration de propriété qui utilise le modificateur [override](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="e8392-126">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="e8392-127">Pour plus d’informations sur les classes abstraites, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="e8392-127">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="e8392-128">Une classe abstraite doit fournir une implémentation pour tous les membres d’interface.</span><span class="sxs-lookup"><span data-stu-id="e8392-128">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="e8392-129">Une classe abstraite qui implémente une interface peut mapper les méthodes d’interface à des méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="e8392-129">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="e8392-130">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e8392-130">For example:</span></span>  
  
 <span data-ttu-id="e8392-131">[!code-cs[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e8392-131">[!code-cs[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8392-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="e8392-132">Example</span></span>  
 <span data-ttu-id="e8392-133">Dans cet exemple, la classe `DerivedClass` est dérivée de la classe abstraite `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="e8392-133">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="e8392-134">La classe abstraite contient une méthode abstraite, `AbstractMethod`, et deux propriétés abstraites, `X` et `Y`.</span><span class="sxs-lookup"><span data-stu-id="e8392-134">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
 <span data-ttu-id="e8392-135">[!code-cs[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="e8392-135">[!code-cs[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]</span></span>  
  
 <span data-ttu-id="e8392-136">Dans l’exemple précédent, si vous tentez d’instancier la classe abstraite en utilisant une instruction comme celle-ci :</span><span class="sxs-lookup"><span data-stu-id="e8392-136">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```  
BaseClass bc = new BaseClass();   // Error  
```  
  
 <span data-ttu-id="e8392-137">vous obtenez une erreur indiquant que le compilateur ne peut pas créer une instance de la classe abstraite BaseClass.</span><span class="sxs-lookup"><span data-stu-id="e8392-137">you will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e8392-138">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e8392-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e8392-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8392-139">See Also</span></span>  
 <span data-ttu-id="e8392-140">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e8392-140">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="e8392-141">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e8392-141">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e8392-142">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="e8392-142">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="e8392-143">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span><span class="sxs-lookup"><span data-stu-id="e8392-143">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span></span>  
 <span data-ttu-id="e8392-144">[override](../../../csharp/language-reference/keywords/override.md) </span><span class="sxs-lookup"><span data-stu-id="e8392-144">[override](../../../csharp/language-reference/keywords/override.md) </span></span>  
 [<span data-ttu-id="e8392-145">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="e8392-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

