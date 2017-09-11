---
title: Types pointeur (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: 19
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
ms.openlocfilehash: 1a4ebc69762f18dc630100b544c18df0f43734ac
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="abfb4-102">Types pointeur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="abfb4-102">Pointer types (C# Programming Guide)</span></span>
<span data-ttu-id="abfb4-103">Dans un contexte unsafe, un type peut être un type pointeur, un type valeur ou un type référence.</span><span class="sxs-lookup"><span data-stu-id="abfb4-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="abfb4-104">La déclaration d'un type pointeur peut prendre l'une des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="abfb4-104">A pointer type declaration takes one of the following forms:</span></span>  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 <span data-ttu-id="abfb4-105">Chacun des types suivants peut être un type pointeur :</span><span class="sxs-lookup"><span data-stu-id="abfb4-105">Any of the following types may be a pointer type:</span></span>  
  
-   <span data-ttu-id="abfb4-106">[sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md) ou [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="abfb4-106">[sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md), or [bool](../../../csharp/language-reference/keywords/bool.md).</span></span>  
  
-   <span data-ttu-id="abfb4-107">Tout type [enum](../../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="abfb4-107">Any [enum](../../../csharp/language-reference/keywords/enum.md) type.</span></span>  
  
-   <span data-ttu-id="abfb4-108">Tout type pointeur.</span><span class="sxs-lookup"><span data-stu-id="abfb4-108">Any pointer type.</span></span>  
  
-   <span data-ttu-id="abfb4-109">Tout type struct défini par l'utilisateur qui contient des champs de types unmanaged uniquement.</span><span class="sxs-lookup"><span data-stu-id="abfb4-109">Any user-defined struct type that contains fields of unmanaged types only.</span></span>  
  
 <span data-ttu-id="abfb4-110">Les types pointeur n’héritent pas de [object](../../../csharp/language-reference/keywords/object.md), et aucune conversion n’est possible entre les types pointeur et `object`.</span><span class="sxs-lookup"><span data-stu-id="abfb4-110">Pointer types do not inherit from [object](../../../csharp/language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="abfb4-111">Par ailleurs, le boxing et l'unboxing ne prennent pas en charge les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="abfb4-111">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="abfb4-112">Cependant, vous pouvez effectuer des conversions entre différents types pointeur ainsi qu'entre des types pointeur et des types intégraux.</span><span class="sxs-lookup"><span data-stu-id="abfb4-112">However, you can convert between different pointer types and between pointer types and integral types.</span></span>  
  
 <span data-ttu-id="abfb4-113">Lorsque vous déclarez plusieurs pointeurs dans la même déclaration, l'astérisque (*) est écrit conjointement au type sous-jacent uniquement, il n'est pas utilisé en tant que préfixe de chaque nom de pointeur.</span><span class="sxs-lookup"><span data-stu-id="abfb4-113">When you declare multiple pointers in the same declaration, the asterisk (*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="abfb4-114">Exemple :</span><span class="sxs-lookup"><span data-stu-id="abfb4-114">For example:</span></span>  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 <span data-ttu-id="abfb4-115">Un pointeur ne peut pas pointer vers une référence ou vers un [struct](../../../csharp/language-reference/keywords/struct.md) qui contient des références, car une référence d’objet peut être collectée par le récupérateur de mémoire, même si un pointeur pointe vers elle.</span><span class="sxs-lookup"><span data-stu-id="abfb4-115">A pointer cannot point to a reference or to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="abfb4-116">Le récupérateur de mémoire ne se préoccupe pas de savoir si un objet est pointé par des types pointeur.</span><span class="sxs-lookup"><span data-stu-id="abfb4-116">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>  
  
 <span data-ttu-id="abfb4-117">La valeur de la variable pointeur de type `myType*` est l'adresse d'une variable de type `myType`.</span><span class="sxs-lookup"><span data-stu-id="abfb4-117">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="abfb4-118">Les éléments suivants sont des exemples de déclarations de type pointeur :</span><span class="sxs-lookup"><span data-stu-id="abfb4-118">The following are examples of pointer type declarations:</span></span>  
  
|<span data-ttu-id="abfb4-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="abfb4-119">Example</span></span>|<span data-ttu-id="abfb4-120">Description</span><span class="sxs-lookup"><span data-stu-id="abfb4-120">Description</span></span>|  
|-------------|-----------------|  
|`int* p`|<span data-ttu-id="abfb4-121">`p` est un pointeur vers un entier.</span><span class="sxs-lookup"><span data-stu-id="abfb4-121">`p` is a pointer to an integer.</span></span>|  
|`int** p`|<span data-ttu-id="abfb4-122">`p` est un pointeur vers un pointeur vers un entier.</span><span class="sxs-lookup"><span data-stu-id="abfb4-122">`p` is a pointer to a pointer to an integer.</span></span>|  
|`int*[] p`|<span data-ttu-id="abfb4-123">`p` est un tableau unidimensionnel de pointeurs vers des entiers.</span><span class="sxs-lookup"><span data-stu-id="abfb4-123">`p` is a single-dimensional array of pointers to integers.</span></span>|  
|`char* p`|<span data-ttu-id="abfb4-124">`p` est un pointeur vers un caractère.</span><span class="sxs-lookup"><span data-stu-id="abfb4-124">`p` is a pointer to a char.</span></span>|  
|`void* p`|<span data-ttu-id="abfb4-125">`p` est un pointeur vers un type inconnu.</span><span class="sxs-lookup"><span data-stu-id="abfb4-125">`p` is a pointer to an unknown type.</span></span>|  
  
 <span data-ttu-id="abfb4-126">L'opérateur d'indirection de pointeur * peut être utilisé pour accéder au contenu à l'emplacement vers lequel pointe la variable pointeur.</span><span class="sxs-lookup"><span data-stu-id="abfb4-126">The pointer indirection operator * can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="abfb4-127">Observez par exemple la déclaration suivante :</span><span class="sxs-lookup"><span data-stu-id="abfb4-127">For example, consider the following declaration:</span></span>  
  
```  
int* myVariable;  
```  
  
 <span data-ttu-id="abfb4-128">L'expression `*myVariable` désigne la variable `int` trouvée à l'adresse contenue dans `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="abfb4-128">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>  
  
 <span data-ttu-id="abfb4-129">Plusieurs exemples de pointeurs sont présentés dans les rubriques [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md) et [Conversions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="abfb4-129">There are several examples of pointers in the topics [fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span>  <span data-ttu-id="abfb4-130">L'exemple suivant montre la nécessité d'un pointeur intérieur pour le mot clé `unsafe` et les instructions `fixed`, et comment l'incrémenter.</span><span class="sxs-lookup"><span data-stu-id="abfb4-130">The following example shows the need for the `unsafe` keyword and the `fixed` statement, and how to increment an interior pointer.</span></span>  <span data-ttu-id="abfb4-131">Vous pouvez coller ce code dans la fonction Main d'une application console pour l'exécuter.</span><span class="sxs-lookup"><span data-stu-id="abfb4-131">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="abfb4-132">(N’oubliez pas d’autoriser le code unsafe dans le **Concepteur de projet**. Pour cela, choisissez **Projet**, **Propriétés** dans la barre de menus, puis sélectionnez **Autoriser le code unsafe** dans l’onglet **Générer**.)</span><span class="sxs-lookup"><span data-stu-id="abfb4-132">(Remember to enable unsafe code in the **Project Designer**; choose **Project**, **Properties** on the menu bar, and then select **Allow unsafe code** in the **Build** tab.)</span></span>  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
```  
  
 <span data-ttu-id="abfb4-133">L'opérateur d'indirection ne peut pas être appliqué à un pointeur de type `void*`.</span><span class="sxs-lookup"><span data-stu-id="abfb4-133">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="abfb4-134">Toutefois, vous pouvez utiliser un cast pour convertir un pointeur void en n'importe quel autre type pointeur, et inversement.</span><span class="sxs-lookup"><span data-stu-id="abfb4-134">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>  
  
 <span data-ttu-id="abfb4-135">Un pointeur peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="abfb4-135">A pointer can be `null`.</span></span> <span data-ttu-id="abfb4-136">Le fait d'appliquer un opérateur d'indirection à un pointeur Null donne lieu à un comportement défini par l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="abfb4-136">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>  
  
 <span data-ttu-id="abfb4-137">Sachez que le passage de pointeurs entre méthodes peut engendrer un comportement non défini.</span><span class="sxs-lookup"><span data-stu-id="abfb4-137">Be aware that passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="abfb4-138">Par exemple, retourner un pointeur à une variable locale via un paramètre Out ou Ref ou en tant que résultat de fonction.</span><span class="sxs-lookup"><span data-stu-id="abfb4-138">Examples are returning a pointer to a local variable through an Out or Ref parameter or as the function result.</span></span> <span data-ttu-id="abfb4-139">Si le pointeur a été défini dans un bloc fixed, la variable vers laquelle il pointe peut ne plus être fixed.</span><span class="sxs-lookup"><span data-stu-id="abfb4-139">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>  
  
 <span data-ttu-id="abfb4-140">Le tableau suivant répertorie les opérateurs et les instructions qui peuvent fonctionner sur des pointeurs dans un contexte unsafe :</span><span class="sxs-lookup"><span data-stu-id="abfb4-140">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>  
  
|<span data-ttu-id="abfb4-141">Opérateur/Instruction</span><span class="sxs-lookup"><span data-stu-id="abfb4-141">Operator/Statement</span></span>|<span data-ttu-id="abfb4-142">Utilisation</span><span class="sxs-lookup"><span data-stu-id="abfb4-142">Use</span></span>|  
|-------------------------|---------|  
|*|<span data-ttu-id="abfb4-143">Exécute l'indirection de pointeur.</span><span class="sxs-lookup"><span data-stu-id="abfb4-143">Performs pointer indirection.</span></span>|  
|->|<span data-ttu-id="abfb4-144">Accède à un membre d'un struct via un pointeur.</span><span class="sxs-lookup"><span data-stu-id="abfb4-144">Accesses a member of a struct through a pointer.</span></span>|  
|<span data-ttu-id="abfb4-145">[]</span><span class="sxs-lookup"><span data-stu-id="abfb4-145">[]</span></span>|<span data-ttu-id="abfb4-146">Indexe un pointeur.</span><span class="sxs-lookup"><span data-stu-id="abfb4-146">Indexes a pointer.</span></span>|  
|`&`|<span data-ttu-id="abfb4-147">Obtient l'adresse d'une variable.</span><span class="sxs-lookup"><span data-stu-id="abfb4-147">Obtains the address of a variable.</span></span>|  
|<span data-ttu-id="abfb4-148">++ et --</span><span class="sxs-lookup"><span data-stu-id="abfb4-148">++ and --</span></span>|<span data-ttu-id="abfb4-149">Incrémente et décrémente les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="abfb4-149">Increments and decrements pointers.</span></span>|  
|<span data-ttu-id="abfb4-150">+ et -</span><span class="sxs-lookup"><span data-stu-id="abfb4-150">+ and -</span></span>|<span data-ttu-id="abfb4-151">Exécute des opérations arithmétiques sur les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="abfb4-151">Performs pointer arithmetic.</span></span>|  
|<span data-ttu-id="abfb4-152">==, !=, \<, >, \<= et >=</span><span class="sxs-lookup"><span data-stu-id="abfb4-152">==, !=, \<, >, \<=, and >=</span></span>|<span data-ttu-id="abfb4-153">Compare des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="abfb4-153">Compares pointers.</span></span>|  
|`stackalloc`|<span data-ttu-id="abfb4-154">Alloue de la mémoire sur la pile.</span><span class="sxs-lookup"><span data-stu-id="abfb4-154">Allocates memory on the stack.</span></span>|  
|<span data-ttu-id="abfb4-155">Instruction `fixed`</span><span class="sxs-lookup"><span data-stu-id="abfb4-155">`fixed` statement</span></span>|<span data-ttu-id="abfb4-156">Résout temporairement une variable afin de pouvoir rechercher son adresse.</span><span class="sxs-lookup"><span data-stu-id="abfb4-156">Temporarily fixes a variable so that its address may be found.</span></span>|  
  
## <a name="c-language-specification"></a><span data-ttu-id="abfb4-157">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="abfb4-157">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="abfb4-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abfb4-158">See Also</span></span>  
 <span data-ttu-id="abfb4-159">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="abfb4-159">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="abfb4-160">[Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="abfb4-160">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="abfb4-161">[Conversions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="abfb4-161">[Pointer Conversions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md) </span></span>  
 <span data-ttu-id="abfb4-162">[Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="abfb4-162">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="abfb4-163">[Types](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="abfb4-163">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="abfb4-164">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="abfb4-164">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="abfb4-165">[fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="abfb4-165">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 <span data-ttu-id="abfb4-166">[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) </span><span class="sxs-lookup"><span data-stu-id="abfb4-166">[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) </span></span>  
 [<span data-ttu-id="abfb4-167">Conversion boxing et unboxing</span><span class="sxs-lookup"><span data-stu-id="abfb4-167">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)

