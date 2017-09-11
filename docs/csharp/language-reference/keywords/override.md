---
title: "override (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- override
- override_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
caps.latest.revision: 26
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
ms.openlocfilehash: 0f5a87eaa5894b61187c379c92ad785336aa79b2
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="override-c-reference"></a><span data-ttu-id="e6200-102">override (référence C#)</span><span class="sxs-lookup"><span data-stu-id="e6200-102">override (C# Reference)</span></span>
<span data-ttu-id="e6200-103">Le modificateur `override` est nécessaire pour étendre ou modifier l’implémentation abstraite ou virtuelle d’une méthode, d’une propriété, d’un indexeur ou d’un événement hérités.</span><span class="sxs-lookup"><span data-stu-id="e6200-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6200-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e6200-104">Example</span></span>  
 <span data-ttu-id="e6200-105">Dans cet exemple, la classe `Square` doit fournir une implémentation substituée de `Area`, car `Area` est héritée de la classe abstraite `ShapesClass` :</span><span class="sxs-lookup"><span data-stu-id="e6200-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>  
  
 <span data-ttu-id="e6200-106">[!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e6200-106">[!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]</span></span>  
  
 <span data-ttu-id="e6200-107">Une méthode `override` fournit une nouvelle implémentation d’un membre hérité d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="e6200-107">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="e6200-108">La méthode substituée par une déclaration `override` est appelée méthode de base substituée.</span><span class="sxs-lookup"><span data-stu-id="e6200-108">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="e6200-109">La méthode de base substituée doit avoir la même signature que la méthode `override`.</span><span class="sxs-lookup"><span data-stu-id="e6200-109">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="e6200-110">Pour plus d’informations sur l’héritage, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="e6200-110">For information about inheritance, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="e6200-111">Vous ne pouvez pas surcharger une méthode statique ou non virtuelle.</span><span class="sxs-lookup"><span data-stu-id="e6200-111">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="e6200-112">La méthode de base substituée doit être `virtual`, `abstract` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="e6200-112">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="e6200-113">Une déclaration `override` ne peut pas changer l’accessibilité de la méthode `virtual`.</span><span class="sxs-lookup"><span data-stu-id="e6200-113">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="e6200-114">Les deux méthodes `override` et `virtual` doivent avoir le même [modificateur de niveau d’accès](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="e6200-114">Both the `override` method and the `virtual` method must have the same [access level modifier](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="e6200-115">Vous ne pouvez pas utiliser les modificateurs `new`, `static` ou `virtual` pour modifier une méthode `override`.</span><span class="sxs-lookup"><span data-stu-id="e6200-115">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>  
  
 <span data-ttu-id="e6200-116">Une déclaration de propriété de substitution doit spécifier exactement les mêmes modificateur d’accès, type et nom que la propriété héritée, et la propriété substituée doit être `virtual`, `abstract` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="e6200-116">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="e6200-117">Pour plus d’informations sur l’utilisation du mot clé `override`, consultez [Gestion de version avec les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="e6200-117">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6200-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="e6200-118">Example</span></span>  
 <span data-ttu-id="e6200-119">Cet exemple définit une classe de base nommée `Employee` et une classe dérivée nommée `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="e6200-119">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="e6200-120">La classe `SalesEmployee` inclut une propriété supplémentaire (`salesbonus`) et substitue la méthode `CalculatePay` afin de la prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="e6200-120">The `SalesEmployee` class includes an extra property, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>  
  
 <span data-ttu-id="e6200-121">[!code-cs[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e6200-121">[!code-cs[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e6200-122">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e6200-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e6200-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6200-123">See Also</span></span>  
 <span data-ttu-id="e6200-124">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e6200-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="e6200-125">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e6200-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e6200-126">[Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="e6200-126">[Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span></span>  
 <span data-ttu-id="e6200-127">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="e6200-127">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="e6200-128">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="e6200-128">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="e6200-129">[abstract](../../../csharp/language-reference/keywords/abstract.md) </span><span class="sxs-lookup"><span data-stu-id="e6200-129">[abstract](../../../csharp/language-reference/keywords/abstract.md) </span></span>  
 <span data-ttu-id="e6200-130">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span><span class="sxs-lookup"><span data-stu-id="e6200-130">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span></span>  
 <span data-ttu-id="e6200-131">[new](../../../csharp/language-reference/keywords/new.md) </span><span class="sxs-lookup"><span data-stu-id="e6200-131">[new](../../../csharp/language-reference/keywords/new.md) </span></span>  
 [<span data-ttu-id="e6200-132">Polymorphisme</span><span class="sxs-lookup"><span data-stu-id="e6200-132">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)

