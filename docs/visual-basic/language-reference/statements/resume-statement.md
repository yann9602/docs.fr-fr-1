---
title: Resume, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cb4334f302c07c81b6b8a7d0626be08cc69b1ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="resume-statement"></a><span data-ttu-id="9ed43-102">Resume, instruction</span><span class="sxs-lookup"><span data-stu-id="9ed43-102">Resume Statement</span></span>
<span data-ttu-id="9ed43-103">Reprend l’exécution après qu’une routine de gestion des erreurs est terminée.</span><span class="sxs-lookup"><span data-stu-id="9ed43-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="9ed43-104">Nous vous suggérons d’utiliser la gestion structurée des exceptions dans votre code autant que possible, au lieu d’utiliser la gestion des exceptions structurées et `On Error` et `Resume` instructions.</span><span class="sxs-lookup"><span data-stu-id="9ed43-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="9ed43-105">Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9ed43-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed43-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ed43-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="9ed43-107">Composants</span><span class="sxs-lookup"><span data-stu-id="9ed43-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="9ed43-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9ed43-108">Required.</span></span> <span data-ttu-id="9ed43-109">Si l’erreur s’est produite dans la même procédure que le Gestionnaire d’erreurs, l’exécution se poursuit avec l’instruction qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="9ed43-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="9ed43-110">Si l’erreur s’est produite dans une procédure appelée, l’exécution reprend à l’instruction qui a appelé la procédure contenant la routine de gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="9ed43-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="9ed43-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="9ed43-111">Optional.</span></span> <span data-ttu-id="9ed43-112">Si l’erreur s’est produite dans la même procédure que le Gestionnaire d’erreurs, l’exécution se poursuit avec l’instruction qui suit immédiatement l’instruction ayant provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="9ed43-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="9ed43-113">Si l’erreur s’est produite dans une procédure appelée, l’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé la procédure contenant la routine de gestion des erreurs (ou `On Error Resume Next` instruction).</span><span class="sxs-lookup"><span data-stu-id="9ed43-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="9ed43-114">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="9ed43-114">Optional.</span></span> <span data-ttu-id="9ed43-115">L’exécution se poursuit à la ligne spécifiée dans le champ obligatoire `line` argument.</span><span class="sxs-lookup"><span data-stu-id="9ed43-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="9ed43-116">Le `line` argument est une étiquette de ligne ou un numéro de ligne et doit se trouver dans la même procédure que le Gestionnaire d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="9ed43-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ed43-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="9ed43-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ed43-118">Nous vous recommandons d’utiliser Gestion structurée des exceptions dans votre code autant que possible, au lieu d’utiliser la gestion des exceptions structurées et `On Error` et `Resume` instructions.</span><span class="sxs-lookup"><span data-stu-id="9ed43-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="9ed43-119">Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9ed43-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="9ed43-120">Si vous utilisez un `Resume` instruction n’importe où autre que dans une routine de gestion des erreurs, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="9ed43-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="9ed43-121">Le `Resume` instruction ne peut pas être utilisée dans une procédure qui contient un `Try...Catch...Finally` instruction.</span><span class="sxs-lookup"><span data-stu-id="9ed43-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ed43-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ed43-122">Example</span></span>  
 <span data-ttu-id="9ed43-123">Cet exemple utilise la `Resume` instruction pour terminer la gestion des erreurs dans une procédure, puis reprend l’exécution avec l’instruction qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="9ed43-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="9ed43-124">L’erreur numéro 55 est générée pour illustrer l’utilisation de la `Resume` instruction.</span><span class="sxs-lookup"><span data-stu-id="9ed43-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="9ed43-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9ed43-125">Requirements</span></span>  
 <span data-ttu-id="9ed43-126">**Namespace :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="9ed43-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="9ed43-127">**Assembly :** bibliothèque Visual Basic Runtime (dans Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="9ed43-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed43-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ed43-128">See Also</span></span>  
 [<span data-ttu-id="9ed43-129">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="9ed43-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="9ed43-130">Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="9ed43-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)  
 [<span data-ttu-id="9ed43-131">On Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="9ed43-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
