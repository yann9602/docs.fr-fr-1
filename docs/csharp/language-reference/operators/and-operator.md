---
title: "&amp;, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d92a860df6fcc9acf14aab4ec558556735ac8aac
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="198e4-102">&amp;, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="198e4-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="198e4-103">L’opérateur & peut être utilisé comme opérateur unaire ou comme opérateur binaire.</span><span class="sxs-lookup"><span data-stu-id="198e4-103">The & operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="198e4-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="198e4-104">Remarks</span></span>  
 <span data-ttu-id="198e4-105">L’opérateur & unaire retourne l’adresse de son opérande (requiert un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md)).</span><span class="sxs-lookup"><span data-stu-id="198e4-105">The unary & operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="198e4-106">Les opérateurs & binaires sont prédéfinis pour les types intégraux et `bool`.</span><span class="sxs-lookup"><span data-stu-id="198e4-106">Binary & operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="198e4-107">Pour les types intégraux, & calcule l’opération logique AND au niveau du bit de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="198e4-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="198e4-108">Pour les opérandes `bool`, & calcule l’opération logique AND de ses opérandes ; autrement dit, le résultat est `true` uniquement si ses deux opérandes ont la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="198e4-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="198e4-109">L’opérateur `&` évalue les deux opérateurs indépendamment de la valeur du premier.</span><span class="sxs-lookup"><span data-stu-id="198e4-109">The `&` operator evaluates both operators regardless of the first one's value.</span></span> <span data-ttu-id="198e4-110">Exemple :</span><span class="sxs-lookup"><span data-stu-id="198e4-110">For example:</span></span>  
  
 <span data-ttu-id="198e4-111">[!code-cs[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="198e4-111">[!code-cs[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="198e4-112">Les types définis par l’utilisateur peuvent surcharger l’opérateur `&` binaire (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="198e4-112">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="198e4-113">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="198e4-113">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="198e4-114">Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="198e4-114">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="198e4-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="198e4-115">Example</span></span>  
 <span data-ttu-id="198e4-116">[!code-cs[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="198e4-116">[!code-cs[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198e4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="198e4-117">See Also</span></span>  
 <span data-ttu-id="198e4-118">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="198e4-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="198e4-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="198e4-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="198e4-120">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="198e4-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

