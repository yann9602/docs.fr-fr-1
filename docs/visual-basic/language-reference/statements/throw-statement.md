---
title: Throw, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50ada551c32b8296f0dad2ae929ca9c81a14a711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="fff6b-102">Throw, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fff6b-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="fff6b-103">Lève une exception dans une procédure.</span><span class="sxs-lookup"><span data-stu-id="fff6b-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fff6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fff6b-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="fff6b-105">Élément</span><span class="sxs-lookup"><span data-stu-id="fff6b-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="fff6b-106">Fournit des informations relatives à l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="fff6b-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="fff6b-107">Facultatif lorsqu’il réside dans un `Catch` instruction, requise dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="fff6b-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fff6b-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="fff6b-108">Remarks</span></span>  
 <span data-ttu-id="fff6b-109">Le `Throw` instruction lève une exception que vous pouvez gérer à l’aide du code de gestion des exceptions structurée (`Try`... `Catch`... `Finally`) ou le code de gestion des exceptions structurée (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="fff6b-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="fff6b-110">Vous pouvez utiliser la `Throw` instruction pour intercepter les erreurs dans votre code, car Visual Basic monte dans la pile des appels jusqu'à ce qu’il trouve le code de gestion des exceptions approprié.</span><span class="sxs-lookup"><span data-stu-id="fff6b-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="fff6b-111">A `Throw` instruction sans expression peut uniquement être utilisée dans un `Catch` instruction, dans lequel cas l’instruction lève à nouveau l’exception qui est gérée par le `Catch` instruction.</span><span class="sxs-lookup"><span data-stu-id="fff6b-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="fff6b-112">Le `Throw` instruction rétablit la pile des appels pour le `expression` exception.</span><span class="sxs-lookup"><span data-stu-id="fff6b-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="fff6b-113">Si `expression` n’est pas fourni, la pile des appels reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="fff6b-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="fff6b-114">Vous pouvez accéder à la pile des appels de l’exception via la <xref:System.Exception.StackTrace%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="fff6b-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fff6b-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="fff6b-115">Example</span></span>  
 <span data-ttu-id="fff6b-116">Le code suivant utilise la `Throw` instruction pour lever une exception :</span><span class="sxs-lookup"><span data-stu-id="fff6b-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="fff6b-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fff6b-117">Requirements</span></span>  
 <span data-ttu-id="fff6b-118">**Namespace :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="fff6b-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="fff6b-119">**Module :**`Interaction`</span><span class="sxs-lookup"><span data-stu-id="fff6b-119">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="fff6b-120">**Assembly :** bibliothèque Visual Basic Runtime (dans Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="fff6b-120">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff6b-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fff6b-121">See Also</span></span>  
 [<span data-ttu-id="fff6b-122">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="fff6b-122">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="fff6b-123">On Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="fff6b-123">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
