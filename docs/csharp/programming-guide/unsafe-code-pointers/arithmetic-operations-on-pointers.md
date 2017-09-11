---
title: "Opérations arithmétiques sur les pointeurs (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
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
ms.openlocfilehash: d40d44f8be590a909ff059b0fa84efb598fcf263
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="4e068-102">Opérations arithmétiques sur les pointeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="4e068-102">Arithmetic Operations on Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="4e068-103">Cette rubrique décrit l’utilisation des opérateurs arithmétiques `+` et **-** pour manipuler les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="4e068-103">This topic discusses using the arithmetic operators `+` and **-** to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e068-104">Vous ne pouvez pas effectuer d’opérations arithmétiques sur les pointeurs void.</span><span class="sxs-lookup"><span data-stu-id="4e068-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="4e068-105">Ajout et soustraction de valeurs numériques dans les pointeurs</span><span class="sxs-lookup"><span data-stu-id="4e068-105">Adding and Subtracting Numeric Values to or From Pointers</span></span>  
 <span data-ttu-id="4e068-106">Vous pouvez ajouter une valeur `n` de type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) à un pointeur `p` de n’importe quel type à l’exception de `void*`.</span><span class="sxs-lookup"><span data-stu-id="4e068-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.</span></span> <span data-ttu-id="4e068-107">Le pointeur `p+n` est le résultat de l’ajout de `n * sizeof(p) to the address of p`.</span><span class="sxs-lookup"><span data-stu-id="4e068-107">The result `p+n` is the pointer resulting from adding `n * sizeof(p) to the address of p`.</span></span> <span data-ttu-id="4e068-108">De la même façon, `p-n` est le pointeur qui résulte de la soustraction de `n * sizeof(p)` de l’adresse de `p`.</span><span class="sxs-lookup"><span data-stu-id="4e068-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(p)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="4e068-109">Soustraction de pointeurs</span><span class="sxs-lookup"><span data-stu-id="4e068-109">Subtracting Pointers</span></span>  
 <span data-ttu-id="4e068-110">Vous pouvez également soustraire des pointeurs du même type.</span><span class="sxs-lookup"><span data-stu-id="4e068-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="4e068-111">Le résultat est toujours du type `long`.</span><span class="sxs-lookup"><span data-stu-id="4e068-111">The result is always of the type `long`.</span></span> <span data-ttu-id="4e068-112">Par exemple, si `p1` et `p2` sont des pointeurs du type `pointer-type*`, l’expression `p1-p2` produit le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="4e068-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 <span data-ttu-id="4e068-113">Aucune exception n’est générée si l’opération arithmétique produit un dépassement de capacité sur le domaine du pointeur, et le résultat dépend de l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="4e068-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e068-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e068-114">Example</span></span>  
 <span data-ttu-id="4e068-115">[!code-cs[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4e068-115">[!code-cs[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]</span></span>  
  
 <span data-ttu-id="4e068-116">[!code-cs[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4e068-116">[!code-cs[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4e068-117">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4e068-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e068-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e068-118">See Also</span></span>  
 <span data-ttu-id="4e068-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4e068-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4e068-120">[Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="4e068-120">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="4e068-121">[Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="4e068-121">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="4e068-122">[Opérateurs C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="4e068-122">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="4e068-123">[Manipulation de pointeurs](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md) </span><span class="sxs-lookup"><span data-stu-id="4e068-123">[Manipulating Pointers](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md) </span></span>  
 <span data-ttu-id="4e068-124">[Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="4e068-124">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="4e068-125">[Types](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="4e068-125">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="4e068-126">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="4e068-126">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="4e068-127">[fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4e068-127">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="4e068-128">stackalloc</span><span class="sxs-lookup"><span data-stu-id="4e068-128">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

