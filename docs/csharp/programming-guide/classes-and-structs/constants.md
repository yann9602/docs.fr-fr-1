---
title: "Constantes (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
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
ms.openlocfilehash: 85273420e9e0dbf4b8f24568d97be127c85d5f42
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="c20aa-102">Constantes (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c20aa-102">Constants (C# Programming Guide)</span></span>
<span data-ttu-id="c20aa-103">Les constantes sont des valeurs immuables qui sont connues au moment de la compilation et qui ne changent pas pendant la durée de vie du programme.</span><span class="sxs-lookup"><span data-stu-id="c20aa-103">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="c20aa-104">Les constantes sont déclarées avec le modificateur [const](../../../csharp/language-reference/keywords/const.md).</span><span class="sxs-lookup"><span data-stu-id="c20aa-104">Constants are declared with the [const](../../../csharp/language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="c20aa-105">Seuls les types intégrés C# (à l’exclusion de <xref:System.Object?displayProperty=fullName>) peuvent être déclarés comme `const`.</span><span class="sxs-lookup"><span data-stu-id="c20aa-105">Only the C# built-in types (excluding <xref:System.Object?displayProperty=fullName>) may be declared as `const`.</span></span> <span data-ttu-id="c20aa-106">Pour obtenir une liste des types intégrés, consultez [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="c20aa-106">For a list of the built-in types, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span> <span data-ttu-id="c20aa-107">Les types définis par l’utilisateur, notamment les classes, les structs et les tableaux, ne peuvent pas être `const`.</span><span class="sxs-lookup"><span data-stu-id="c20aa-107">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="c20aa-108">Utilisez le modificateur [readonly](../../../csharp/language-reference/keywords/readonly.md) pour créer une classe, un struct ou un tableau initialisé une fois au moment de l’exécution (par exemple, dans un constructeur) et qui ne peut pas être modifié ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="c20aa-108">Use the [readonly](../../../csharp/language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="c20aa-109">C# ne prend pas en charge les propriétés, les événements ou les méthodes `const`.</span><span class="sxs-lookup"><span data-stu-id="c20aa-109">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="c20aa-110">Le type enum vous permet de définir des constantes nommées pour les types intégrés intégraux (par exemple, `int`, `uint`, `long`, etc.).</span><span class="sxs-lookup"><span data-stu-id="c20aa-110">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="c20aa-111">Pour plus d’informations, consultez [enum](../../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="c20aa-111">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="c20aa-112">Les constantes doivent être initialisées à mesure qu’elles sont déclarées.</span><span class="sxs-lookup"><span data-stu-id="c20aa-112">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="c20aa-113">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c20aa-113">For example:</span></span>  
  
 <span data-ttu-id="c20aa-114">[!code-cs[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c20aa-114">[!code-cs[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]</span></span>  
  
 <span data-ttu-id="c20aa-115">Dans cet exemple, la constante `months` est toujours 12, et ne peut pas être modifiée, même par la classe elle-même.</span><span class="sxs-lookup"><span data-stu-id="c20aa-115">In this example, the constant `months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="c20aa-116">En fait, quand le compilateur rencontre un identificateur constant dans du code source C# (par exemple, `months`), il substitue la valeur littérale directement dans le code en langage intermédiaire (IL, Intermediate Language) qu’il produit.</span><span class="sxs-lookup"><span data-stu-id="c20aa-116">In fact, when the compiler encounters a constant identifier in C# source code (for example, `months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="c20aa-117">Étant donné qu’aucune adresse de variable n’est associée à une constante au moment de l’exécution, les champs `const` ne peuvent pas être passés par référence et ne peuvent pas apparaître comme l-value dans une expression.</span><span class="sxs-lookup"><span data-stu-id="c20aa-117">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c20aa-118">Procédez avec précaution lorsque vous faites référence à des valeurs constantes définies dans un autre code telles que des DLL.</span><span class="sxs-lookup"><span data-stu-id="c20aa-118">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="c20aa-119">Si une nouvelle version de la DLL définit une nouvelle valeur pour la constante, votre programme conserve l’ancienne valeur littérale jusqu’à ce qu’elle soit recompilée sur la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="c20aa-119">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="c20aa-120">Plusieurs constantes du même type peuvent être déclarées en même temps, par exemple :</span><span class="sxs-lookup"><span data-stu-id="c20aa-120">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 <span data-ttu-id="c20aa-121">[!code-cs[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c20aa-121">[!code-cs[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]</span></span>  
  
 <span data-ttu-id="c20aa-122">L’expression utilisée pour initialiser une constante peut référencer une autre constante si elle ne crée pas de référence circulaire.</span><span class="sxs-lookup"><span data-stu-id="c20aa-122">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="c20aa-123">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c20aa-123">For example:</span></span>  
  
 <span data-ttu-id="c20aa-124">[!code-cs[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c20aa-124">[!code-cs[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]</span></span>  
  
 <span data-ttu-id="c20aa-125">Les constantes peuvent être marquées comme [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou `protected internal`.</span><span class="sxs-lookup"><span data-stu-id="c20aa-125">Constants can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or `protected internal`.</span></span> <span data-ttu-id="c20aa-126">Ces modificateurs d’accès définissent la façon dont les utilisateurs de la classe peuvent accéder à la constante.</span><span class="sxs-lookup"><span data-stu-id="c20aa-126">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="c20aa-127">Pour plus d’informations, consultez [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="c20aa-127">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="c20aa-128">Les constantes sont accessibles comme si elles étaient des champs [static](../../../csharp/language-reference/keywords/static.md), car la valeur de la constante est identique pour toutes les instances du type.</span><span class="sxs-lookup"><span data-stu-id="c20aa-128">Constants are accessed as if they were [static](../../../csharp/language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="c20aa-129">Vous n’utilisez pas le mot clé `static` pour les déclarer.</span><span class="sxs-lookup"><span data-stu-id="c20aa-129">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="c20aa-130">Les expressions ne se trouvant pas dans la classe qui définit la constante doivent utiliser le nom de la classe, un point et le nom de la constante pour accéder à la constante.</span><span class="sxs-lookup"><span data-stu-id="c20aa-130">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="c20aa-131">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c20aa-131">For example:</span></span>  
  
 <span data-ttu-id="c20aa-132">[!code-cs[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="c20aa-132">[!code-cs[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c20aa-133">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c20aa-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c20aa-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c20aa-134">See Also</span></span>  
 <span data-ttu-id="c20aa-135">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c20aa-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c20aa-136">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="c20aa-136">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="c20aa-137">[Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="c20aa-137">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 <span data-ttu-id="c20aa-138">[Types](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="c20aa-138">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="c20aa-139">[readonly](../../../csharp/language-reference/keywords/readonly.md) </span><span class="sxs-lookup"><span data-stu-id="c20aa-139">[readonly](../../../csharp/language-reference/keywords/readonly.md) </span></span>  
 [<span data-ttu-id="c20aa-140">Immutability in C# Part One: Kinds of Immutability</span><span class="sxs-lookup"><span data-stu-id="c20aa-140">Immutability in C# Part One: Kinds of Immutability</span></span>](http://go.microsoft.com/fwlink/?LinkId=112379)

