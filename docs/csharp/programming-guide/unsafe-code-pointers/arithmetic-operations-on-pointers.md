---
title: "Opérations arithmétiques sur les pointeurs (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 54c439aab8b6cd34a796db8d31f9eabeefddf9f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="f20b4-102">Opérations arithmétiques sur les pointeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f20b4-102">Arithmetic Operations on Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="f20b4-103">Cette rubrique décrit l’utilisation des opérateurs arithmétiques `+` et **-** pour manipuler les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="f20b4-103">This topic discusses using the arithmetic operators `+` and **-** to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f20b4-104">Vous ne pouvez pas effectuer d’opérations arithmétiques sur les pointeurs void.</span><span class="sxs-lookup"><span data-stu-id="f20b4-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="f20b4-105">Ajout et soustraction de valeurs numériques dans les pointeurs</span><span class="sxs-lookup"><span data-stu-id="f20b4-105">Adding and Subtracting Numeric Values to or From Pointers</span></span>  
 <span data-ttu-id="f20b4-106">Vous pouvez ajouter une valeur `n` de type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) à un pointeur `p` de n’importe quel type à l’exception de `void*`.</span><span class="sxs-lookup"><span data-stu-id="f20b4-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.</span></span> <span data-ttu-id="f20b4-107">Le pointeur `p+n` est le résultat de l’ajout de `n * sizeof(p) to the address of p`.</span><span class="sxs-lookup"><span data-stu-id="f20b4-107">The result `p+n` is the pointer resulting from adding `n * sizeof(p) to the address of p`.</span></span> <span data-ttu-id="f20b4-108">De la même façon, `p-n` est le pointeur qui résulte de la soustraction de `n * sizeof(p)` de l’adresse de `p`.</span><span class="sxs-lookup"><span data-stu-id="f20b4-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(p)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="f20b4-109">Soustraction de pointeurs</span><span class="sxs-lookup"><span data-stu-id="f20b4-109">Subtracting Pointers</span></span>  
 <span data-ttu-id="f20b4-110">Vous pouvez également soustraire des pointeurs du même type.</span><span class="sxs-lookup"><span data-stu-id="f20b4-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="f20b4-111">Le résultat est toujours du type `long`.</span><span class="sxs-lookup"><span data-stu-id="f20b4-111">The result is always of the type `long`.</span></span> <span data-ttu-id="f20b4-112">Par exemple, si `p1` et `p2` sont des pointeurs du type `pointer-type*`, l’expression `p1-p2` produit le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="f20b4-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 <span data-ttu-id="f20b4-113">Aucune exception n’est générée si l’opération arithmétique produit un dépassement de capacité sur le domaine du pointeur, et le résultat dépend de l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="f20b4-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f20b4-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="f20b4-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f20b4-115">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f20b4-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f20b4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f20b4-116">See Also</span></span>  
 [<span data-ttu-id="f20b4-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f20b4-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f20b4-118">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="f20b4-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="f20b4-119">Expressions de pointeur</span><span class="sxs-lookup"><span data-stu-id="f20b4-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="f20b4-120">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="f20b4-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="f20b4-121">Manipulation de pointeurs</span><span class="sxs-lookup"><span data-stu-id="f20b4-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="f20b4-122">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="f20b4-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="f20b4-123">Types</span><span class="sxs-lookup"><span data-stu-id="f20b4-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="f20b4-124">unsafe</span><span class="sxs-lookup"><span data-stu-id="f20b4-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="f20b4-125">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="f20b4-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="f20b4-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f20b4-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
