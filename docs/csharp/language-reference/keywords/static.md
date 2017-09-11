---
title: "static (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- static
- static_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
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
ms.openlocfilehash: 8e46dc2f00d1c185379dba1017ca445b9ae5ae72
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="static-c-reference"></a><span data-ttu-id="79056-102">static (référence C#)</span><span class="sxs-lookup"><span data-stu-id="79056-102">static (C# Reference)</span></span>
<span data-ttu-id="79056-103">Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui-même plutôt qu’à un objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="79056-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="79056-104">Le modificateur `static` peut être utilisé avec des classes, des champs, des méthodes, des propriétés, des opérateurs, des événements et des constructeurs. En revanche, il ne peut pas être utilisé avec des indexeurs, des finaliseurs ni des types autres que des classes.</span><span class="sxs-lookup"><span data-stu-id="79056-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="79056-105">Pour plus d’informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="79056-105">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79056-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="79056-106">Example</span></span>  
 <span data-ttu-id="79056-107">La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :</span><span class="sxs-lookup"><span data-stu-id="79056-107">The following class is declared as `static` and contains only `static` methods:</span></span>  
  
 <span data-ttu-id="79056-108">[!code-cs[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="79056-108">[!code-cs[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]</span></span>  
  
 <span data-ttu-id="79056-109">Une déclaration de constante ou de type est implicitement un membre statique.</span><span class="sxs-lookup"><span data-stu-id="79056-109">A constant or type declaration is implicitly a static member.</span></span>  
  
 <span data-ttu-id="79056-110">Un membre statique ne peut pas être référencé via une instance.</span><span class="sxs-lookup"><span data-stu-id="79056-110">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="79056-111">Au lieu de cela, il est référencé via le nom de type.</span><span class="sxs-lookup"><span data-stu-id="79056-111">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="79056-112">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="79056-112">For example, consider the following class:</span></span>  
  
 <span data-ttu-id="79056-113">[!code-cs[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="79056-113">[!code-cs[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]</span></span>  
  
 <span data-ttu-id="79056-114">Pour faire référence au membre statique `x`, utilisez le nom complet `MyBaseC.MyStruct.x`, à moins que le membre soit accessible à partir de la même portée :</span><span class="sxs-lookup"><span data-stu-id="79056-114">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 <span data-ttu-id="79056-115">Alors qu’une instance d’une classe contient une copie distincte de tous les champs d’instance de la classe, il existe une seule copie de chaque champ statique.</span><span class="sxs-lookup"><span data-stu-id="79056-115">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>  
  
 <span data-ttu-id="79056-116">Il n’est pas possible d’utiliser [this](../../../csharp/language-reference/keywords/this.md) pour référencer des méthodes statiques ou des accesseurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="79056-116">It is not possible to use [this](../../../csharp/language-reference/keywords/this.md) to reference static methods or property accessors.</span></span>  
  
 <span data-ttu-id="79056-117">Si le mot clé `static` est appliqué à une classe, tous les membres de la classe doivent être statiques.</span><span class="sxs-lookup"><span data-stu-id="79056-117">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>  
  
 <span data-ttu-id="79056-118">Les classes et les classes statiques peuvent avoir des constructeurs statiques.</span><span class="sxs-lookup"><span data-stu-id="79056-118">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="79056-119">Les constructeurs statiques sont appelés à un moment donné entre le démarrage du programme et l’instanciation de la classe.</span><span class="sxs-lookup"><span data-stu-id="79056-119">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79056-120">L’utilisation du mot clé `static` est plus restreinte que dans C++.</span><span class="sxs-lookup"><span data-stu-id="79056-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="79056-121">Pour comparer avec le mot clé C++, consultez [Classes de stockage (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="79056-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>
  
 <span data-ttu-id="79056-122">Pour illustrer les membres statiques, considérons une classe qui représente un employé d’une entreprise.</span><span class="sxs-lookup"><span data-stu-id="79056-122">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="79056-123">Supposons que la classe contient une méthode pour compter les employés et un champ pour stocker le nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="79056-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="79056-124">La méthode et le champ n’appartiennent à aucune instance d’employé.</span><span class="sxs-lookup"><span data-stu-id="79056-124">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="79056-125">Au lieu de cela, ils appartiennent à la classe entreprise.</span><span class="sxs-lookup"><span data-stu-id="79056-125">Instead they belong to the company class.</span></span> <span data-ttu-id="79056-126">Par conséquent, ils doivent être déclarés comme membres statiques de cette classe.</span><span class="sxs-lookup"><span data-stu-id="79056-126">Therefore, they should be declared as static members of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79056-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="79056-127">Example</span></span>  
 <span data-ttu-id="79056-128">Cet exemple lit le nom et l’ID d’un nouvel employé, incrémente d’une unité le compteur d’employés et affiche les informations concernant le nouvel employé et le nouveau nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="79056-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="79056-129">Pour plus de simplicité, ce programme lit le nombre actuel d’employés à partir du clavier.</span><span class="sxs-lookup"><span data-stu-id="79056-129">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="79056-130">Dans une application réelle, ces informations doivent être lues à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="79056-130">In a real application, this information should be read from a file.</span></span>  
  
 <span data-ttu-id="79056-131">[!code-cs[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="79056-131">[!code-cs[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="79056-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="79056-132">Example</span></span>  
 <span data-ttu-id="79056-133">Cet exemple montre que bien que vous puissiez initialiser un champ statique à l’aide d’un autre champ statique encore non déclaré, les résultats sont indéfinis tant que vous n’assignez pas explicitement une valeur au champ statique.</span><span class="sxs-lookup"><span data-stu-id="79056-133">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>  
  
 <span data-ttu-id="79056-134">[!code-cs[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="79056-134">[!code-cs[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="79056-135">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="79056-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="79056-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79056-136">See Also</span></span>  
 <span data-ttu-id="79056-137">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="79056-137">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="79056-138">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="79056-138">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="79056-139">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="79056-139">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="79056-140">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="79056-140">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 [<span data-ttu-id="79056-141">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="79056-141">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)

