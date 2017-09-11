---
title: "/, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
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
ms.openlocfilehash: 2972261996467f987fa457213b1bcb482d9f1519
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="59673-102">/, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="59673-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="59673-103">L’opérateur de division (`/`) divise son premier opérande par son deuxième opérande.</span><span class="sxs-lookup"><span data-stu-id="59673-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="59673-104">Tous les types numériques ont des opérateurs de division prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="59673-104">All numeric types have predefined division operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59673-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="59673-105">Remarks</span></span>  
 <span data-ttu-id="59673-106">Les types définis par l’utilisateur peuvent surcharger l’opérateur `/` (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="59673-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="59673-107">Une surcharge de l’opérateur `/` surcharge implicitement l’[opérateur /=](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="59673-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="59673-108">Quand vous divisez deux entiers, le résultat est toujours un entier.</span><span class="sxs-lookup"><span data-stu-id="59673-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="59673-109">Par exemple, le résultat de 7 / 3 est 2.</span><span class="sxs-lookup"><span data-stu-id="59673-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="59673-110">Pour déterminer le reste de 7 / 3, utilisez l’opérateur de reste ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span><span class="sxs-lookup"><span data-stu-id="59673-110">To determine the remainder of 7 / 3, use the remainder operator ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span></span> <span data-ttu-id="59673-111">Pour obtenir un quotient comme nombre rationnel ou fraction, affectez au dividende ou au diviseur le type `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="59673-111">To obtain a quotient as a rational number or fraction, give the dividend or divisor type `float` or type `double`.</span></span> <span data-ttu-id="59673-112">Vous pouvez attribuer le type implicitement si vous exprimez le dividende ou le diviseur sous forme de nombre décimal en plaçant un chiffre à droite de la virgule décimale, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="59673-112">You can assign the type implicitly if you express the dividend or divisor as a decimal by putting a digit to the right side of the decimal point, as the following example shows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59673-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="59673-113">Example</span></span>  
 <span data-ttu-id="59673-114">[!code-cs[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="59673-114">[!code-cs[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59673-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59673-115">See Also</span></span>  
 <span data-ttu-id="59673-116">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="59673-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="59673-117">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="59673-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="59673-118">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="59673-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

