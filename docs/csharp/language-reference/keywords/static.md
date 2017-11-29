---
title: "static (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords: static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c47f4a19843039c27ef9f1602581d1004fb8fd76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="static-c-reference"></a><span data-ttu-id="eccdb-102">static (référence C#)</span><span class="sxs-lookup"><span data-stu-id="eccdb-102">static (C# Reference)</span></span>
<span data-ttu-id="eccdb-103">Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui-même plutôt qu’à un objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="eccdb-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="eccdb-104">Le modificateur `static` peut être utilisé avec des classes, des champs, des méthodes, des propriétés, des opérateurs, des événements et des constructeurs. En revanche, il ne peut pas être utilisé avec des indexeurs, des finaliseurs ni des types autres que des classes.</span><span class="sxs-lookup"><span data-stu-id="eccdb-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="eccdb-105">Pour plus d’informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="eccdb-105">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eccdb-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="eccdb-106">Example</span></span>  
 <span data-ttu-id="eccdb-107">La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :</span><span class="sxs-lookup"><span data-stu-id="eccdb-107">The following class is declared as `static` and contains only `static` methods:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 <span data-ttu-id="eccdb-108">Une déclaration de constante ou de type est implicitement un membre statique.</span><span class="sxs-lookup"><span data-stu-id="eccdb-108">A constant or type declaration is implicitly a static member.</span></span>  
  
 <span data-ttu-id="eccdb-109">Un membre statique ne peut pas être référencé via une instance.</span><span class="sxs-lookup"><span data-stu-id="eccdb-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="eccdb-110">Au lieu de cela, il est référencé via le nom de type.</span><span class="sxs-lookup"><span data-stu-id="eccdb-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="eccdb-111">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="eccdb-111">For example, consider the following class:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 <span data-ttu-id="eccdb-112">Pour faire référence au membre statique `x`, utilisez le nom complet `MyBaseC.MyStruct.x`, à moins que le membre soit accessible à partir de la même portée :</span><span class="sxs-lookup"><span data-stu-id="eccdb-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 <span data-ttu-id="eccdb-113">Alors qu’une instance d’une classe contient une copie distincte de tous les champs d’instance de la classe, il existe une seule copie de chaque champ statique.</span><span class="sxs-lookup"><span data-stu-id="eccdb-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>  
  
 <span data-ttu-id="eccdb-114">Il n’est pas possible d’utiliser [this](../../../csharp/language-reference/keywords/this.md) pour référencer des méthodes statiques ou des accesseurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="eccdb-114">It is not possible to use [this](../../../csharp/language-reference/keywords/this.md) to reference static methods or property accessors.</span></span>  
  
 <span data-ttu-id="eccdb-115">Si le mot clé `static` est appliqué à une classe, tous les membres de la classe doivent être statiques.</span><span class="sxs-lookup"><span data-stu-id="eccdb-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>  
  
 <span data-ttu-id="eccdb-116">Les classes et les classes statiques peuvent avoir des constructeurs statiques.</span><span class="sxs-lookup"><span data-stu-id="eccdb-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="eccdb-117">Les constructeurs statiques sont appelés à un moment donné entre le démarrage du programme et l’instanciation de la classe.</span><span class="sxs-lookup"><span data-stu-id="eccdb-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eccdb-118">L’utilisation du mot clé `static` est plus restreinte que dans C++.</span><span class="sxs-lookup"><span data-stu-id="eccdb-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="eccdb-119">Pour comparer avec le mot clé C++, consultez [Classes de stockage (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="eccdb-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>
  
 <span data-ttu-id="eccdb-120">Pour illustrer les membres statiques, considérons une classe qui représente un employé d’une entreprise.</span><span class="sxs-lookup"><span data-stu-id="eccdb-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="eccdb-121">Supposons que la classe contient une méthode pour compter les employés et un champ pour stocker le nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="eccdb-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="eccdb-122">La méthode et le champ n’appartiennent à aucune instance d’employé.</span><span class="sxs-lookup"><span data-stu-id="eccdb-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="eccdb-123">Au lieu de cela, ils appartiennent à la classe entreprise.</span><span class="sxs-lookup"><span data-stu-id="eccdb-123">Instead they belong to the company class.</span></span> <span data-ttu-id="eccdb-124">Par conséquent, ils doivent être déclarés comme membres statiques de cette classe.</span><span class="sxs-lookup"><span data-stu-id="eccdb-124">Therefore, they should be declared as static members of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eccdb-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="eccdb-125">Example</span></span>  
 <span data-ttu-id="eccdb-126">Cet exemple lit le nom et l’ID d’un nouvel employé, incrémente d’une unité le compteur d’employés et affiche les informations concernant le nouvel employé et le nouveau nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="eccdb-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="eccdb-127">Pour plus de simplicité, ce programme lit le nombre actuel d’employés à partir du clavier.</span><span class="sxs-lookup"><span data-stu-id="eccdb-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="eccdb-128">Dans une application réelle, ces informations doivent être lues à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="eccdb-128">In a real application, this information should be read from a file.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="eccdb-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="eccdb-129">Example</span></span>  
 <span data-ttu-id="eccdb-130">Cet exemple montre que bien que vous puissiez initialiser un champ statique à l’aide d’un autre champ statique encore non déclaré, les résultats sont indéfinis tant que vous n’assignez pas explicitement une valeur au champ statique.</span><span class="sxs-lookup"><span data-stu-id="eccdb-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="eccdb-131">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="eccdb-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eccdb-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eccdb-132">See Also</span></span>  
 [<span data-ttu-id="eccdb-133">Référence C#</span><span class="sxs-lookup"><span data-stu-id="eccdb-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="eccdb-134">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="eccdb-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="eccdb-135">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="eccdb-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="eccdb-136">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="eccdb-136">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="eccdb-137">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="eccdb-137">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
