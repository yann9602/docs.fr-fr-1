---
title: "break (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- break
- break_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: 21
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
ms.openlocfilehash: 73f6b6a37513b3aed796d811672fa43fa9e1c0b1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="break-c-reference"></a><span data-ttu-id="3f006-102">break (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3f006-102">break (C# Reference)</span></span>
<span data-ttu-id="3f006-103">L’instruction `break` termine la boucle englobante ou l’instruction [switch](../../../csharp/language-reference/keywords/switch.md) la plus proche dans laquelle elle figure.</span><span class="sxs-lookup"><span data-stu-id="3f006-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="3f006-104">Le contrôle est passé à l’instruction qui suit l’instruction terminée, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="3f006-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f006-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f006-105">Example</span></span>  
 <span data-ttu-id="3f006-106">Dans cet exemple, l’instruction conditionnelle contient un compteur qui est supposé compter de 1 à 100. Toutefois, l’instruction `break` termine la boucle après le chiffre 4.</span><span class="sxs-lookup"><span data-stu-id="3f006-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>  
  
 <span data-ttu-id="3f006-107">[!code-cs[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3f006-107">[!code-cs[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f006-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f006-108">Example</span></span>  
 <span data-ttu-id="3f006-109">Dans cet exemple, l’instruction `break` est utilisée pour sortir d’une boucle imbriquée interne et passer le contrôle à la boucle externe.</span><span class="sxs-lookup"><span data-stu-id="3f006-109">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>  
  
 <span data-ttu-id="3f006-110">[!code-cs[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="3f006-110">[!code-cs[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f006-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f006-111">Example</span></span>  
 <span data-ttu-id="3f006-112">Cet exemple illustre l’utilisation de `break` dans une instruction [switch](../../../csharp/language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="3f006-112">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 <span data-ttu-id="3f006-113">[!code-cs[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="3f006-113">[!code-cs[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]</span></span>  
  
 <span data-ttu-id="3f006-114">Si vous aviez entré `4`, le résultat serait le suivant :</span><span class="sxs-lookup"><span data-stu-id="3f006-114">If you entered `4`, the output would be:</span></span>  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="3f006-115">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3f006-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f006-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f006-116">See Also</span></span>  
 <span data-ttu-id="3f006-117">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f006-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="3f006-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f006-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="3f006-119">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f006-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="3f006-120">[switch](../../../csharp/language-reference/keywords/switch.md) </span><span class="sxs-lookup"><span data-stu-id="3f006-120">[switch](../../../csharp/language-reference/keywords/switch.md) </span></span>  
 <span data-ttu-id="3f006-121">[Instructions de saut](../../../csharp/language-reference/keywords/jump-statements.md) </span><span class="sxs-lookup"><span data-stu-id="3f006-121">[Jump Statements](../../../csharp/language-reference/keywords/jump-statements.md) </span></span>  
 [<span data-ttu-id="3f006-122">Instructions d’itération</span><span class="sxs-lookup"><span data-stu-id="3f006-122">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)

