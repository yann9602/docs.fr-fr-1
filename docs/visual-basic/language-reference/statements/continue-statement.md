---
title: Continue, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a47819600a6c1d58f09c2f8ed3443632e9dab68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="9b6d3-102">Continue, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b6d3-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="9b6d3-103">Transfère le contrôle immédiatement à l’itération suivante d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="9b6d3-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b6d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b6d3-104">Syntax</span></span>  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="9b6d3-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="9b6d3-105">Remarks</span></span>  
 <span data-ttu-id="9b6d3-106">Vous pouvez transférer à partir d’à l’intérieur d’un `Do`, `For`, ou `While` boucle à l’itération suivante de cette boucle.</span><span class="sxs-lookup"><span data-stu-id="9b6d3-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="9b6d3-107">Contrôle passe immédiatement au test de condition de la boucle, ce qui revient à effectuer un transfert à la `For` ou `While` instruction, ou à la `Do` ou `Loop` instruction qui contient le `Until` ou `While` clause.</span><span class="sxs-lookup"><span data-stu-id="9b6d3-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="9b6d3-108">Vous pouvez utiliser `Continue` à n’importe quel emplacement de la boucle qui autorise les transferts.</span><span class="sxs-lookup"><span data-stu-id="9b6d3-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="9b6d3-109">Les règles qui autorisent le transfert de contrôle sont identiques à celles de la [instruction GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9b6d3-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="9b6d3-110">Par exemple, si une boucle est entièrement contenue dans un `Try` bloc, un `Catch` bloc, ou un `Finally` bloc, vous pouvez utiliser `Continue` pour transférer hors de la boucle.</span><span class="sxs-lookup"><span data-stu-id="9b6d3-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="9b6d3-111">If, d’autre part, le `Try`... `End Try` structure est contenue dans la boucle, vous ne pouvez pas utiliser `Continue` pour transférer le contrôle de la `Finally` bloc et vous pouvez l’utiliser pour transférer d’un `Try` ou `Catch` bloquer uniquement si vous transférez complètement hors de la `Try`... `End Try` structure.</span><span class="sxs-lookup"><span data-stu-id="9b6d3-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="9b6d3-112">Si vous avez des boucles imbriquées du même type, par exemple un `Do` boucle dans une autre `Do` boucle, une `Continue Do` instruction passe à l’itération suivante de la plus profonde `Do` boucle qui le contient.</span><span class="sxs-lookup"><span data-stu-id="9b6d3-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="9b6d3-113">Vous ne pouvez pas utiliser `Continue` pour passer à l’itération suivante d’une boucle conteneur du même type.</span><span class="sxs-lookup"><span data-stu-id="9b6d3-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="9b6d3-114">Si vous avez des boucles imbriquées de types différents, par exemple un `Do` mises en boucle dans un `For` boucle, vous pouvez passer à l’itération suivante d’une boucle à l’aide `Continue Do` ou `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="9b6d3-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b6d3-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="9b6d3-115">Example</span></span>  
 <span data-ttu-id="9b6d3-116">Le code suivant exemple utilise la `Continue While` instruction pour passer à la colonne suivante d’un tableau si un diviseur est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="9b6d3-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="9b6d3-117">Le `Continue While` se trouve dans un `For` boucle.</span><span class="sxs-lookup"><span data-stu-id="9b6d3-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="9b6d3-118">Elle transfère vers le `While col < lastcol` instruction, qui est l’itération suivante de la plus profonde `While` boucle qui contient le `For` boucle.</span><span class="sxs-lookup"><span data-stu-id="9b6d3-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9b6d3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b6d3-119">See Also</span></span>  
 [<span data-ttu-id="9b6d3-120">Do...Loop (instruction)</span><span class="sxs-lookup"><span data-stu-id="9b6d3-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="9b6d3-121">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="9b6d3-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="9b6d3-122">While...End While (instruction)</span><span class="sxs-lookup"><span data-stu-id="9b6d3-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="9b6d3-123">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="9b6d3-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
