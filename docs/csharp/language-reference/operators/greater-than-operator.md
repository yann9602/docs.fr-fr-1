---
title: "&gt;, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
caps.latest.revision: 16
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
ms.openlocfilehash: 5b4eb1f6fcca311fc772e4dbe0ce0391201af3de
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="b8525-102">&gt;, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b8525-102">&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="b8525-103">Tous les types numériques et d’énumération définissent un opérateur relationnel « supérieur à » (`>`) qui retourne `true` si le premier opérande est supérieur au second, et `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="b8525-103">All numeric and enumeration types define a "greater than" relational operator (`>`) that returns `true` if the first operand is greater than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8525-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="b8525-104">Remarks</span></span>  
 <span data-ttu-id="b8525-105">Les types définis par l’utilisateur peuvent surcharger l’opérateur `>` (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b8525-105">User-defined types can overload the `>` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="b8525-106">Si `>` est surchargé, [<](../../../csharp/language-reference/operators/less-than-operator.md) doit l’être aussi.</span><span class="sxs-lookup"><span data-stu-id="b8525-106">If `>` is overloaded, [<](../../../csharp/language-reference/operators/less-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="b8525-107">Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="b8525-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8525-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8525-108">Example</span></span>  
 <span data-ttu-id="b8525-109">[!code-cs[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b8525-109">[!code-cs[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8525-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8525-110">See Also</span></span>  
 <span data-ttu-id="b8525-111">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b8525-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b8525-112">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b8525-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b8525-113">[Opérateurs C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="b8525-113">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 [<span data-ttu-id="b8525-114">explicit</span><span class="sxs-lookup"><span data-stu-id="b8525-114">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)

