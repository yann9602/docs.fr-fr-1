---
title: "+ , opérateur (Informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b15d5d1a304569b92b2f811a9ea714e4b30d60d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="33662-102">+, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="33662-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="33662-103">L’opérateur `+` peut être utilisé comme opérateur unaire ou opérateur binaire.</span><span class="sxs-lookup"><span data-stu-id="33662-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33662-104">Notes</span><span class="sxs-lookup"><span data-stu-id="33662-104">Remarks</span></span>  
 <span data-ttu-id="33662-105">Les opérateurs `+` sont prédéfinis pour tous les types numériques.</span><span class="sxs-lookup"><span data-stu-id="33662-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="33662-106">Le résultat d’une opération `+` unaire sur un type numérique correspond simplement à la valeur de l’opérande.</span><span class="sxs-lookup"><span data-stu-id="33662-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="33662-107">Les opérateurs `+` binaires sont prédéfinis pour les types numériques et chaîne.</span><span class="sxs-lookup"><span data-stu-id="33662-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="33662-108">Pour les types numériques, + calcule la somme des deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="33662-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="33662-109">Quand les deux opérandes ou l’un d’entre eux sont de type chaîne, + concatène les représentations sous forme de chaîne des opérandes.</span><span class="sxs-lookup"><span data-stu-id="33662-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="33662-110">Les types délégués fournissent aussi un opérateur `+` binaire, qui effectue la concaténation de délégués.</span><span class="sxs-lookup"><span data-stu-id="33662-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="33662-111">Les types définis par l’utilisateur peuvent surcharger les opérateurs `+` unaires et `+` binaires.</span><span class="sxs-lookup"><span data-stu-id="33662-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="33662-112">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="33662-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="33662-113">Pour plus d’informations, consultez [operator (référence C#)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="33662-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33662-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="33662-114">Example</span></span>  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="33662-115">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="33662-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33662-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33662-116">See Also</span></span>  
 [<span data-ttu-id="33662-117">Référence C#</span><span class="sxs-lookup"><span data-stu-id="33662-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="33662-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="33662-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="33662-119">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="33662-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="33662-120">operator (référence C#)</span><span class="sxs-lookup"><span data-stu-id="33662-120">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)
