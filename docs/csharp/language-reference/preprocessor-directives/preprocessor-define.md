---
title: "#<a name=\"define-c-reference\"></a>define (informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#define'
helpviewer_keywords: '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae72a1b6c19421c51348a0d93691ba3fe29a191c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="define-c-reference"></a><span data-ttu-id="dbd5b-102">#define (référence C#)</span><span class="sxs-lookup"><span data-stu-id="dbd5b-102">#define (C# Reference)</span></span>
<span data-ttu-id="dbd5b-103">Vous utilisez `#define` pour définir un symbole.</span><span class="sxs-lookup"><span data-stu-id="dbd5b-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="dbd5b-104">Quand vous utilisez le symbole sous forme d’expression passée à la directive [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), l’expression donne la valeur `true`, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="dbd5b-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="dbd5b-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="dbd5b-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbd5b-106">La directive `#define` ne peut pas être utilisée pour déclarer des valeurs constantes comme c’est le cas en général en C et C++.</span><span class="sxs-lookup"><span data-stu-id="dbd5b-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="dbd5b-107">Les constantes en C# sont définies plutôt comme des membres statiques d’une classe ou d’un struct.</span><span class="sxs-lookup"><span data-stu-id="dbd5b-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="dbd5b-108">Si vous avez plusieurs constantes de ce type, créez une classe « Constantes » distincte pour les stocker.</span><span class="sxs-lookup"><span data-stu-id="dbd5b-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="dbd5b-109">Les symboles peuvent être utilisés pour spécifier des conditions de compilation.</span><span class="sxs-lookup"><span data-stu-id="dbd5b-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="dbd5b-110">Vous pouvez tester le symbole avec [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ou [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="dbd5b-110">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="dbd5b-111">Vous pouvez également utiliser l’attribut `conditional` pour effectuer une compilation conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="dbd5b-111">You can also use the `conditional` attribute to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="dbd5b-112">Vous pouvez définir un symbole, mais vous ne pouvez pas attribuer de valeur à un symbole.</span><span class="sxs-lookup"><span data-stu-id="dbd5b-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="dbd5b-113">La directive `#define` doit apparaître dans le fichier avant l’utilisation d’instructions qui ne sont pas également des directives de préprocesseur.</span><span class="sxs-lookup"><span data-stu-id="dbd5b-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="dbd5b-114">Vous pouvez également définir un symbole avec l’option de compilateur [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="dbd5b-114">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="dbd5b-115">Vous pouvez annuler la définition d’un symbole avec [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="dbd5b-115">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="dbd5b-116">Un symbole que vous définissez avec `/define` ou `#define` n’est pas en conflit avec une variable du même nom.</span><span class="sxs-lookup"><span data-stu-id="dbd5b-116">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="dbd5b-117">Autrement dit, un nom de variable ne doit pas être passé à une directive de préprocesseur et un symbole ne peut être évalué que par une directive de préprocesseur.</span><span class="sxs-lookup"><span data-stu-id="dbd5b-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="dbd5b-118">La portée d’un symbole qui a été créé à l’aide de `#define` est le fichier dans lequel le symbole a été défini.</span><span class="sxs-lookup"><span data-stu-id="dbd5b-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="dbd5b-119">Comme le montre l’exemple suivant, vous devez placer les directives `#define` en haut du fichier.</span><span class="sxs-lookup"><span data-stu-id="dbd5b-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 <span data-ttu-id="dbd5b-120">Pour obtenir un exemple montrant comment annuler la définition d’un symbole, consultez [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="dbd5b-120">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd5b-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbd5b-121">See Also</span></span>  
 [<span data-ttu-id="dbd5b-122">Référence C#</span><span class="sxs-lookup"><span data-stu-id="dbd5b-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="dbd5b-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="dbd5b-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dbd5b-124">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="dbd5b-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="dbd5b-125">const</span><span class="sxs-lookup"><span data-stu-id="dbd5b-125">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="dbd5b-126">Comment : effectuer une compilation conditionnelle avec Trace et Debug</span><span class="sxs-lookup"><span data-stu-id="dbd5b-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [<span data-ttu-id="dbd5b-127">#undef</span><span class="sxs-lookup"><span data-stu-id="dbd5b-127">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [<span data-ttu-id="dbd5b-128">#if</span><span class="sxs-lookup"><span data-stu-id="dbd5b-128">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
