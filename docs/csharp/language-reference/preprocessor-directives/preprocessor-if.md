---
title: "#<a name=\"if-c-reference\"></a>if (informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#if'
helpviewer_keywords: '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4e3b79f64f5190d48d7248726ecdf031ad685e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="if-c-reference"></a><span data-ttu-id="da500-102">#if (référence C#)</span><span class="sxs-lookup"><span data-stu-id="da500-102">#if (C# Reference)</span></span>
<span data-ttu-id="da500-103">Quand le compilateur C# rencontre une directive `#if`, suivie éventuellement d’une directive [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), il compile le code entre les directives uniquement si le symbole spécifié est défini.</span><span class="sxs-lookup"><span data-stu-id="da500-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) directive, it will compile the code between the directives only if the specified symbol is defined.</span></span>  <span data-ttu-id="da500-104">Contrairement à C et C++, vous ne pouvez pas attribuer une valeur numérique à un symbole ; l’instruction #if en C# est booléenne et vérifie uniquement si le symbole a été défini ou non.</span><span class="sxs-lookup"><span data-stu-id="da500-104">Unlike C and C++, you cannot assign a numeric value to a symbol; the #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="da500-105">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="da500-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 <span data-ttu-id="da500-106">Vous pouvez utiliser les opérateurs [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (égalité), [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (inégalité) uniquement pour tester la valeur [true](../../../csharp/language-reference/keywords/true.md) ou [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="da500-106">You can use the operators [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (equality), [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (inequality) only to test for [true](../../../csharp/language-reference/keywords/true.md) or [false](../../../csharp/language-reference/keywords/false.md) .</span></span> <span data-ttu-id="da500-107">True signifie que le symbole est défini.</span><span class="sxs-lookup"><span data-stu-id="da500-107">True means the symbol is defined.</span></span> <span data-ttu-id="da500-108">L’instruction `#if DEBUG` a la même signification que `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="da500-108">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="da500-109">Vous pouvez utiliser les opérateurs [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (et), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (or) et [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="da500-109">You can use the operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (and), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (or), and [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span></span> <span data-ttu-id="da500-110">(not) pour vérifier si plusieurs symboles ont été définis.</span><span class="sxs-lookup"><span data-stu-id="da500-110">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="da500-111">Vous pouvez également regrouper des symboles et des opérateurs à l’aide de parenthèses.</span><span class="sxs-lookup"><span data-stu-id="da500-111">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da500-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="da500-112">Remarks</span></span>  
 <span data-ttu-id="da500-113">`#if`, ainsi que les directives [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) et [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md), vous permettent d’inclure ou d’exclure du code en fonction de l’existence d’un ou plusieurs symboles.</span><span class="sxs-lookup"><span data-stu-id="da500-113">`#if`, along with the [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), and [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="da500-114">Cela peut être utile lors de la compilation du code pour une version Debug ou lors de la compilation d’une configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="da500-114">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>  
  
 <span data-ttu-id="da500-115">Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`.</span><span class="sxs-lookup"><span data-stu-id="da500-115">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>  
  
 <span data-ttu-id="da500-116">`#define` vous permet de définir un symbole de telle sorte que, en utilisant le symbole comme expression passée à la directive `#if`, l’expression corresponde à `true`.</span><span class="sxs-lookup"><span data-stu-id="da500-116">`#define` lets you define a symbol, such that, by using the symbol as the expression passed to the `#if` directive, the expression will evaluate to `true`.</span></span>  
  
 <span data-ttu-id="da500-117">Vous pouvez également définir un symbole avec l’option du compilateur [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="da500-117">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="da500-118">Vous pouvez annuler la définition d’un symbole avec [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="da500-118">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="da500-119">Un symbole que vous définissez avec `/define` ou `#define` n’est pas en conflit avec une variable du même nom.</span><span class="sxs-lookup"><span data-stu-id="da500-119">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="da500-120">Autrement dit, un nom de variable ne doit pas être passé à une directive de préprocesseur et un symbole ne peut être évalué que par une directive de préprocesseur.</span><span class="sxs-lookup"><span data-stu-id="da500-120">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="da500-121">La portée d’un symbole créé avec `#define` est le fichier dans lequel il a été défini.</span><span class="sxs-lookup"><span data-stu-id="da500-121">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da500-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="da500-122">Example</span></span>  
  
```csharp
// preprocessor_if.cs  
#define DEBUG
#define MYTEST  
using System;  
public class MyClass   
{  
    static void Main()   
    {  
#if (DEBUG && !MYTEST)  
        Console.WriteLine("DEBUG is defined");  
#elif (!DEBUG && MYTEST)  
        Console.WriteLine("MYTEST is defined");  
#elif (DEBUG && MYTEST)  
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else  
        Console.WriteLine("DEBUG and MYTEST are not defined");  
#endif  
    }  
}  
```  
  
 <span data-ttu-id="da500-123">**DEBUG et MYTEST sont définis**</span><span class="sxs-lookup"><span data-stu-id="da500-123">**DEBUG and MYTEST are defined**</span></span>  
## <a name="see-also"></a><span data-ttu-id="da500-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da500-124">See Also</span></span>  
 [<span data-ttu-id="da500-125">Référence C#</span><span class="sxs-lookup"><span data-stu-id="da500-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="da500-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="da500-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="da500-127">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="da500-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
