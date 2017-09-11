---
title: "--, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- --_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
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
ms.openlocfilehash: 100e68f3b07164b0cfb398a32f47137f2726943f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="---operator-c-reference"></a><span data-ttu-id="7dc5e-102">--, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7dc5e-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="7dc5e-103">L’opérateur de décrémentation (`--`) décrémente son opérande de 1.</span><span class="sxs-lookup"><span data-stu-id="7dc5e-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="7dc5e-104">L’opérateur de décrémentation peut figurer avant ou après son opérande : `--variable` et `variable--`.</span><span class="sxs-lookup"><span data-stu-id="7dc5e-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="7dc5e-105">La première forme est une opération de décrément préfixé.</span><span class="sxs-lookup"><span data-stu-id="7dc5e-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="7dc5e-106">Le résultat de l’opération est la valeur de l’opérande « après » sa décrémentation.</span><span class="sxs-lookup"><span data-stu-id="7dc5e-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="7dc5e-107">La deuxième forme est une opération de décrément suffixé.</span><span class="sxs-lookup"><span data-stu-id="7dc5e-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="7dc5e-108">Le résultat de l’opération est la valeur de l’opérande « avant » sa décrémentation.</span><span class="sxs-lookup"><span data-stu-id="7dc5e-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dc5e-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="7dc5e-109">Remarks</span></span>  
 <span data-ttu-id="7dc5e-110">Les types numériques et d’énumération ont des opérateurs de décrémentation prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="7dc5e-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="7dc5e-111">Les types définis par l’utilisateur peuvent surcharger l’opérateur `--` (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="7dc5e-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="7dc5e-112">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="7dc5e-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dc5e-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="7dc5e-113">Example</span></span>  
 <span data-ttu-id="7dc5e-114">[!code-cs[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="7dc5e-114">[!code-cs[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dc5e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7dc5e-115">See Also</span></span>  
 <span data-ttu-id="7dc5e-116">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7dc5e-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="7dc5e-117">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7dc5e-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="7dc5e-118">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="7dc5e-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

