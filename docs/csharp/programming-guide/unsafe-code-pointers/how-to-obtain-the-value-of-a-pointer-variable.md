---
title: "Guide pratique pour obtenir la valeur d’une variable de pointeur (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: 17
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
ms.openlocfilehash: 4cff42de07f2edb279ddd1cafefe9f4b67a38ce1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="a757c-102">Guide pratique pour obtenir la valeur d’une variable de pointeur (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a757c-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="a757c-103">Utilisez l’opérateur d’indirection de pointeur pour obtenir la variable à l’emplacement désigné par un pointeur.</span><span class="sxs-lookup"><span data-stu-id="a757c-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="a757c-104">L’expression prend la forme suivante, `p` étant un type de pointeur :</span><span class="sxs-lookup"><span data-stu-id="a757c-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="a757c-105">Vous ne pouvez pas utiliser l’opérateur d’indirection unaire sur une expression d’un autre type que le type de pointeur.</span><span class="sxs-lookup"><span data-stu-id="a757c-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="a757c-106">Par ailleurs, vous ne pouvez pas l’appliquer à un pointeur [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="a757c-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="a757c-107">Quand vous appliquez l’opérateur d’indirection à un pointeur [null](../../../csharp/language-reference/keywords/null.md), le résultat dépend de l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="a757c-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a757c-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="a757c-108">Example</span></span>  
 <span data-ttu-id="a757c-109">Dans l’exemple suivant, une variable de type `char` est accessible via des pointeurs de types différents.</span><span class="sxs-lookup"><span data-stu-id="a757c-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="a757c-110">Notez que l’adresse de `theChar` peut varier d’une exécution à l’autre, car l’adresse physique allouée à une variable peut changer.</span><span class="sxs-lookup"><span data-stu-id="a757c-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 <span data-ttu-id="a757c-111">[!code-cs[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a757c-111">[!code-cs[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]</span></span>  
  
 <span data-ttu-id="a757c-112">[!code-cs[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="a757c-112">[!code-cs[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]</span></span>  
  
 <span data-ttu-id="a757c-113">**Value of theChar = Z** </span><span class="sxs-lookup"><span data-stu-id="a757c-113">**Value of theChar = Z** </span></span>  
<span data-ttu-id="a757c-114">**Address of theChar = 12F718**</span><span class="sxs-lookup"><span data-stu-id="a757c-114">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="a757c-115">**Value of pChar = Z** </span><span class="sxs-lookup"><span data-stu-id="a757c-115">**Value of pChar = Z** </span></span>  
<span data-ttu-id="a757c-116">**Value of pInt = 90**</span><span class="sxs-lookup"><span data-stu-id="a757c-116">**Value of pInt = 90**</span></span>    
## <a name="see-also"></a><span data-ttu-id="a757c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a757c-117">See Also</span></span>  
 <span data-ttu-id="a757c-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a757c-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="a757c-119">[Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="a757c-119">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="a757c-120">[Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="a757c-120">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="a757c-121">[Types](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="a757c-121">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="a757c-122">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="a757c-122">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="a757c-123">[fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a757c-123">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="a757c-124">stackalloc</span><span class="sxs-lookup"><span data-stu-id="a757c-124">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

