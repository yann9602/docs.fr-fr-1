---
title: "%, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '%_CSharpKeyword'
helpviewer_keywords:
- modulus operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cea4aa03424e93f3ec144126d73c63931a737b54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a04ba-102">%, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a04ba-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="a04ba-103">L’opérateur `%` calcule le reste de la division du premier opérande par le deuxième.</span><span class="sxs-lookup"><span data-stu-id="a04ba-103">The `%` operator computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="a04ba-104">Tous les types numériques ont des opérateurs de reste prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="a04ba-104">All numeric types have predefined remainder operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a04ba-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="a04ba-105">Remarks</span></span>  
 <span data-ttu-id="a04ba-106">Les types définis par l’utilisateur peuvent surcharger l’opérateur `%` (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a04ba-106">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="a04ba-107">Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="a04ba-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a04ba-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="a04ba-108">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="a04ba-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="a04ba-109">Comments</span></span>  
 <span data-ttu-id="a04ba-110">Notez les erreurs d’arrondi associées au type double.</span><span class="sxs-lookup"><span data-stu-id="a04ba-110">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a04ba-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a04ba-111">See Also</span></span>  
 [<span data-ttu-id="a04ba-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="a04ba-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a04ba-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a04ba-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a04ba-114">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="a04ba-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
