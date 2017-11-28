---
title: "/=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26096d9b5dfc565c9933f1ed8ffb241dc900d9ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="81df7-102">/=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="81df7-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="81df7-103">Opérateur d’assignation de division.</span><span class="sxs-lookup"><span data-stu-id="81df7-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81df7-104">Notes</span><span class="sxs-lookup"><span data-stu-id="81df7-104">Remarks</span></span>  
 <span data-ttu-id="81df7-105">Une expression qui utilise l’opérateur d’assignation `/=`, telle que</span><span class="sxs-lookup"><span data-stu-id="81df7-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```  
x /= y  
```  
  
 <span data-ttu-id="81df7-106">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="81df7-106">is equivalent to</span></span>  
  
```  
x = x / y  
```  
  
 <span data-ttu-id="81df7-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="81df7-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="81df7-108">L’[opérateur /](../../../csharp/language-reference/operators/division-operator.md) est prédéfini pour les types numériques afin d’effectuer une division.</span><span class="sxs-lookup"><span data-stu-id="81df7-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="81df7-109">Vous ne pouvez pas surcharger directement l’opérateur `/=`, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur /](../../../csharp/language-reference/operators/division-operator.md) (voir [opérateur](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="81df7-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="81df7-110">Sur tous les opérateurs d’assignation composée, le fait de surcharger l’opérateur binaire surcharge implicitement l’assignation composée équivalente.</span><span class="sxs-lookup"><span data-stu-id="81df7-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81df7-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="81df7-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="81df7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81df7-112">See Also</span></span>  
 [<span data-ttu-id="81df7-113">Référence C#</span><span class="sxs-lookup"><span data-stu-id="81df7-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="81df7-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="81df7-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="81df7-115">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="81df7-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
