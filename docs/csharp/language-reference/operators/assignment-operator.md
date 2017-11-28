---
title: "=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: =_CSharpKeyword
helpviewer_keywords: = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c7188abe54cb69678720b4dbbf4dbdea1be4abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="966c3-102">=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="966c3-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="966c3-103">L’opérateur d’assignation (`=`) stocke la valeur de l’opérande de droite dans l’emplacement de stockage, la propriété ou l’indexeur indiqué par l’opérande de gauche et retourne la valeur comme résultat.</span><span class="sxs-lookup"><span data-stu-id="966c3-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="966c3-104">Les opérandes doivent être du même type (ou l’opérande de droite doit être implicitement convertible en type de l’opérande de gauche).</span><span class="sxs-lookup"><span data-stu-id="966c3-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="966c3-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="966c3-105">Remarks</span></span>  
 <span data-ttu-id="966c3-106">L’opérateur d’assignation ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="966c3-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="966c3-107">Toutefois, vous pouvez définir des opérateurs de conversion implicites pour un type, qui vous permettent d’utiliser l’opérateur d’assignation avec ces types.</span><span class="sxs-lookup"><span data-stu-id="966c3-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="966c3-108">Pour plus d’informations, consultez [Utilisation d’opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="966c3-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="966c3-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="966c3-109">Example</span></span>  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="966c3-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="966c3-110">See Also</span></span>  
 [<span data-ttu-id="966c3-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="966c3-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="966c3-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="966c3-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="966c3-113">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="966c3-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
