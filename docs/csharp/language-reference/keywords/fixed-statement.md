---
title: "fixed, instruction (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords: fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13633e71c863b075eede41c9a18419d65350bdb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="9980b-102">fixed, instruction (référence C#)</span><span class="sxs-lookup"><span data-stu-id="9980b-102">fixed Statement (C# Reference)</span></span>
<span data-ttu-id="9980b-103">L’instruction `fixed` empêche le récupérateur de mémoire de déplacer une variable mobile.</span><span class="sxs-lookup"><span data-stu-id="9980b-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="9980b-104">L’instruction `fixed` est uniquement autorisée dans un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="9980b-104">The `fixed` statement is only permitted in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="9980b-105">`Fixed` peut également être utilisé pour créer des [mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="9980b-105">`Fixed` can also be used to create [fixed size buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 <span data-ttu-id="9980b-106">L’instruction `fixed` définit un pointeur vers une variable managée et épingle cette variable pendant l’exécution de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="9980b-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="9980b-107">Sans `fixed`, les pointeurs de variables managées déplaçables seraient peu utiles puisque le garbage collection pourrait déplacer les variables de manière imprévisible.</span><span class="sxs-lookup"><span data-stu-id="9980b-107">Without `fixed`, pointers to movable managed variables would be of little use since garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="9980b-108">Le compilateur C# permet seulement d’assigner un pointeur à une variable managée dans une instruction `fixed`.</span><span class="sxs-lookup"><span data-stu-id="9980b-108">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 <span data-ttu-id="9980b-109">Vous pouvez initialiser un pointeur à l’aide d’un tableau, d’une chaîne, d’un tampon de taille fixe ou de l’adresse d’une variable.</span><span class="sxs-lookup"><span data-stu-id="9980b-109">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="9980b-110">L’exemple suivant montre l’utilisation des adresses de variables, des tableaux et des chaînes.</span><span class="sxs-lookup"><span data-stu-id="9980b-110">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="9980b-111">Pour plus d’informations sur les mémoires tampons de taille fixe, consultez [Mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="9980b-111">For more information about fixed-size buffers, see [Fixed Size Buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 <span data-ttu-id="9980b-112">Vous pouvez initialiser plusieurs pointeurs, tant qu’ils sont tous du même type.</span><span class="sxs-lookup"><span data-stu-id="9980b-112">You can initialize multiple pointers, as long as they are all of the same type.</span></span>  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 <span data-ttu-id="9980b-113">Pour initialiser des pointeurs de types différents, imbriquez des instructions `fixed`, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9980b-113">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 <span data-ttu-id="9980b-114">Une fois que le code de l’instruction est exécuté, toutes les variables épinglées sont libérées et soumises au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="9980b-114">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="9980b-115">Par conséquent, ne pointez pas vers ces variables en dehors de l’instruction `fixed`.</span><span class="sxs-lookup"><span data-stu-id="9980b-115">Therefore, do not point to those variables outside the `fixed` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9980b-116">Les pointeurs initialisés dans les instructions fixed ne peuvent pas être modifiés.</span><span class="sxs-lookup"><span data-stu-id="9980b-116">Pointers initialized in fixed statements cannot be modified.</span></span>  
  
 <span data-ttu-id="9980b-117">En mode unsafe, vous pouvez allouer de la mémoire sur la pile, où elle n’est pas soumise au garbage collection et n’a donc pas besoin d’être épinglée.</span><span class="sxs-lookup"><span data-stu-id="9980b-117">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="9980b-118">Pour plus d’informations, consultez [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="9980b-118">For more information, see [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9980b-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="9980b-119">Example</span></span>  
 [!code-csharp[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9980b-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9980b-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9980b-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9980b-121">See Also</span></span>  
 [<span data-ttu-id="9980b-122">Référence C#</span><span class="sxs-lookup"><span data-stu-id="9980b-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9980b-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9980b-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9980b-124">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="9980b-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9980b-125">unsafe</span><span class="sxs-lookup"><span data-stu-id="9980b-125">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="9980b-126">Mémoires tampons de taille fixe</span><span class="sxs-lookup"><span data-stu-id="9980b-126">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
