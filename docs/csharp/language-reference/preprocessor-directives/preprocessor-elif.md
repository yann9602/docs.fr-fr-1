---
title: "#<a name=\"elif-c-reference\"></a>elif (informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#elif'
dev_langs:
- CSharp
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
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
ms.openlocfilehash: 7635365222621101253ecb2a3676701c2e6a2b88
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="elif-c-reference"></a><span data-ttu-id="1a110-102">#elif (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="1a110-102">#elif (C# Reference)</span></span>
<span data-ttu-id="1a110-103">`#elif` vous permet de créer une directive conditionnelle composée.</span><span class="sxs-lookup"><span data-stu-id="1a110-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="1a110-104">L’expression `#elif` est évaluée si ni l’expression [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) précédente ni une expression de directive `#elif` facultative précédente n’est évaluée à `true`.</span><span class="sxs-lookup"><span data-stu-id="1a110-104">The `#elif` expression will be evaluated if neither the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="1a110-105">Si une expression `#elif` est évaluée à `true`, le compilateur évalue l’ensemble du code situé entre `#elif` et la directive conditionnelle suivante.</span><span class="sxs-lookup"><span data-stu-id="1a110-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="1a110-106">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1a110-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="1a110-107">Vous pouvez utiliser les opérateurs `==` (égalité), `!=` (inégalité) `&&` (et) et `||` (ou) pour évaluer plusieurs symboles.</span><span class="sxs-lookup"><span data-stu-id="1a110-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="1a110-108">Vous pouvez également regrouper des symboles et des opérateurs à l’aide de parenthèses.</span><span class="sxs-lookup"><span data-stu-id="1a110-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a110-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="1a110-109">Remarks</span></span>  
 <span data-ttu-id="1a110-110">`#elif` revient à utiliser :</span><span class="sxs-lookup"><span data-stu-id="1a110-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="1a110-111">`#elif` est plus simple à utiliser, car chaque expression `#if` a besoin d’une expression [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), alors qu’une expression `#elif` peut être utilisée sans expression `#endif` correspondante.</span><span class="sxs-lookup"><span data-stu-id="1a110-111">Using `#elif` is simpler, because each `#if` requires a [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="1a110-112">Pour obtenir un exemple sur la façon d’utiliser `#elif`, consultez [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="1a110-112">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a110-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a110-113">See Also</span></span>  
 <span data-ttu-id="1a110-114">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1a110-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1a110-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1a110-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="1a110-116">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="1a110-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

