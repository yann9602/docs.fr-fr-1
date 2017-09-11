---
title: "=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
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
ms.openlocfilehash: e40b2f221717461443a5d0247b3401eb527a7b5a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="240e4-102">=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="240e4-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="240e4-103">L’opérateur d’assignation (`=`) stocke la valeur de l’opérande de droite dans l’emplacement de stockage, la propriété ou l’indexeur indiqué par l’opérande de gauche et retourne la valeur comme résultat.</span><span class="sxs-lookup"><span data-stu-id="240e4-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="240e4-104">Les opérandes doivent être du même type (ou l’opérande de droite doit être implicitement convertible en type de l’opérande de gauche).</span><span class="sxs-lookup"><span data-stu-id="240e4-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="240e4-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="240e4-105">Remarks</span></span>  
 <span data-ttu-id="240e4-106">L’opérateur d’assignation ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="240e4-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="240e4-107">Toutefois, vous pouvez définir des opérateurs de conversion implicites pour un type, qui vous permettent d’utiliser l’opérateur d’assignation avec ces types.</span><span class="sxs-lookup"><span data-stu-id="240e4-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="240e4-108">Pour plus d’informations, consultez [Utilisation d’opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="240e4-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="240e4-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="240e4-109">Example</span></span>  
 <span data-ttu-id="240e4-110">[!code-cs[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="240e4-110">[!code-cs[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="240e4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="240e4-111">See Also</span></span>  
 <span data-ttu-id="240e4-112">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="240e4-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="240e4-113">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="240e4-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="240e4-114">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="240e4-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

