---
title: "^, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
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
ms.openlocfilehash: f081dd2979930404639638179444adc05dd462e1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="97afa-102">^, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="97afa-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="97afa-103">Les opérateurs `^` binaires sont prédéfinis pour les types intégraux et `bool`.</span><span class="sxs-lookup"><span data-stu-id="97afa-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="97afa-104">Pour les types intégraux, `^` effectue l’opération de bits OR exclusif sur les opérandes.</span><span class="sxs-lookup"><span data-stu-id="97afa-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="97afa-105">Pour les opérandes `bool`, `^` effectue l’opération OR exclusif logique sur ses opérandes. En conséquence, le résultat est `true` si et seulement si un seul des opérandes correspond à `true`.</span><span class="sxs-lookup"><span data-stu-id="97afa-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97afa-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="97afa-106">Remarks</span></span>  
 <span data-ttu-id="97afa-107">Les types définis par l’utilisateur peuvent surcharger l’opérateur `^` (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="97afa-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="97afa-108">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="97afa-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97afa-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="97afa-109">Example</span></span>  
 <span data-ttu-id="97afa-110">[!code-cs[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="97afa-110">[!code-cs[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="97afa-111">Le calcul de `0xf8 ^ 0x3f` dans l’exemple précédent effectue une opération de bits OR exclusif des deux valeurs binaires suivantes, qui correspondent aux valeurs hexadécimales F8 et 3F :</span><span class="sxs-lookup"><span data-stu-id="97afa-111">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="97afa-112">Le résultat de l’opération OR exclusif est `1100 0111`, qui correspond à C7 en hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="97afa-112">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97afa-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97afa-113">See Also</span></span>  
 <span data-ttu-id="97afa-114">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="97afa-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="97afa-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="97afa-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="97afa-116">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="97afa-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

