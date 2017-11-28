---
title: "*=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc2201f78e1e05bd0ccdea04522896c00294bdd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3f820-102">*=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3f820-102">*= Operator (C# Reference)</span></span>
<span data-ttu-id="3f820-103">Opérateur d’assignation de multiplication binaire.</span><span class="sxs-lookup"><span data-stu-id="3f820-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f820-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="3f820-104">Remarks</span></span>  
 <span data-ttu-id="3f820-105">Une expression qui utilise l’opérateur d’assignation `*=`, telle que</span><span class="sxs-lookup"><span data-stu-id="3f820-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```  
x *= y  
```  
  
 <span data-ttu-id="3f820-106">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="3f820-106">is equivalent to</span></span>  
  
```  
x = x * y  
```  
  
 <span data-ttu-id="3f820-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="3f820-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="3f820-108">L’[opérateur *](../../../csharp/language-reference/operators/multiplication-operator.md) est prédéfini pour les types numériques de façon à effectuer une multiplication.</span><span class="sxs-lookup"><span data-stu-id="3f820-108">The [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="3f820-109">L’opérateur `*=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur *](../../../csharp/language-reference/operators/multiplication-operator.md) (consultez [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="3f820-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f820-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f820-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3f820-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f820-111">See Also</span></span>  
 [<span data-ttu-id="3f820-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="3f820-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3f820-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3f820-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3f820-114">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="3f820-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
