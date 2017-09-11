---
title: "Guide pratique pour incrémenter et décrémenter des pointeurs (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: 20
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
ms.openlocfilehash: b474249ed9f7778e44981b292d51f29f46bc420d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="2f26d-102">Guide pratique pour incrémenter et décrémenter des pointeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2f26d-102">How to: Increment and Decrement Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="2f26d-103">Utilisez les opérateurs d’incrémentation et de décrémentation, `++` et `--`, pour changer l’emplacement du pointeur de [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) pour un pointeur de type pointer-type*.</span><span class="sxs-lookup"><span data-stu-id="2f26d-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) for a pointer of type pointer-type*.</span></span> <span data-ttu-id="2f26d-104">Les expressions d’incrémentation et de décrémentation prennent la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="2f26d-104">The increment and decrement expressions take the following form:</span></span>  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="2f26d-105">Les opérateurs d’incrémentation et de décrémentation peuvent être appliqués aux pointeurs de tout type à l’exception du type `void*`.</span><span class="sxs-lookup"><span data-stu-id="2f26d-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="2f26d-106">L’application de l’opérateur d’incrémentation à un pointeur de type `pointer-type` a pour effet d’ajouter [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) à l’adresse contenue dans la variable pointeur.</span><span class="sxs-lookup"><span data-stu-id="2f26d-106">The effect of applying the increment operator to a pointer of the type `pointer-type` is to add [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="2f26d-107">L’application de l’opérateur de décrémentation à un pointeur de type `pointer-type` a pour effet de soustraire `sizeof` (`pointer-type`) à l’adresse contenue dans la variable pointeur.</span><span class="sxs-lookup"><span data-stu-id="2f26d-107">The effect of applying the decrement operator to a pointer of the type `pointer-type` is to subtract `sizeof` (`pointer-type`) from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="2f26d-108">Aucune exception n’est générée si l’opération produit un dépassement de capacité sur le domaine du pointeur, et le résultat dépend de l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="2f26d-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f26d-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f26d-109">Example</span></span>  
 <span data-ttu-id="2f26d-110">Dans cet exemple, vous parcourez un tableau en incrémentant le pointeur de la taille de `int`.</span><span class="sxs-lookup"><span data-stu-id="2f26d-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="2f26d-111">À chaque étape, vous affichez l’adresse et le contenu de l’élément de tableau.</span><span class="sxs-lookup"><span data-stu-id="2f26d-111">With each step, you display the address and the content of the array element.</span></span>  
  
 <span data-ttu-id="2f26d-112">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2f26d-112">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]</span></span>  
  
 <span data-ttu-id="2f26d-113">[!code-cs[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2f26d-113">[!code-cs[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]</span></span>  
  
 <span data-ttu-id="2f26d-114">**Valeur : 0 @ Adresse : 12860272**</span><span class="sxs-lookup"><span data-stu-id="2f26d-114">**Value:0 @ Address:12860272**</span></span>  
<span data-ttu-id="2f26d-115">**Valeur : 1 @ Adresse : 12860276**</span><span class="sxs-lookup"><span data-stu-id="2f26d-115">**Value:1 @ Address:12860276**</span></span>  
<span data-ttu-id="2f26d-116">**Valeur : 2 @ Adresse : 12860280**</span><span class="sxs-lookup"><span data-stu-id="2f26d-116">**Value:2 @ Address:12860280**</span></span>  
<span data-ttu-id="2f26d-117">**Valeur : 3 @ Adresse : 12860284**</span><span class="sxs-lookup"><span data-stu-id="2f26d-117">**Value:3 @ Address:12860284**</span></span>  
<span data-ttu-id="2f26d-118">**Valeur : 4 @ Adresse : 12860288**</span><span class="sxs-lookup"><span data-stu-id="2f26d-118">**Value:4 @ Address:12860288**</span></span>   
## <a name="see-also"></a><span data-ttu-id="2f26d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f26d-119">See Also</span></span>  
 <span data-ttu-id="2f26d-120">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2f26d-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2f26d-121">[Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="2f26d-121">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="2f26d-122">[Opérateurs C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="2f26d-122">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="2f26d-123">[Manipulation de pointeurs](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md) </span><span class="sxs-lookup"><span data-stu-id="2f26d-123">[Manipulating Pointers](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md) </span></span>  
 <span data-ttu-id="2f26d-124">[Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="2f26d-124">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="2f26d-125">[Types](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="2f26d-125">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="2f26d-126">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="2f26d-126">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="2f26d-127">[fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="2f26d-127">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="2f26d-128">stackalloc</span><span class="sxs-lookup"><span data-stu-id="2f26d-128">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

