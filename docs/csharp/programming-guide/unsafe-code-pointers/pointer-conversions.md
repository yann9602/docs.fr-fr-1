---
title: Conversions de pointeur (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 17
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
ms.openlocfilehash: e415d892d979e2bdcd648256150e2a96b1772ce4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="0b286-102">Conversions de pointeur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="0b286-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="0b286-103">Le tableau suivant présente les conversions de pointeur implicites prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="0b286-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="0b286-104">Les conversions implicites peuvent se produire dans de nombreuses situations, comme les appels de méthode et les instructions d’assignation.</span><span class="sxs-lookup"><span data-stu-id="0b286-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="0b286-105">Conversions de pointeur implicites</span><span class="sxs-lookup"><span data-stu-id="0b286-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="0b286-106">De</span><span class="sxs-lookup"><span data-stu-id="0b286-106">From</span></span>|<span data-ttu-id="0b286-107">Vers</span><span class="sxs-lookup"><span data-stu-id="0b286-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="0b286-108">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="0b286-108">Any pointer type</span></span>|<span data-ttu-id="0b286-109">void*</span><span class="sxs-lookup"><span data-stu-id="0b286-109">void*</span></span>|  
|<span data-ttu-id="0b286-110">null</span><span class="sxs-lookup"><span data-stu-id="0b286-110">null</span></span>|<span data-ttu-id="0b286-111">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="0b286-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="0b286-112">La conversion de pointeur explicite permet d’effectuer des conversions, pour lesquelles il n’existe pas de conversion implicite, à l’aide d’une expression de cast.</span><span class="sxs-lookup"><span data-stu-id="0b286-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="0b286-113">Le tableau suivant liste ces conversions.</span><span class="sxs-lookup"><span data-stu-id="0b286-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="0b286-114">Conversions de pointeur explicites</span><span class="sxs-lookup"><span data-stu-id="0b286-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="0b286-115">De</span><span class="sxs-lookup"><span data-stu-id="0b286-115">From</span></span>|<span data-ttu-id="0b286-116">Vers</span><span class="sxs-lookup"><span data-stu-id="0b286-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="0b286-117">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="0b286-117">Any pointer type</span></span>|<span data-ttu-id="0b286-118">Tout autre type pointeur</span><span class="sxs-lookup"><span data-stu-id="0b286-118">Any other pointer type</span></span>|  
|<span data-ttu-id="0b286-119">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="0b286-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="0b286-120">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="0b286-120">Any pointer type</span></span>|  
|<span data-ttu-id="0b286-121">Tout type pointeur</span><span class="sxs-lookup"><span data-stu-id="0b286-121">Any pointer type</span></span>|<span data-ttu-id="0b286-122">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="0b286-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0b286-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="0b286-123">Example</span></span>  
 <span data-ttu-id="0b286-124">Dans l’exemple suivant, un pointeur vers `int` est converti en pointeur vers `byte`.</span><span class="sxs-lookup"><span data-stu-id="0b286-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="0b286-125">Notez que le pointeur pointe vers l’octet traité le plus faible de la variable.</span><span class="sxs-lookup"><span data-stu-id="0b286-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="0b286-126">Quand vous incrémentez successivement le résultat, jusqu’à la taille de `int` (4 octets), vous pouvez afficher les octets restants de la variable.</span><span class="sxs-lookup"><span data-stu-id="0b286-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 <span data-ttu-id="0b286-127">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0b286-127">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]</span></span>  
  
 <span data-ttu-id="0b286-128">[!code-cs[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="0b286-128">[!code-cs[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b286-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b286-129">See Also</span></span>  
 <span data-ttu-id="0b286-130">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0b286-130">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="0b286-131">[Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="0b286-131">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="0b286-132">[Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="0b286-132">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="0b286-133">[Types](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="0b286-133">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="0b286-134">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="0b286-134">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="0b286-135">[fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0b286-135">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="0b286-136">stackalloc</span><span class="sxs-lookup"><span data-stu-id="0b286-136">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

