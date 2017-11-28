---
title: "/, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9e12e5c472266ea75d3f572a2091bd0784ea5dcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="eee4d-102">/, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="eee4d-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="eee4d-103">L’opérateur de division (`/`) divise son premier opérande par son deuxième opérande.</span><span class="sxs-lookup"><span data-stu-id="eee4d-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="eee4d-104">Tous les types numériques ont des opérateurs de division prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="eee4d-104">All numeric types have predefined division operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eee4d-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="eee4d-105">Remarks</span></span>  
 <span data-ttu-id="eee4d-106">Les types définis par l’utilisateur peuvent surcharger l’opérateur `/` (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="eee4d-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="eee4d-107">Une surcharge de l’opérateur `/` surcharge implicitement l’[opérateur /=](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="eee4d-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="eee4d-108">Quand vous divisez deux entiers, le résultat est toujours un entier.</span><span class="sxs-lookup"><span data-stu-id="eee4d-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="eee4d-109">Par exemple, le résultat de 7 / 3 est 2.</span><span class="sxs-lookup"><span data-stu-id="eee4d-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="eee4d-110">Pour déterminer le reste de 7 / 3, utilisez l’opérateur de reste ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span><span class="sxs-lookup"><span data-stu-id="eee4d-110">To determine the remainder of 7 / 3, use the remainder operator ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span></span> <span data-ttu-id="eee4d-111">Pour obtenir un quotient comme nombre rationnel ou fraction, affectez au dividende ou au diviseur le type `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="eee4d-111">To obtain a quotient as a rational number or fraction, give the dividend or divisor type `float` or type `double`.</span></span> <span data-ttu-id="eee4d-112">Vous pouvez attribuer le type implicitement si vous exprimez le dividende ou le diviseur sous forme de nombre décimal en plaçant un chiffre à droite de la virgule décimale, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="eee4d-112">You can assign the type implicitly if you express the dividend or divisor as a decimal by putting a digit to the right side of the decimal point, as the following example shows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eee4d-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="eee4d-113">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="eee4d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eee4d-114">See Also</span></span>  
 [<span data-ttu-id="eee4d-115">Référence C#</span><span class="sxs-lookup"><span data-stu-id="eee4d-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="eee4d-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="eee4d-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="eee4d-117">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="eee4d-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
