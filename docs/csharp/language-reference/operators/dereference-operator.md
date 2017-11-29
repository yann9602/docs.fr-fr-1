---
title: "-&gt;, opérateur (Informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c5918f56257feb29d2624ba29b8cebaaa4f4ebe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="ddb46-102">-&gt;, opérateur (Informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="ddb46-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="ddb46-103">L’opérateur `->` allie l’annulation de la référence d’un pointeur et l’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="ddb46-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddb46-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="ddb46-104">Remarks</span></span>  
 <span data-ttu-id="ddb46-105">Une expression de forme</span><span class="sxs-lookup"><span data-stu-id="ddb46-105">An expression of the form,</span></span>  
  
```  
x->y  
```  
  
 <span data-ttu-id="ddb46-106">(où `x` est un pointeur de type `T*` et `y` un membre de `T`) est équivalente à</span><span class="sxs-lookup"><span data-stu-id="ddb46-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```  
(*x).y  
```  
  
 <span data-ttu-id="ddb46-107">L’opérateur `->` peut être utilisé uniquement dans du code marqué comme [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="ddb46-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="ddb46-108">L’opérateur `->` ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="ddb46-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddb46-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="ddb46-109">Example</span></span>  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ddb46-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddb46-110">See Also</span></span>  
 [<span data-ttu-id="ddb46-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="ddb46-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ddb46-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ddb46-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ddb46-113">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="ddb46-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
