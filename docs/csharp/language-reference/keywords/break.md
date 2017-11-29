---
title: "break (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords: break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b533d325be41683ed6f56e9e63b3c11ddde9cb17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="break-c-reference"></a><span data-ttu-id="27e20-102">break (référence C#)</span><span class="sxs-lookup"><span data-stu-id="27e20-102">break (C# Reference)</span></span>
<span data-ttu-id="27e20-103">L’instruction `break` termine la boucle englobante ou l’instruction [switch](../../../csharp/language-reference/keywords/switch.md) la plus proche dans laquelle elle figure.</span><span class="sxs-lookup"><span data-stu-id="27e20-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="27e20-104">Le contrôle est passé à l’instruction qui suit l’instruction terminée, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="27e20-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27e20-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="27e20-105">Example</span></span>  
 <span data-ttu-id="27e20-106">Dans cet exemple, l’instruction conditionnelle contient un compteur qui est supposé compter de 1 à 100. Toutefois, l’instruction `break` termine la boucle après le chiffre 4.</span><span class="sxs-lookup"><span data-stu-id="27e20-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="27e20-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="27e20-107">Example</span></span>  
 <span data-ttu-id="27e20-108">Dans cet exemple, l’instruction `break` est utilisée pour sortir d’une boucle imbriquée interne et passer le contrôle à la boucle externe.</span><span class="sxs-lookup"><span data-stu-id="27e20-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="27e20-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="27e20-109">Example</span></span>  
 <span data-ttu-id="27e20-110">Cet exemple illustre l’utilisation de `break` dans une instruction [switch](../../../csharp/language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="27e20-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 <span data-ttu-id="27e20-111">Si vous aviez entré `4`, le résultat serait le suivant :</span><span class="sxs-lookup"><span data-stu-id="27e20-111">If you entered `4`, the output would be:</span></span>  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="27e20-112">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="27e20-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="27e20-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27e20-113">See Also</span></span>  
 [<span data-ttu-id="27e20-114">Référence C#</span><span class="sxs-lookup"><span data-stu-id="27e20-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="27e20-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="27e20-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="27e20-116">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="27e20-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="27e20-117">switch</span><span class="sxs-lookup"><span data-stu-id="27e20-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)  
 [<span data-ttu-id="27e20-118">Instructions de saut</span><span class="sxs-lookup"><span data-stu-id="27e20-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)  
 [<span data-ttu-id="27e20-119">Instructions d’itération</span><span class="sxs-lookup"><span data-stu-id="27e20-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
