---
title: "Comment : obtenir l'adresse d'une variable (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="49291-102">Comment : obtenir l'adresse d'une variable (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="49291-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="49291-103">Pour obtenir l’adresse d’une expression unaire, qui est évaluée en tant que variable fixe, utilisez l’opérateur address-of :</span><span class="sxs-lookup"><span data-stu-id="49291-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator:</span></span>  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="49291-104">L’opérateur address-of peut être appliqué à une seule variable uniquement.</span><span class="sxs-lookup"><span data-stu-id="49291-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="49291-105">Si la variable peut être déplacée, vous pouvez utiliser l’[instruction fixed](../../../csharp/language-reference/keywords/fixed-statement.md) pour fixer temporairement la variable avant d’obtenir son adresse.</span><span class="sxs-lookup"><span data-stu-id="49291-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="49291-106">Il vous appartient de vérifier que la variable est initialisée.</span><span class="sxs-lookup"><span data-stu-id="49291-106">It is your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="49291-107">Le compilateur ne génère pas de message d’erreur si la variable n’est pas initialisée.</span><span class="sxs-lookup"><span data-stu-id="49291-107">The compiler will not issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="49291-108">Vous ne pouvez pas obtenir l’adresse d’une constante ou d’une valeur.</span><span class="sxs-lookup"><span data-stu-id="49291-108">You cannot get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49291-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="49291-109">Example</span></span>  
 <span data-ttu-id="49291-110">Dans cet exemple, un pointeur désignant `int`, `p`, est déclaré et se voit assigner l’adresse d’une variable entière, `number`.</span><span class="sxs-lookup"><span data-stu-id="49291-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="49291-111">La variable `number` est initialisée à la suite de l’assignation à *p.</span><span class="sxs-lookup"><span data-stu-id="49291-111">The variable `number` is initialized as a result of the assignment to *p.</span></span> <span data-ttu-id="49291-112">Si vous assortissez cette instruction d’assignation d’un commentaire, l’initialisation de la variable `number` est supprimée, mais aucune erreur n’est émise au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="49291-112">If you make this assignment statement a comment, the initialization of the variable `number` will be removed, but no compile-time error is issued.</span></span> <span data-ttu-id="49291-113">Notez l’utilisation de l’opérateur d’[accès de membre](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) `->` pour obtenir et afficher l’adresse stockée dans le pointeur.</span><span class="sxs-lookup"><span data-stu-id="49291-113">Notice the use of the [Member Access](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operator `->` to obtain and display the address stored in the pointer.</span></span>  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="49291-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49291-114">See Also</span></span>  
 [<span data-ttu-id="49291-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="49291-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="49291-116">Expressions de pointeur</span><span class="sxs-lookup"><span data-stu-id="49291-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="49291-117">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="49291-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="49291-118">Types</span><span class="sxs-lookup"><span data-stu-id="49291-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="49291-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="49291-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="49291-120">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="49291-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="49291-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="49291-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
