---
title: "#<a name=\"endif-c-reference\"></a>endif (informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#endif'
helpviewer_keywords: '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d7e68dd20d914052c3fe5cabcb83abdae100465c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="endif-c-reference"></a><span data-ttu-id="0cc61-102">#endif (référence C#)</span><span class="sxs-lookup"><span data-stu-id="0cc61-102">#endif (C# Reference)</span></span>
<span data-ttu-id="0cc61-103">`#endif` spécifie la fin d’une directive conditionnelle, qui a commencé avec la directive [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="0cc61-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="0cc61-104">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0cc61-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="0cc61-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="0cc61-105">Remarks</span></span>  
 <span data-ttu-id="0cc61-106">Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`.</span><span class="sxs-lookup"><span data-stu-id="0cc61-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="0cc61-107">Consultez [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) pour obtenir un exemple d’utilisation de `#endif`.</span><span class="sxs-lookup"><span data-stu-id="0cc61-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cc61-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cc61-108">See Also</span></span>  
 [<span data-ttu-id="0cc61-109">Référence C#</span><span class="sxs-lookup"><span data-stu-id="0cc61-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0cc61-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="0cc61-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0cc61-111">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="0cc61-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
