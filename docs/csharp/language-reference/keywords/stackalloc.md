---
title: "stackalloc (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords: stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad4453f889a344fcd44dfad44a30fef07380b6a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="f4a08-102">stackalloc (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f4a08-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="f4a08-103">Le mot clé `stackalloc` est utilisé dans un contexte de code unsafe pour allouer un bloc de mémoire sur la pile.</span><span class="sxs-lookup"><span data-stu-id="f4a08-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a><span data-ttu-id="f4a08-104">Notes</span><span class="sxs-lookup"><span data-stu-id="f4a08-104">Remarks</span></span>  
 <span data-ttu-id="f4a08-105">Le mot clé est valide uniquement dans les initialiseurs de variable locale.</span><span class="sxs-lookup"><span data-stu-id="f4a08-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="f4a08-106">Le code suivant génère des erreurs de compilation.</span><span class="sxs-lookup"><span data-stu-id="f4a08-106">The following code causes compiler errors.</span></span>  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 <span data-ttu-id="f4a08-107">Des types pointeur étant impliqués, `stackalloc` requiert un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="f4a08-107">Because pointer types are involved, `stackalloc` requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="f4a08-108">Pour plus d’informations, consultez [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4a08-108">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="f4a08-109">`stackalloc` est similaire à [_alloca](/cpp/c-runtime-library/reference/alloca) dans la bibliothèque Runtime C.</span><span class="sxs-lookup"><span data-stu-id="f4a08-109">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>  
  
 <span data-ttu-id="f4a08-110">L’exemple suivant calcule et affiche les 20 premiers nombres de la suite de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="f4a08-110">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="f4a08-111">Chaque nombre est la somme des deux nombres précédents.</span><span class="sxs-lookup"><span data-stu-id="f4a08-111">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="f4a08-112">Dans le code, un bloc de mémoire de taille suffisante pour contenir 20 éléments de type `int` est alloué sur la pile, et non sur le tas.</span><span class="sxs-lookup"><span data-stu-id="f4a08-112">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="f4a08-113">L’adresse du bloc est stockée dans le pointeur `fib`.</span><span class="sxs-lookup"><span data-stu-id="f4a08-113">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="f4a08-114">Cette mémoire n’est pas soumise au garbage collection et n’est donc pas tenue d’être épinglée (en utilisant [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="f4a08-114">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)).</span></span> <span data-ttu-id="f4a08-115">La durée de vie du bloc de mémoire est limitée à la durée de vie de la méthode qui le définit.</span><span class="sxs-lookup"><span data-stu-id="f4a08-115">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="f4a08-116">Vous ne pouvez pas libérer la mémoire avant le retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f4a08-116">You cannot free the memory before the method returns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4a08-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="f4a08-117">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a><span data-ttu-id="f4a08-118">Sécurité</span><span class="sxs-lookup"><span data-stu-id="f4a08-118">Security</span></span>  
 <span data-ttu-id="f4a08-119">Le code unsafe est moins sûr que les alternatives safe.</span><span class="sxs-lookup"><span data-stu-id="f4a08-119">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="f4a08-120">Toutefois, l’utilisation de `stackalloc` active automatiquement les fonctionnalités de détection des dépassements de mémoire tampon dans le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f4a08-120">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="f4a08-121">Si un dépassement de mémoire tampon est détecté, le processus est terminé aussi rapidement que possible pour réduire les risques d’exécution de code malveillant.</span><span class="sxs-lookup"><span data-stu-id="f4a08-121">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f4a08-122">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f4a08-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f4a08-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4a08-123">See Also</span></span>  
 [<span data-ttu-id="f4a08-124">Référence C#</span><span class="sxs-lookup"><span data-stu-id="f4a08-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f4a08-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f4a08-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f4a08-126">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="f4a08-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f4a08-127">Mots clés des opérateurs</span><span class="sxs-lookup"><span data-stu-id="f4a08-127">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="f4a08-128">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="f4a08-128">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
