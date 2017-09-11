---
title: "Guide pratique pour obtenir l’adresse d’une variable (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: 19
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
ms.openlocfilehash: 169f68cc80b7a27427a9987942e66e0ba9ed1a02
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="ac51c-102">Guide pratique pour obtenir l’adresse d’une variable (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ac51c-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="ac51c-103">Pour obtenir l’adresse d’une expression unaire, qui est évaluée en tant que variable fixe, utilisez l’opérateur address-of :</span><span class="sxs-lookup"><span data-stu-id="ac51c-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator:</span></span>  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="ac51c-104">L’opérateur address-of peut être appliqué à une seule variable uniquement.</span><span class="sxs-lookup"><span data-stu-id="ac51c-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="ac51c-105">Si la variable peut être déplacée, vous pouvez utiliser l’[instruction fixed](../../../csharp/language-reference/keywords/fixed-statement.md) pour fixer temporairement la variable avant d’obtenir son adresse.</span><span class="sxs-lookup"><span data-stu-id="ac51c-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="ac51c-106">Il vous appartient de vérifier que la variable est initialisée.</span><span class="sxs-lookup"><span data-stu-id="ac51c-106">It is your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="ac51c-107">Le compilateur ne génère pas de message d’erreur si la variable n’est pas initialisée.</span><span class="sxs-lookup"><span data-stu-id="ac51c-107">The compiler will not issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="ac51c-108">Vous ne pouvez pas obtenir l’adresse d’une constante ou d’une valeur.</span><span class="sxs-lookup"><span data-stu-id="ac51c-108">You cannot get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac51c-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac51c-109">Example</span></span>  
 <span data-ttu-id="ac51c-110">Dans cet exemple, un pointeur désignant `int`, `p`, est déclaré et se voit assigner l’adresse d’une variable entière, `number`.</span><span class="sxs-lookup"><span data-stu-id="ac51c-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="ac51c-111">La variable `number` est initialisée à la suite de l’assignation à *p.</span><span class="sxs-lookup"><span data-stu-id="ac51c-111">The variable `number` is initialized as a result of the assignment to *p.</span></span> <span data-ttu-id="ac51c-112">Si vous assortissez cette instruction d’assignation d’un commentaire, l’initialisation de la variable `number` est supprimée, mais aucune erreur n’est émise au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="ac51c-112">If you make this assignment statement a comment, the initialization of the variable `number` will be removed, but no compile-time error is issued.</span></span> <span data-ttu-id="ac51c-113">Notez l’utilisation de l’opérateur d’[accès de membre](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) `->` pour obtenir et afficher l’adresse stockée dans le pointeur.</span><span class="sxs-lookup"><span data-stu-id="ac51c-113">Notice the use of the [Member Access](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operator `->` to obtain and display the address stored in the pointer.</span></span>  
  
 <span data-ttu-id="ac51c-114">[!code-cs[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ac51c-114">[!code-cs[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]</span></span>  
  
 <span data-ttu-id="ac51c-115">[!code-cs[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ac51c-115">[!code-cs[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac51c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac51c-116">See Also</span></span>  
 <span data-ttu-id="ac51c-117">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac51c-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ac51c-118">[Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="ac51c-118">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="ac51c-119">[Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="ac51c-119">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="ac51c-120">[Types](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="ac51c-120">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="ac51c-121">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="ac51c-121">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="ac51c-122">[fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ac51c-122">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="ac51c-123">stackalloc</span><span class="sxs-lookup"><span data-stu-id="ac51c-123">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

