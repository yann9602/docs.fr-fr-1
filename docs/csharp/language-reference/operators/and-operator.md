---
title: "&amp;, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eceee8e01ba46f65c6b182a40d14e62aaba5dd53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="6f0ba-102">&amp;, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="6f0ba-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="6f0ba-103">L’opérateur & peut être utilisé comme opérateur unaire ou comme opérateur binaire.</span><span class="sxs-lookup"><span data-stu-id="6f0ba-103">The & operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f0ba-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="6f0ba-104">Remarks</span></span>  
 <span data-ttu-id="6f0ba-105">L’opérateur & unaire retourne l’adresse de son opérande (requiert un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md)).</span><span class="sxs-lookup"><span data-stu-id="6f0ba-105">The unary & operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="6f0ba-106">Les opérateurs & binaires sont prédéfinis pour les types intégraux et `bool`.</span><span class="sxs-lookup"><span data-stu-id="6f0ba-106">Binary & operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="6f0ba-107">Pour les types intégraux, & calcule l’opération logique AND au niveau du bit de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="6f0ba-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="6f0ba-108">Pour les opérandes `bool`, & calcule l’opération logique AND de ses opérandes ; autrement dit, le résultat est `true` uniquement si ses deux opérandes ont la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="6f0ba-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="6f0ba-109">L’opérateur `&` évalue les deux opérateurs indépendamment de la valeur du premier.</span><span class="sxs-lookup"><span data-stu-id="6f0ba-109">The `&` operator evaluates both operators regardless of the first one's value.</span></span> <span data-ttu-id="6f0ba-110">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6f0ba-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="6f0ba-111">Les types définis par l’utilisateur peuvent surcharger l’opérateur `&` binaire (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="6f0ba-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="6f0ba-112">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="6f0ba-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="6f0ba-113">Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="6f0ba-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f0ba-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f0ba-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6f0ba-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f0ba-115">See Also</span></span>  
 [<span data-ttu-id="6f0ba-116">Référence C#</span><span class="sxs-lookup"><span data-stu-id="6f0ba-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6f0ba-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6f0ba-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6f0ba-118">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="6f0ba-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
