---
title: "Types valeur (informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.valuetypes
dev_langs:
- CSharp
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: 18
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
ms.openlocfilehash: 7500426846562dd7f3bbb8ea99f300a3e8a26546
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="value-types-c-reference"></a><span data-ttu-id="cc6d2-102">Types valeur (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="cc6d2-102">Value Types (C# Reference)</span></span>
<span data-ttu-id="cc6d2-103">Les types valeur se composent de deux catégories principales :</span><span class="sxs-lookup"><span data-stu-id="cc6d2-103">The value types consist of two main categories:</span></span>  
  
-   [<span data-ttu-id="cc6d2-104">Structs</span><span class="sxs-lookup"><span data-stu-id="cc6d2-104">Structs</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="cc6d2-105">Énumérations</span><span class="sxs-lookup"><span data-stu-id="cc6d2-105">Enumerations</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
 <span data-ttu-id="cc6d2-106">Les structs appartiennent aux catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc6d2-106">Structs fall into these categories:</span></span>  
  
-   <span data-ttu-id="cc6d2-107">Types numériques</span><span class="sxs-lookup"><span data-stu-id="cc6d2-107">Numeric types</span></span>  
  
    -   [<span data-ttu-id="cc6d2-108">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="cc6d2-108">Integral types</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [<span data-ttu-id="cc6d2-109">Types virgule flottante</span><span class="sxs-lookup"><span data-stu-id="cc6d2-109">Floating-point types</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [<span data-ttu-id="cc6d2-110">decimal</span><span class="sxs-lookup"><span data-stu-id="cc6d2-110">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [<span data-ttu-id="cc6d2-111">bool</span><span class="sxs-lookup"><span data-stu-id="cc6d2-111">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)  
  
-   <span data-ttu-id="cc6d2-112">Structs définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-112">User defined structs.</span></span>  
  
## <a name="main-features-of-value-types"></a><span data-ttu-id="cc6d2-113">Principales fonctionnalités des types valeur</span><span class="sxs-lookup"><span data-stu-id="cc6d2-113">Main Features of Value Types</span></span>  
 <span data-ttu-id="cc6d2-114">Les variables basées sur des types valeur contiennent directement des valeurs.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-114">Variables that are based on value types directly contain values.</span></span> <span data-ttu-id="cc6d2-115">Le fait d’assigner une variable de type valeur à une autre a pour effet de copier la valeur contenue,</span><span class="sxs-lookup"><span data-stu-id="cc6d2-115">Assigning one value type variable to another copies the contained value.</span></span> <span data-ttu-id="cc6d2-116">contrairement à une opération d’assignation de variables de type référence, qui copie une référence à l’objet mais pas l’objet lui-même.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-116">This differs from the assignment of reference type variables, which copies a reference to the object but not the object itself.</span></span>  
  
 <span data-ttu-id="cc6d2-117">Tous les types valeur sont implicitement dérivés de <xref:System.ValueType?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-117">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="cc6d2-118">Contrairement aux types référence, vous ne pouvez pas faire dériver un nouveau type d’un type valeur.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-118">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="cc6d2-119">En revanche, comme les types référence, les structs peuvent implémenter des interfaces.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-119">However, like reference types, structs can implement interfaces.</span></span>  
  
 <span data-ttu-id="cc6d2-120">Contrairement aux types référence, un type valeur ne peut pas contenir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-120">Unlike reference types, a value type cannot contain the `null` value.</span></span> <span data-ttu-id="cc6d2-121">Cependant, la fonctionnalité [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md) n’autorise pas l’assignation de types valeur à `null`.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-121">However, the [nullable types](../../../csharp/programming-guide/nullable-types/index.md) feature does allow for value types to be assigned to `null`.</span></span>  
  
 <span data-ttu-id="cc6d2-122">Chaque type valeur a un constructeur par défaut implicite qui initialise la valeur par défaut de ce type.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-122">Each value type has an implicit default constructor that initializes the default value of that type.</span></span> <span data-ttu-id="cc6d2-123">Pour plus d’informations sur les valeurs par défaut des types valeur, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="cc6d2-123">For information about default values of value types, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="main-features-of-simple-types"></a><span data-ttu-id="cc6d2-124">Principales fonctionnalités des types simples</span><span class="sxs-lookup"><span data-stu-id="cc6d2-124">Main Features of Simple Types</span></span>  
 <span data-ttu-id="cc6d2-125">Tous les types simples (ceux qui font partie intégrante du langage C#) sont des alias des types du système .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-125">All of the simple types -- those integral to the C# language -- are aliases of the .NET Framework System types.</span></span> <span data-ttu-id="cc6d2-126">Par exemple, [int](../../../csharp/language-reference/keywords/int.md) est un alias de <xref:System.Int32?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-126">For example, [int](../../../csharp/language-reference/keywords/int.md) is an alias of <xref:System.Int32?displayProperty=fullName>.</span></span> <span data-ttu-id="cc6d2-127">Pour obtenir la liste complète des alias, consultez [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="cc6d2-127">For a complete list of aliases, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span>  
  
 <span data-ttu-id="cc6d2-128">Les expressions constantes, dont les opérandes sont tous des constantes de type simple, sont évaluées au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-128">Constant expressions, whose operands are all simple type constants, are evaluated at compilation time.</span></span>  
  
 <span data-ttu-id="cc6d2-129">Les types simples peuvent être initialisés à l’aide de littéraux.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-129">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="cc6d2-130">Par exemple, « A » est un littéral de type `char`, tandis que 2001 est un littéral de type `int`.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-130">For example, 'A' is a literal of the type `char` and 2001 is a literal of the type `int`.</span></span>  
  
## <a name="initializing-value-types"></a><span data-ttu-id="cc6d2-131">Initialisation des types valeur</span><span class="sxs-lookup"><span data-stu-id="cc6d2-131">Initializing Value Types</span></span>  
 <span data-ttu-id="cc6d2-132">En C#, les variables locales doivent être initialisées avant d’être utilisées.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-132">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="cc6d2-133">Par exemple, vous pouvez déclarer une variable locale sans l’initialiser comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="cc6d2-133">For example, you might declare a local variable without initialization as in the following example:</span></span>  
  
```  
int myInt;  
```  
  
 <span data-ttu-id="cc6d2-134">Vous ne pouvez pas l’utiliser avant de l’avoir initialisée.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-134">You cannot use it before you initialize it.</span></span> <span data-ttu-id="cc6d2-135">Vous pouvez l’initialiser à l’aide de l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="cc6d2-135">You can initialize it using the following statement:</span></span>  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 <span data-ttu-id="cc6d2-136">Cette instruction est équivalente à l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="cc6d2-136">This statement is equivalent to the following statement:</span></span>  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 <span data-ttu-id="cc6d2-137">Bien entendu, vous pouvez intégrer la déclaration et l’initialisation dans une même instruction comme dans les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="cc6d2-137">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>  
  
```  
int myInt = new int();  
```  
  
 <span data-ttu-id="cc6d2-138">– ou –</span><span class="sxs-lookup"><span data-stu-id="cc6d2-138">–or–</span></span>  
  
```  
int myInt = 0;  
```  
  
 <span data-ttu-id="cc6d2-139">L’opérateur [new](../../../csharp/language-reference/keywords/new.md) permet d’appeler le constructeur par défaut du type spécifique et d’assigner la valeur par défaut à la variable.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-139">Using the [new](../../../csharp/language-reference/keywords/new.md) operator calls the default constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="cc6d2-140">Dans l’exemple précédent, le constructeur par défaut a assigné la valeur `0` à `myInt`.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-140">In the preceding example, the default constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="cc6d2-141">Pour plus d’informations sur les valeurs assignées par l’appel des constructeurs par défaut, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="cc6d2-141">For more information about values assigned by calling default constructors, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="cc6d2-142">Avec les types définis par l’utilisateur, l’opérateur [new](../../../csharp/language-reference/keywords/new.md) permet d’appeler le constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-142">With user-defined types, use [new](../../../csharp/language-reference/keywords/new.md) to invoke the default constructor.</span></span> <span data-ttu-id="cc6d2-143">Par exemple, l’instruction suivante appelle le constructeur par défaut du struct `Point` :</span><span class="sxs-lookup"><span data-stu-id="cc6d2-143">For example, the following statement invokes the default constructor of the `Point` struct:</span></span>  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 <span data-ttu-id="cc6d2-144">Après cet appel, le struct est considéré comme définitivement assigné ; autrement dit, tous ses membres sont initialisés avec leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="cc6d2-144">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>  
  
 <span data-ttu-id="cc6d2-145">Pour plus d’informations sur l’opérateur new, consultez [new](../../../csharp/language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="cc6d2-145">For more information about the new operator, see [new](../../../csharp/language-reference/keywords/new.md).</span></span>  
  
 <span data-ttu-id="cc6d2-146">Pour plus d’informations sur la mise en forme de la sortie des types numériques, consultez [Tableau des formats des résultats numériques](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="cc6d2-146">For information about formatting the output of numeric types, see [Formatting Numeric Results Table](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc6d2-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc6d2-147">See Also</span></span>  
 <span data-ttu-id="cc6d2-148">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="cc6d2-148">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="cc6d2-149">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="cc6d2-149">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="cc6d2-150">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="cc6d2-150">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="cc6d2-151">[Types](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="cc6d2-151">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="cc6d2-152">[Tableaux de référence des types](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span><span class="sxs-lookup"><span data-stu-id="cc6d2-152">[Reference Tables for Types](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span></span>  
 [<span data-ttu-id="cc6d2-153">Types référence</span><span class="sxs-lookup"><span data-stu-id="cc6d2-153">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)

