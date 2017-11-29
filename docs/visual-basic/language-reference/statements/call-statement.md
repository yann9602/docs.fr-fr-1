---
title: Call, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72450fd6f931f36f640d3e384a6fd38d57a7a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="37c51-102">Call, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37c51-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="37c51-103">Transfère le contrôle à un `Function`, `Sub`, ou de la procédure de la bibliothèque de liens dynamiques (DLL).</span><span class="sxs-lookup"><span data-stu-id="37c51-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37c51-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="37c51-105">Composants</span><span class="sxs-lookup"><span data-stu-id="37c51-105">Parts</span></span>  
 `procedureName`  
 <span data-ttu-id="37c51-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="37c51-106">Required.</span></span> <span data-ttu-id="37c51-107">Nom de la procédure à appeler.</span><span class="sxs-lookup"><span data-stu-id="37c51-107">Name of the procedure to call.</span></span>  
  
 `argumentList`  
 <span data-ttu-id="37c51-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="37c51-108">Optional.</span></span> <span data-ttu-id="37c51-109">Liste de variables ou d’expressions représentant les arguments passés à la procédure lorsqu’elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="37c51-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="37c51-110">Plusieurs arguments sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="37c51-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="37c51-111">Si vous incluez `argumentList`, vous devez le placer entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="37c51-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37c51-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="37c51-112">Remarks</span></span>  
 <span data-ttu-id="37c51-113">Vous pouvez utiliser le `Call` mot clé lorsque vous appelez une procédure.</span><span class="sxs-lookup"><span data-stu-id="37c51-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="37c51-114">Pour la plupart des appels de procédure, vous n’êtes pas obligé d’utiliser ce mot clé.</span><span class="sxs-lookup"><span data-stu-id="37c51-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="37c51-115">Vous utilisez généralement la `Call` mot clé lorsque l’expression appelée ne commence pas par un identificateur.</span><span class="sxs-lookup"><span data-stu-id="37c51-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="37c51-116">Utilisation de la `Call` n’est pas recommandé de mot clé pour d’autres utilisations.</span><span class="sxs-lookup"><span data-stu-id="37c51-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="37c51-117">Si la procédure retourne une valeur, la `Call` instruction ignore.</span><span class="sxs-lookup"><span data-stu-id="37c51-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37c51-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="37c51-118">Example</span></span>  
 <span data-ttu-id="37c51-119">Le code suivant montre deux exemples où le `Call` mot clé est nécessaire pour appeler une procédure.</span><span class="sxs-lookup"><span data-stu-id="37c51-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="37c51-120">Dans les deux exemples, l’expression appelée ne commence pas par un identificateur.</span><span class="sxs-lookup"><span data-stu-id="37c51-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="37c51-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37c51-121">See Also</span></span>  
 [<span data-ttu-id="37c51-122">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="37c51-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="37c51-123">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="37c51-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="37c51-124">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="37c51-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="37c51-125">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="37c51-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
