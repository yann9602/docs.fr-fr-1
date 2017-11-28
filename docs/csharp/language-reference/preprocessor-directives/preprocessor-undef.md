---
title: "#<a name=\"undef-c-reference\"></a>undef (informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#undef'
helpviewer_keywords: '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7a3c162c0ecb8bb39cc13a34dcd15fa3ce96ebb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="undef-c-reference"></a><span data-ttu-id="748de-102">#undef (référence C#)</span><span class="sxs-lookup"><span data-stu-id="748de-102">#undef (C# Reference)</span></span>
<span data-ttu-id="748de-103">`#undef` vous permet d’annuler la définition d’un symbole de telle sorte qu’en utilisant le symbole comme expression dans une directive [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), l’expression correspond à `false`.</span><span class="sxs-lookup"><span data-stu-id="748de-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="748de-104">Un symbole peut être défini avec la directive [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) ou l’option du compilateur [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="748de-104">A symbol can be defined either with the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) directive or the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="748de-105">La directive `#undef` doit figurer dans le fichier préalablement à l’utilisation d’instructions qui ne sont pas aussi des directives.</span><span class="sxs-lookup"><span data-stu-id="748de-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="748de-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="748de-106">Example</span></span>  
  
```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass   
{  
    static void Main()   
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```  
  
 <span data-ttu-id="748de-107">**DEBUG n’est pas défini**</span><span class="sxs-lookup"><span data-stu-id="748de-107">**DEBUG is not defined**</span></span>  
## <a name="see-also"></a><span data-ttu-id="748de-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="748de-108">See Also</span></span>  
 [<span data-ttu-id="748de-109">Référence C#</span><span class="sxs-lookup"><span data-stu-id="748de-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="748de-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="748de-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="748de-111">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="748de-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
