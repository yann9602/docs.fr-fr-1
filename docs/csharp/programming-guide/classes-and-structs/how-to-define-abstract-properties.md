---
title: "Guide pratique pour définir des propriétés abstraites (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: 13
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
ms.openlocfilehash: c6decaae138a21c24e94e2ed74111c860777f64b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="8e19c-102">Guide pratique pour définir des propriétés abstraites (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="8e19c-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="8e19c-103">L’exemple suivant montre comment définir des propriétés [abstract](../../../csharp/language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="8e19c-103">The following example shows how to define [abstract](../../../csharp/language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="8e19c-104">Une déclaration de propriété abstraite ne fournit pas une implémentation des accesseurs de propriété ; elle déclare que la classe prend en charge des propriétés, mais laisse l’implémentation de l’accesseur aux classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="8e19c-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="8e19c-105">L’exemple suivant montre comment implémenter les propriétés abstraites héritées d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="8e19c-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="8e19c-106">Cet exemple se compose de trois fichiers, chacun étant compilé individuellement, et l’assembly obtenu est référencé par la compilation suivante :</span><span class="sxs-lookup"><span data-stu-id="8e19c-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
-   <span data-ttu-id="8e19c-107">abstractshape.cs : classe `Shape` qui contient une propriété `Area` abstraite.</span><span class="sxs-lookup"><span data-stu-id="8e19c-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
-   <span data-ttu-id="8e19c-108">shapes.cs : sous-classes de la classe `Shape`.</span><span class="sxs-lookup"><span data-stu-id="8e19c-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
-   <span data-ttu-id="8e19c-109">shapetest.cs : programme de test destiné à afficher les zones de certains objets dérivés de `Shape`.</span><span class="sxs-lookup"><span data-stu-id="8e19c-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="8e19c-110">Pour compiler l’exemple, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8e19c-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="8e19c-111">Cette commande crée le fichier exécutable shapetest.exe.</span><span class="sxs-lookup"><span data-stu-id="8e19c-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e19c-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="8e19c-112">Example</span></span>  
 <span data-ttu-id="8e19c-113">Ce fichier déclare la classe `Shape` qui contient la propriété `Area` du type `double`.</span><span class="sxs-lookup"><span data-stu-id="8e19c-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 <span data-ttu-id="8e19c-114">[!code-cs[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8e19c-114">[!code-cs[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]</span></span>  
  
-   <span data-ttu-id="8e19c-115">Les modificateurs sur la propriété sont placés sur la déclaration de propriété proprement dite.</span><span class="sxs-lookup"><span data-stu-id="8e19c-115">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="8e19c-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8e19c-116">For example:</span></span>  
  
    ```  
    public abstract double Area  
    ```  
  
-   <span data-ttu-id="8e19c-117">Quand vous déclarez une propriété abstraite (telle que `Area` dans cet exemple), vous indiquez simplement quels les accesseurs de propriété sont disponibles, mais vous ne les implémentez pas.</span><span class="sxs-lookup"><span data-stu-id="8e19c-117">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="8e19c-118">Dans cet exemple, seul un accesseur [get](../../../csharp/language-reference/keywords/get.md) est disponible, donc la propriété est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="8e19c-118">In this example, only a [get](../../../csharp/language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e19c-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="8e19c-119">Example</span></span>  
 <span data-ttu-id="8e19c-120">Le code suivant présente trois sous-classes de `Shape` et indique comment elles substituent la propriété `Area` pour fournir leur propre implémentation.</span><span class="sxs-lookup"><span data-stu-id="8e19c-120">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 <span data-ttu-id="8e19c-121">[!code-cs[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="8e19c-121">[!code-cs[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e19c-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="8e19c-122">Example</span></span>  
 <span data-ttu-id="8e19c-123">Le code suivant montre un programme de test qui crée un certain nombre d’objets dérivés de `Shape` et imprime les zones correspondantes.</span><span class="sxs-lookup"><span data-stu-id="8e19c-123">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 <span data-ttu-id="8e19c-124">[!code-cs[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="8e19c-124">[!code-cs[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e19c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e19c-125">See Also</span></span>  
 <span data-ttu-id="8e19c-126">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8e19c-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8e19c-127">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="8e19c-127">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="8e19c-128">[Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="8e19c-128">[Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span></span>  
 <span data-ttu-id="8e19c-129">[Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="8e19c-129">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 [<span data-ttu-id="8e19c-130">Guide pratique : créer et utiliser des assemblys à l’aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="8e19c-130">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)

