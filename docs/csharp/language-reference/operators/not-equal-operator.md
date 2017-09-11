---
title: "!=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '!=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
caps.latest.revision: 14
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
ms.openlocfilehash: 49c5c9668c6b1169220ee4fa0babf167292a9813
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="3fd55-102">!=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3fd55-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="3fd55-103">L’opérateur d’inégalité (`!=`) retourne la valeur false si ses opérandes sont égaux et la valeur true dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="3fd55-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="3fd55-104">Les opérateurs d’inégalité sont prédéfinis pour tous les types, dont string et object.</span><span class="sxs-lookup"><span data-stu-id="3fd55-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="3fd55-105">Les types définis par l’utilisateur peuvent surcharger l’opérateur `!=`.</span><span class="sxs-lookup"><span data-stu-id="3fd55-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fd55-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="3fd55-106">Remarks</span></span>  
 <span data-ttu-id="3fd55-107">Pour les types valeur prédéfinis, l’opérateur d’inégalité (`!=`) retourne la valeur true si les valeurs de ses opérandes sont différentes et la valeur false dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="3fd55-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="3fd55-108">Pour les types référence autres que `string`, `!=` retourne la valeur true si ses deux opérandes font référence à des objets différents.</span><span class="sxs-lookup"><span data-stu-id="3fd55-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="3fd55-109">Pour le type `string`, `!=` compare les valeurs des chaînes.</span><span class="sxs-lookup"><span data-stu-id="3fd55-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="3fd55-110">Les types valeur définis par l’utilisateur peuvent surcharger l’opérateur `!=` (consultez [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="3fd55-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="3fd55-111">Il en va de même pour les types référence définis par l’utilisateur, même si par défaut `!=` se comporte comme indiqué ci-dessus pour les types référence prédéfinis et définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3fd55-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="3fd55-112">Si `!=` est surchargé, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) doit aussi l’être.</span><span class="sxs-lookup"><span data-stu-id="3fd55-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="3fd55-113">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="3fd55-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fd55-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="3fd55-114">Example</span></span>  
 <span data-ttu-id="3fd55-115">[!code-cs[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3fd55-115">[!code-cs[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd55-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fd55-116">See Also</span></span>  
 <span data-ttu-id="3fd55-117">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="3fd55-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="3fd55-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3fd55-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="3fd55-119">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="3fd55-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

