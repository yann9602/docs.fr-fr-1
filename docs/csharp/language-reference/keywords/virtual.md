---
title: "virtual (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords: virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dce3333646bca6f558e3760849b6cffdb34a6c0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="virtual-c-reference"></a><span data-ttu-id="727c1-102">virtual (référence C#)</span><span class="sxs-lookup"><span data-stu-id="727c1-102">virtual (C# Reference)</span></span>
<span data-ttu-id="727c1-103">Le mot clé `virtual` sert à modifier une méthode, une propriété, un indexeur ou une déclaration event et leur permet d’être substitués dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="727c1-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="727c1-104">Par exemple, cette méthode peut être substituée par toute classe qui en hérite :</span><span class="sxs-lookup"><span data-stu-id="727c1-104">For example, this method can be overridden by any class that inherits it:</span></span>  
  
```  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 <span data-ttu-id="727c1-105">L’implémentation d’un membre virtuel peut être modifiée par un [membre de substitution](../../../csharp/language-reference/keywords/override.md) dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="727c1-105">The implementation of a virtual member can be changed by an [overriding member](../../../csharp/language-reference/keywords/override.md) in a derived class.</span></span> <span data-ttu-id="727c1-106">Pour plus d’informations sur l’utilisation du mot clé `virtual`, consultez [Gestion de version avec les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="727c1-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="727c1-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="727c1-107">Remarks</span></span>  
 <span data-ttu-id="727c1-108">Quand une méthode virtuelle est appelée, un membre de substitution est recherché dans le type d’objet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="727c1-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="727c1-109">Le membre de substitution de la classe la plus dérivée est appelé (cela peut être le membre d’origine), si aucune classe dérivée n’a substitué le membre.</span><span class="sxs-lookup"><span data-stu-id="727c1-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>  
  
 <span data-ttu-id="727c1-110">Par défaut, les méthodes ne sont pas virtuelles.</span><span class="sxs-lookup"><span data-stu-id="727c1-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="727c1-111">Vous ne pouvez pas substituer une méthode non virtuelle.</span><span class="sxs-lookup"><span data-stu-id="727c1-111">You cannot override a non-virtual method.</span></span>  
  
 <span data-ttu-id="727c1-112">Vous ne pouvez pas utiliser le `virtual` modificateur avec la `static`, `abstract`, `private`, ou `override` modificateurs.</span><span class="sxs-lookup"><span data-stu-id="727c1-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="727c1-113">L’exemple suivant illustre une propriété virtuelle :</span><span class="sxs-lookup"><span data-stu-id="727c1-113">The following example shows a virtual property:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 <span data-ttu-id="727c1-114">Les propriétés virtuelles se comportent comme les méthodes abstraites, à l’exception des différences dans la syntaxe de déclaration et d’appel.</span><span class="sxs-lookup"><span data-stu-id="727c1-114">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="727c1-115">L’utilisation du modificateur `virtual` sur une propriété statique est une erreur.</span><span class="sxs-lookup"><span data-stu-id="727c1-115">It is an error to use the `virtual` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="727c1-116">Une propriété virtuelle héritée peut être substituée dans une classe dérivée en incluant une déclaration de propriété qui utilise le modificateur `override`.</span><span class="sxs-lookup"><span data-stu-id="727c1-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="727c1-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="727c1-117">Example</span></span>  
 <span data-ttu-id="727c1-118">Dans cet exemple, la classe `Shape` contient les deux coordonnées `x` et `y`, ainsi que la méthode virtuelle `Area()`.</span><span class="sxs-lookup"><span data-stu-id="727c1-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="727c1-119">Différentes classes de formes, telles que `Circle`, `Cylinder` et `Sphere`, héritent de la classe `Shape`, et la surface est calculée pour chaque figure.</span><span class="sxs-lookup"><span data-stu-id="727c1-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="727c1-120">Chaque classe dérivée possède sa propre implémentation de substitution de `Area()`.</span><span class="sxs-lookup"><span data-stu-id="727c1-120">Each derived class has it own override implementation of `Area()`.</span></span>  
  
 <span data-ttu-id="727c1-121">Notez que les classes héritées `Circle`, `Sphere` et `Cylinder` utilisent toutes des constructeurs qui initialisent la classe de base, comme indiqué dans la déclaration suivante.</span><span class="sxs-lookup"><span data-stu-id="727c1-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>  
  
```  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 <span data-ttu-id="727c1-122">Le programme suivant calcule et affiche la zone appropriée pour chaque figure en appelant l’implémentation appropriée de la méthode `Area()`, selon l’objet associé à la méthode.</span><span class="sxs-lookup"><span data-stu-id="727c1-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="727c1-123">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="727c1-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="727c1-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="727c1-124">See Also</span></span>  
 [<span data-ttu-id="727c1-125">Référence C#</span><span class="sxs-lookup"><span data-stu-id="727c1-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="727c1-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="727c1-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="727c1-127">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="727c1-127">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="727c1-128">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="727c1-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="727c1-129">Polymorphisme</span><span class="sxs-lookup"><span data-stu-id="727c1-129">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [<span data-ttu-id="727c1-130">abstract</span><span class="sxs-lookup"><span data-stu-id="727c1-130">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
 [<span data-ttu-id="727c1-131">override</span><span class="sxs-lookup"><span data-stu-id="727c1-131">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="727c1-132">new</span><span class="sxs-lookup"><span data-stu-id="727c1-132">new</span></span>](../../../csharp/language-reference/keywords/new.md)
