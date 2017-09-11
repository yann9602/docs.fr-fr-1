---
title: "#<a name=\"define-c-reference\"></a>define (informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#define'
dev_langs:
- CSharp
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: 22
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
ms.openlocfilehash: 8ace15f79480c9aeb0fcb4c7d46c207d4904cef0
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="define-c-reference"></a><span data-ttu-id="9e648-102">#define (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="9e648-102">#define (C# Reference)</span></span>
<span data-ttu-id="9e648-103">Vous utilisez `#define` pour définir un symbole.</span><span class="sxs-lookup"><span data-stu-id="9e648-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="9e648-104">Quand vous utilisez le symbole sous forme d’expression passée à la directive [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), l’expression donne la valeur `true`, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="9e648-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
  
 <span data-ttu-id="9e648-105">`#`  `define`   `DEBUG`</span><span class="sxs-lookup"><span data-stu-id="9e648-105">`#`  `define`   `DEBUG`</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e648-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="9e648-106">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e648-107">La directive `#define` ne peut pas être utilisée pour déclarer des valeurs constantes comme c’est le cas en général en C et C++.</span><span class="sxs-lookup"><span data-stu-id="9e648-107">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="9e648-108">Les constantes en C# sont définies plutôt comme des membres statiques d’une classe ou d’un struct.</span><span class="sxs-lookup"><span data-stu-id="9e648-108">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="9e648-109">Si vous avez plusieurs constantes de ce type, créez une classe « Constantes » distincte pour les stocker.</span><span class="sxs-lookup"><span data-stu-id="9e648-109">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="9e648-110">Les symboles peuvent être utilisés pour spécifier des conditions de compilation.</span><span class="sxs-lookup"><span data-stu-id="9e648-110">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="9e648-111">Vous pouvez tester le symbole avec [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ou [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="9e648-111">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="9e648-112">Vous pouvez également utiliser l’attribut `conditional` pour effectuer une compilation conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="9e648-112">You can also use the `conditional` attribute to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="9e648-113">Vous pouvez définir un symbole, mais vous ne pouvez pas attribuer de valeur à un symbole.</span><span class="sxs-lookup"><span data-stu-id="9e648-113">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="9e648-114">La directive `#define` doit apparaître dans le fichier avant l’utilisation d’instructions qui ne sont pas également des directives de préprocesseur.</span><span class="sxs-lookup"><span data-stu-id="9e648-114">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="9e648-115">Vous pouvez également définir un symbole avec l’option de compilateur [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="9e648-115">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="9e648-116">Vous pouvez annuler la définition d’un symbole avec [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="9e648-116">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="9e648-117">Un symbole que vous définissez avec `/define` ou `#define` n’est pas en conflit avec une variable du même nom.</span><span class="sxs-lookup"><span data-stu-id="9e648-117">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="9e648-118">Autrement dit, un nom de variable ne doit pas être passé à une directive de préprocesseur et un symbole ne peut être évalué que par une directive de préprocesseur.</span><span class="sxs-lookup"><span data-stu-id="9e648-118">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="9e648-119">La portée d’un symbole qui a été créé à l’aide de `#define` est le fichier dans lequel le symbole a été défini.</span><span class="sxs-lookup"><span data-stu-id="9e648-119">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="9e648-120">Comme le montre l’exemple suivant, vous devez placer les directives `#define` en haut du fichier.</span><span class="sxs-lookup"><span data-stu-id="9e648-120">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="9e648-121">Pour obtenir un exemple montrant comment annuler la définition d’un symbole, consultez [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="9e648-121">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e648-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e648-122">See Also</span></span>  
 <span data-ttu-id="9e648-123">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9e648-123">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9e648-124">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9e648-124">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9e648-125">[Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md) </span><span class="sxs-lookup"><span data-stu-id="9e648-125">[C# Preprocessor Directives](../../../csharp/language-reference/preprocessor-directives/index.md) </span></span>  
 <span data-ttu-id="9e648-126">[const](../../../csharp/language-reference/keywords/const.md) </span><span class="sxs-lookup"><span data-stu-id="9e648-126">[const](../../../csharp/language-reference/keywords/const.md) </span></span>  
 <span data-ttu-id="9e648-127">[Guide pratique pour effectuer une compilation conditionnelle avec Trace et Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) </span><span class="sxs-lookup"><span data-stu-id="9e648-127">[How to: Compile Conditionally with Trace and Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) </span></span>  
 <span data-ttu-id="9e648-128">[#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) </span><span class="sxs-lookup"><span data-stu-id="9e648-128">[#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) </span></span>  
 [<span data-ttu-id="9e648-129">#if</span><span class="sxs-lookup"><span data-stu-id="9e648-129">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)

