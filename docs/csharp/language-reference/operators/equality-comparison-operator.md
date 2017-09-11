---
title: "==, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ==_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
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
ms.openlocfilehash: 0e3ba284bc700e943b108adfec89d14aba41851a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="44e0b-102">==, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="44e0b-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="44e0b-103">Pour les types valeur prédéfinis, l’opérateur d’égalité (`==`) retourne true si les valeurs des opérandes sont égales et `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="44e0b-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="44e0b-104">Pour les types référence autres que [string](../../../csharp/language-reference/keywords/string.md), `==` retourne `true` si ses deux opérandes font référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="44e0b-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="44e0b-105">Pour le type `string`, `==` compare les valeurs des chaînes.</span><span class="sxs-lookup"><span data-stu-id="44e0b-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44e0b-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="44e0b-106">Remarks</span></span>  
 <span data-ttu-id="44e0b-107">Les types valeur définis par l’utilisateur peuvent surcharger l’opérateur `==` (consultez [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="44e0b-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="44e0b-108">Il en va de même pour les types référence définis par l’utilisateur, même si par défaut `==` se comporte comme indiqué ci-dessus pour les types référence prédéfinis et définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="44e0b-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="44e0b-109">Si `==` est surchargé, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) doit l’être aussi.</span><span class="sxs-lookup"><span data-stu-id="44e0b-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="44e0b-110">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="44e0b-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44e0b-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="44e0b-111">Example</span></span>  
 <span data-ttu-id="44e0b-112">[!code-cs[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="44e0b-112">[!code-cs[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e0b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44e0b-113">See Also</span></span>  
 <span data-ttu-id="44e0b-114">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="44e0b-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="44e0b-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="44e0b-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="44e0b-116">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="44e0b-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

