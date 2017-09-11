---
title: "sealed (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sealed
- sealed_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
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
ms.openlocfilehash: a8d0fe959eac03aad4f1ae1fada61c0ad2fd65cd
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="sealed-c-reference"></a><span data-ttu-id="124e6-102">sealed (référence C#)</span><span class="sxs-lookup"><span data-stu-id="124e6-102">sealed (C# Reference)</span></span>
<span data-ttu-id="124e6-103">Lorsqu’il est appliqué à une classe, le modificateur `sealed` empêche les autres classes d’en hériter.</span><span class="sxs-lookup"><span data-stu-id="124e6-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="124e6-104">Dans l’exemple suivant, la classe `B` hérite de la classe `A`, mais aucune classe ne peut hériter de la classe `B`.</span><span class="sxs-lookup"><span data-stu-id="124e6-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>  
  
```  
class A {}      
sealed class B : A {}  
```  
  
 <span data-ttu-id="124e6-105">Vous pouvez également utiliser le modificateur `sealed` sur une méthode ou une propriété qui substitue une méthode ou une propriété virtuelle dans une classe de base.</span><span class="sxs-lookup"><span data-stu-id="124e6-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="124e6-106">Ainsi, vous pouvez autoriser les classes à dériver de votre classe et les empêcher de substituer des méthodes ou des propriétés virtuelles spécifiques.</span><span class="sxs-lookup"><span data-stu-id="124e6-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="124e6-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="124e6-107">Example</span></span>  
 <span data-ttu-id="124e6-108">Dans l’exemple suivant, `Z` hérite de `Y` mais `Z` ne peut pas substituer la fonction virtuelle `F` qui est déclarée dans `X` et scellée (sealed) dans `Y`.</span><span class="sxs-lookup"><span data-stu-id="124e6-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>  
  
 <span data-ttu-id="124e6-109">[!code-cs[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="124e6-109">[!code-cs[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]</span></span>  
  
 <span data-ttu-id="124e6-110">Lorsque vous définissez de nouvelles méthodes ou propriétés dans une classe, vous pouvez empêcher les classes dérivées de les substituer en ne les déclarant pas comme [virtuelles](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="124e6-110">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
 <span data-ttu-id="124e6-111">Une erreur consiste à utiliser le modificateur [abstract](../../../csharp/language-reference/keywords/abstract.md) avec une classe sealed, car une classe abstraite doit être héritée par une classe qui fournit une implémentation des méthodes ou des propriétés abstraites.</span><span class="sxs-lookup"><span data-stu-id="124e6-111">It is an error to use the [abstract](../../../csharp/language-reference/keywords/abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>  
  
 <span data-ttu-id="124e6-112">Lorsqu’il est appliqué à une méthode ou une propriété, le modificateur `sealed` doit toujours être utilisé avec [override](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="124e6-112">When applied to a method or property, the `sealed` modifier must always be used with [override](../../../csharp/language-reference/keywords/override.md).</span></span>  
  
 <span data-ttu-id="124e6-113">Comme les structs sont implicitement sealed, ils ne peuvent pas être hérités.</span><span class="sxs-lookup"><span data-stu-id="124e6-113">Because structs are implicitly sealed, they cannot be inherited.</span></span>  
  
 <span data-ttu-id="124e6-114">Pour plus d’informations, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="124e6-114">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="124e6-115">Pour plus d’exemples, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="124e6-115">For more examples, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="124e6-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="124e6-116">Example</span></span>  
 <span data-ttu-id="124e6-117">[!code-cs[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="124e6-117">[!code-cs[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]</span></span>  
  
 <span data-ttu-id="124e6-118">Dans l’exemple précédent, vous pouvez essayer d’hériter de la classe sealed à l’aide de l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="124e6-118">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 <span data-ttu-id="124e6-119">Le résultat est un message d’erreur :</span><span class="sxs-lookup"><span data-stu-id="124e6-119">The result is an error message:</span></span>  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="124e6-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="124e6-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="124e6-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="124e6-121">Remarks</span></span>  
 <span data-ttu-id="124e6-122">Pour déterminer s’il faut sceller une classe, une méthode ou une propriété, vous devez généralement prendre en compte les deux points suivants :</span><span class="sxs-lookup"><span data-stu-id="124e6-122">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>  
  
-   <span data-ttu-id="124e6-123">Les avantages potentiels dont les classes dérivées peuvent bénéficier grâce à la possibilité de personnaliser votre classe.</span><span class="sxs-lookup"><span data-stu-id="124e6-123">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>  
  
-   <span data-ttu-id="124e6-124">Le risque que les classes dérivées puissent modifier vos classes de telle manière qu’elles ne fonctionnent plus correctement ou comme prévu.</span><span class="sxs-lookup"><span data-stu-id="124e6-124">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="124e6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="124e6-125">See Also</span></span>  
 <span data-ttu-id="124e6-126">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="124e6-126">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="124e6-127">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="124e6-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="124e6-128">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="124e6-128">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="124e6-129">[Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="124e6-129">[Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span></span>  
 <span data-ttu-id="124e6-130">[Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="124e6-130">[Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span></span>  
 <span data-ttu-id="124e6-131">[Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="124e6-131">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="124e6-132">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="124e6-132">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="124e6-133">[override](../../../csharp/language-reference/keywords/override.md) </span><span class="sxs-lookup"><span data-stu-id="124e6-133">[override](../../../csharp/language-reference/keywords/override.md) </span></span>  
 [<span data-ttu-id="124e6-134">virtual</span><span class="sxs-lookup"><span data-stu-id="124e6-134">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)

