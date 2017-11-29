---
title: "~, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a9b0cabcb101fce8422b1390ec8c4cb3b3849631
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="117e7-102">~, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="117e7-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="117e7-103">L’opérateur `~` effectue une opération de complément de bits sur son opérande, qui a pour effet d’inverser chaque bit.</span><span class="sxs-lookup"><span data-stu-id="117e7-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="117e7-104">Les opérateurs de complément de bits sont prédéfinis pour [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) et [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="117e7-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="117e7-105">Le symbole `~` est également utilisé pour déclarer des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="117e7-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="117e7-106">Pour plus d’informations, consultez [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="117e7-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="117e7-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="117e7-107">Remarks</span></span>  
 <span data-ttu-id="117e7-108">Les types définis par l’utilisateur peuvent surcharger l’opérateur `~`.</span><span class="sxs-lookup"><span data-stu-id="117e7-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="117e7-109">Pour plus d’informations, consultez [operator](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="117e7-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="117e7-110">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="117e7-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="117e7-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="117e7-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="117e7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="117e7-112">See Also</span></span>  
 [<span data-ttu-id="117e7-113">Référence C#</span><span class="sxs-lookup"><span data-stu-id="117e7-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="117e7-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="117e7-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="117e7-115">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="117e7-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="117e7-116">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="117e7-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
