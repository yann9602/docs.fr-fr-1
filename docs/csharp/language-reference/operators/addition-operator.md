---
title: "+ , opérateur (Informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
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
ms.openlocfilehash: 5455375148f1924c7fe1cdb10e7924abb83a1565
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="55580-102">+, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="55580-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="55580-103">L’opérateur `+` peut être utilisé comme opérateur unaire ou opérateur binaire.</span><span class="sxs-lookup"><span data-stu-id="55580-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55580-104">Notes</span><span class="sxs-lookup"><span data-stu-id="55580-104">Remarks</span></span>  
 <span data-ttu-id="55580-105">Les opérateurs `+` sont prédéfinis pour tous les types numériques.</span><span class="sxs-lookup"><span data-stu-id="55580-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="55580-106">Le résultat d’une opération `+` unaire sur un type numérique correspond simplement à la valeur de l’opérande.</span><span class="sxs-lookup"><span data-stu-id="55580-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="55580-107">Les opérateurs `+` binaires sont prédéfinis pour les types numériques et chaîne.</span><span class="sxs-lookup"><span data-stu-id="55580-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="55580-108">Pour les types numériques, + calcule la somme des deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="55580-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="55580-109">Quand les deux opérandes ou l’un d’entre eux sont de type chaîne, + concatène les représentations sous forme de chaîne des opérandes.</span><span class="sxs-lookup"><span data-stu-id="55580-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="55580-110">Les types délégués fournissent aussi un opérateur `+` binaire, qui effectue la concaténation de délégués.</span><span class="sxs-lookup"><span data-stu-id="55580-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="55580-111">Les types définis par l’utilisateur peuvent surcharger les opérateurs `+` unaires et `+` binaires.</span><span class="sxs-lookup"><span data-stu-id="55580-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="55580-112">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="55580-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="55580-113">Pour plus d’informations, consultez [operator (référence C#)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="55580-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55580-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="55580-114">Example</span></span>  
 <span data-ttu-id="55580-115">[!code-cs[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="55580-115">[!code-cs[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="55580-116">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="55580-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="55580-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55580-117">See Also</span></span>  
 <span data-ttu-id="55580-118">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="55580-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="55580-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="55580-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="55580-120">[Opérateurs C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="55580-120">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 [<span data-ttu-id="55580-121">operator (référence C#)</span><span class="sxs-lookup"><span data-stu-id="55580-121">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)

