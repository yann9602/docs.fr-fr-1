---
title: "virtual (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- virtual_CSharpKeyword
- virtual
dev_langs:
- CSharp
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
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
ms.openlocfilehash: 24ca77a0a645a17c0223437e73539bc04ba80f23
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="virtual-c-reference"></a><span data-ttu-id="ef512-102">virtual (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ef512-102">virtual (C# Reference)</span></span>
<span data-ttu-id="ef512-103">Le mot clé `virtual` sert à modifier une méthode, une propriété, un indexeur ou une déclaration event et leur permet d’être substitués dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="ef512-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="ef512-104">Par exemple, cette méthode peut être substituée par toute classe qui en hérite :</span><span class="sxs-lookup"><span data-stu-id="ef512-104">For example, this method can be overridden by any class that inherits it:</span></span>  
  
```  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 <span data-ttu-id="ef512-105">L’implémentation d’un membre virtuel peut être modifiée par un [membre de substitution](../../../csharp/language-reference/keywords/override.md) dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="ef512-105">The implementation of a virtual member can be changed by an [overriding member](../../../csharp/language-reference/keywords/override.md) in a derived class.</span></span> <span data-ttu-id="ef512-106">Pour plus d’informations sur l’utilisation du mot clé `virtual`, consultez [Gestion de version avec les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="ef512-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef512-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="ef512-107">Remarks</span></span>  
 <span data-ttu-id="ef512-108">Quand une méthode virtuelle est appelée, un membre de substitution est recherché dans le type d’objet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ef512-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="ef512-109">Le membre de substitution de la classe la plus dérivée est appelé (cela peut être le membre d’origine), si aucune classe dérivée n’a substitué le membre.</span><span class="sxs-lookup"><span data-stu-id="ef512-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>  
  
 <span data-ttu-id="ef512-110">Par défaut, les méthodes ne sont pas virtuelles.</span><span class="sxs-lookup"><span data-stu-id="ef512-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="ef512-111">Vous ne pouvez pas substituer une méthode non virtuelle.</span><span class="sxs-lookup"><span data-stu-id="ef512-111">You cannot override a non-virtual method.</span></span>  
  
 <span data-ttu-id="ef512-112">Vous ne pouvez pas utiliser le modificateur `virtual` avec les modificateurs `static`, `abstract, private` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="ef512-112">You cannot use the `virtual` modifier with the `static`, `abstract, private`, or `override` modifiers.</span></span> <span data-ttu-id="ef512-113">L’exemple suivant illustre une propriété virtuelle :</span><span class="sxs-lookup"><span data-stu-id="ef512-113">The following example shows a virtual property:</span></span>  
  
 <span data-ttu-id="ef512-114">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ef512-114">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]</span></span>  
  
 <span data-ttu-id="ef512-115">Les propriétés virtuelles se comportent comme les méthodes abstraites, à l’exception des différences dans la syntaxe de déclaration et d’appel.</span><span class="sxs-lookup"><span data-stu-id="ef512-115">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="ef512-116">L’utilisation du modificateur `virtual` sur une propriété statique est une erreur.</span><span class="sxs-lookup"><span data-stu-id="ef512-116">It is an error to use the `virtual` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="ef512-117">Une propriété virtuelle héritée peut être substituée dans une classe dérivée en incluant une déclaration de propriété qui utilise le modificateur `override`.</span><span class="sxs-lookup"><span data-stu-id="ef512-117">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef512-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="ef512-118">Example</span></span>  
 <span data-ttu-id="ef512-119">Dans cet exemple, la classe `Shape` contient les deux coordonnées `x` et `y`, ainsi que la méthode virtuelle `Area()`.</span><span class="sxs-lookup"><span data-stu-id="ef512-119">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="ef512-120">Différentes classes de formes, telles que `Circle`, `Cylinder` et `Sphere`, héritent de la classe `Shape`, et la surface est calculée pour chaque figure.</span><span class="sxs-lookup"><span data-stu-id="ef512-120">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="ef512-121">Chaque classe dérivée possède sa propre implémentation de substitution de `Area()`.</span><span class="sxs-lookup"><span data-stu-id="ef512-121">Each derived class has it own override implementation of `Area()`.</span></span>  
  
 <span data-ttu-id="ef512-122">Notez que les classes héritées `Circle`, `Sphere` et `Cylinder` utilisent toutes des constructeurs qui initialisent la classe de base, comme indiqué dans la déclaration suivante.</span><span class="sxs-lookup"><span data-stu-id="ef512-122">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>  
  
```  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 <span data-ttu-id="ef512-123">Le programme suivant calcule et affiche la zone appropriée pour chaque figure en appelant l’implémentation appropriée de la méthode `Area()`, selon l’objet associé à la méthode.</span><span class="sxs-lookup"><span data-stu-id="ef512-123">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>  
  
 <span data-ttu-id="ef512-124">[!code-cs[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ef512-124">[!code-cs[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ef512-125">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ef512-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ef512-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef512-126">See Also</span></span>  
 <span data-ttu-id="ef512-127">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ef512-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ef512-128">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ef512-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ef512-129">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="ef512-129">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="ef512-130">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="ef512-130">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="ef512-131">[Polymorphisme](../../../csharp/programming-guide/classes-and-structs/polymorphism.md) </span><span class="sxs-lookup"><span data-stu-id="ef512-131">[Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md) </span></span>  
 <span data-ttu-id="ef512-132">[abstract](../../../csharp/language-reference/keywords/abstract.md) </span><span class="sxs-lookup"><span data-stu-id="ef512-132">[abstract](../../../csharp/language-reference/keywords/abstract.md) </span></span>  
 <span data-ttu-id="ef512-133">[override](../../../csharp/language-reference/keywords/override.md) </span><span class="sxs-lookup"><span data-stu-id="ef512-133">[override](../../../csharp/language-reference/keywords/override.md) </span></span>  
 [<span data-ttu-id="ef512-134">new</span><span class="sxs-lookup"><span data-stu-id="ef512-134">new</span></span>](../../../csharp/language-reference/keywords/new.md)

