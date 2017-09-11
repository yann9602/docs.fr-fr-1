---
title: "fixed, instruction (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
dev_langs:
- CSharp
helpviewer_keywords:
- fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 24
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
ms.openlocfilehash: 4e1f810f6e6cfaef3a65c7391f074b414ef18b5a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="7ac3b-102">fixed, instruction (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7ac3b-102">fixed Statement (C# Reference)</span></span>
<span data-ttu-id="7ac3b-103">L’instruction `fixed` empêche le récupérateur de mémoire de déplacer une variable mobile.</span><span class="sxs-lookup"><span data-stu-id="7ac3b-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="7ac3b-104">L’instruction `fixed` est uniquement autorisée dans un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="7ac3b-104">The `fixed` statement is only permitted in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="7ac3b-105">`Fixed` peut également être utilisé pour créer des [mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="7ac3b-105">`Fixed` can also be used to create [fixed size buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 <span data-ttu-id="7ac3b-106">L’instruction `fixed` définit un pointeur vers une variable managée et épingle cette variable pendant l’exécution de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="7ac3b-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="7ac3b-107">Sans `fixed`, les pointeurs de variables managées déplaçables seraient peu utiles puisque le garbage collection pourrait déplacer les variables de manière imprévisible.</span><span class="sxs-lookup"><span data-stu-id="7ac3b-107">Without `fixed`, pointers to movable managed variables would be of little use since garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="7ac3b-108">Le compilateur C# permet seulement d’assigner un pointeur à une variable managée dans une instruction `fixed`.</span><span class="sxs-lookup"><span data-stu-id="7ac3b-108">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>  
  
 <span data-ttu-id="7ac3b-109">[!code-cs[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="7ac3b-109">[!code-cs[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]</span></span>  
  
 <span data-ttu-id="7ac3b-110">Vous pouvez initialiser un pointeur à l’aide d’un tableau, d’une chaîne, d’un tampon de taille fixe ou de l’adresse d’une variable.</span><span class="sxs-lookup"><span data-stu-id="7ac3b-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="7ac3b-111">L’exemple suivant montre l’utilisation des adresses de variables, des tableaux et des chaînes.</span><span class="sxs-lookup"><span data-stu-id="7ac3b-111">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="7ac3b-112">Pour plus d’informations sur les mémoires tampons de taille fixe, consultez [Mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="7ac3b-112">For more information about fixed-size buffers, see [Fixed Size Buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 <span data-ttu-id="7ac3b-113">[!code-cs[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="7ac3b-113">[!code-cs[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]</span></span>  
  
 <span data-ttu-id="7ac3b-114">Vous pouvez initialiser plusieurs pointeurs, tant qu’ils sont tous du même type.</span><span class="sxs-lookup"><span data-stu-id="7ac3b-114">You can initialize multiple pointers, as long as they are all of the same type.</span></span>  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 <span data-ttu-id="7ac3b-115">Pour initialiser des pointeurs de types différents, imbriquez des instructions `fixed`, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7ac3b-115">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>  
  
 <span data-ttu-id="7ac3b-116">[!code-cs[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="7ac3b-116">[!code-cs[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]</span></span>  
  
 <span data-ttu-id="7ac3b-117">Une fois que le code de l’instruction est exécuté, toutes les variables épinglées sont libérées et soumises au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7ac3b-117">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="7ac3b-118">Par conséquent, ne pointez pas vers ces variables en dehors de l’instruction `fixed`.</span><span class="sxs-lookup"><span data-stu-id="7ac3b-118">Therefore, do not point to those variables outside the `fixed` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ac3b-119">Les pointeurs initialisés dans les instructions fixed ne peuvent pas être modifiés.</span><span class="sxs-lookup"><span data-stu-id="7ac3b-119">Pointers initialized in fixed statements cannot be modified.</span></span>  
  
 <span data-ttu-id="7ac3b-120">En mode unsafe, vous pouvez allouer de la mémoire sur la pile, où elle n’est pas soumise au garbage collection et n’a donc pas besoin d’être épinglée.</span><span class="sxs-lookup"><span data-stu-id="7ac3b-120">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="7ac3b-121">Pour plus d’informations, consultez [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="7ac3b-121">For more information, see [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ac3b-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="7ac3b-122">Example</span></span>  
 <span data-ttu-id="7ac3b-123">[!code-cs[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="7ac3b-123">[!code-cs[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7ac3b-124">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7ac3b-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7ac3b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ac3b-125">See Also</span></span>  
 <span data-ttu-id="7ac3b-126">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7ac3b-126">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="7ac3b-127">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7ac3b-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="7ac3b-128">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="7ac3b-128">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="7ac3b-129">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="7ac3b-129">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 [<span data-ttu-id="7ac3b-130">Mémoires tampons de taille fixe</span><span class="sxs-lookup"><span data-stu-id="7ac3b-130">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

