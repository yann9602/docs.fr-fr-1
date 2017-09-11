---
title: "&lt;&lt;, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <<_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
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
ms.openlocfilehash: 4e6ad17232ec4eb087ca300342331af6a30789b1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="2b952-102">&lt;&lt;, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="2b952-102">&lt;&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="2b952-103">L’opérateur de décalage vers la gauche (`<<`) décale son premier opérande vers la gauche du nombre de bits spécifié par son deuxième opérande.</span><span class="sxs-lookup"><span data-stu-id="2b952-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="2b952-104">Le deuxième opérande doit être de type [int](../../../csharp/language-reference/keywords/int.md) ou d’un type pour lequel une conversion numérique implicite vers `int` est prédéfinie.</span><span class="sxs-lookup"><span data-stu-id="2b952-104">The type of the second operand must be an [int](../../../csharp/language-reference/keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b952-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="2b952-105">Remarks</span></span>  
 <span data-ttu-id="2b952-106">Si le premier opérande est de type [int](../../../csharp/language-reference/keywords/int.md) ou [uint](../../../csharp/language-reference/keywords/uint.md) (quantité de 32 bits), la valeur du décalage est donnée par les cinq bits de poids faible du second opérande.</span><span class="sxs-lookup"><span data-stu-id="2b952-106">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="2b952-107">Autrement dit, la valeur réelle du décalage est comprise entre 0 et 31 bits.</span><span class="sxs-lookup"><span data-stu-id="2b952-107">That is, the actual shift count is 0 to 31 bits.</span></span>  
  
 <span data-ttu-id="2b952-108">Si le premier opérande est de type [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) (quantité de 64 bits), la valeur du décalage est donnée par les six bits de poids faible du second opérande.</span><span class="sxs-lookup"><span data-stu-id="2b952-108">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="2b952-109">Autrement dit, la valeur réelle du décalage est comprise entre 0 et 63 bits.</span><span class="sxs-lookup"><span data-stu-id="2b952-109">That is, the actual shift count is 0 to 63 bits.</span></span>  
  
 <span data-ttu-id="2b952-110">Les bits de poids fort qui ne se trouvent pas dans la plage du type du premier opérande après le décalage sont ignorés, et les bits vides de poids faible sont remplis de zéros.</span><span class="sxs-lookup"><span data-stu-id="2b952-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="2b952-111">Les opérations de décalage ne provoquent jamais de dépassements de capacité.</span><span class="sxs-lookup"><span data-stu-id="2b952-111">Shift operations never cause overflows.</span></span>  
  
 <span data-ttu-id="2b952-112">Les types définis par l’utilisateur peuvent surcharger l’opérateur `<<` (consultez [operator](../../../csharp/language-reference/keywords/operator.md)) ; le type du premier opérande doit être le type défini par l’utilisateur, et le type du second opérande doit être `int`.</span><span class="sxs-lookup"><span data-stu-id="2b952-112">User-defined types can overload the `<<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="2b952-113">Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="2b952-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b952-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="2b952-114">Example</span></span>  
 <span data-ttu-id="2b952-115">[!code-cs[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2b952-115">[!code-cs[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]</span></span>  
  
## <a name="comments"></a><span data-ttu-id="2b952-116">Commentaires</span><span class="sxs-lookup"><span data-stu-id="2b952-116">Comments</span></span>  
 <span data-ttu-id="2b952-117">Notez que `i<<1` et `i<<33` donnent le même résultat, car 1 et 33 possèdent les cinq mêmes bits de poids faible.</span><span class="sxs-lookup"><span data-stu-id="2b952-117">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b952-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b952-118">See Also</span></span>  
 <span data-ttu-id="2b952-119">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="2b952-119">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="2b952-120">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2b952-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="2b952-121">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="2b952-121">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

