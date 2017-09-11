---
title: "&lt;, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
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
ms.openlocfilehash: 5d90a8e549b54fc229ac3ae5bb8f30ce3b55c0d4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="9dd50-102">&lt;, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="9dd50-102">&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="9dd50-103">Tous les types numériques et d’énumération définissent un opérateur relationnel « inférieur à » (`<`) qui retourne `true` si le premier opérande est inférieur au deuxième et `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="9dd50-103">All numeric and enumeration types define a "less than" relational operator (`<`) that returns `true` if the first operand is less than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9dd50-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="9dd50-104">Remarks</span></span>  
 <span data-ttu-id="9dd50-105">Les types définis par l’utilisateur peuvent surcharger l’opérateur `<` (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="9dd50-105">User-defined types can overload the `<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="9dd50-106">Si `<` est surchargé, [>](../../../csharp/language-reference/operators/greater-than-operator.md) doit aussi l’être.</span><span class="sxs-lookup"><span data-stu-id="9dd50-106">If `<` is overloaded, [>](../../../csharp/language-reference/operators/greater-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="9dd50-107">Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="9dd50-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dd50-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="9dd50-108">Example</span></span>  
 <span data-ttu-id="9dd50-109">[!code-cs[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9dd50-109">[!code-cs[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd50-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dd50-110">See Also</span></span>  
 <span data-ttu-id="9dd50-111">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9dd50-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9dd50-112">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9dd50-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="9dd50-113">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="9dd50-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

