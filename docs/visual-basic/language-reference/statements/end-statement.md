---
title: End, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b692409f2895f5e9b713c57fc35ff2def40bce75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="end-statement"></a><span data-ttu-id="eadd1-102">End, instruction</span><span class="sxs-lookup"><span data-stu-id="eadd1-102">End Statement</span></span>
<span data-ttu-id="eadd1-103">Termine l’exécution immédiatement.</span><span class="sxs-lookup"><span data-stu-id="eadd1-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eadd1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eadd1-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="eadd1-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="eadd1-105">Remarks</span></span>  
 <span data-ttu-id="eadd1-106">Vous pouvez placer le `End` instruction n’importe où dans une procédure pour forcer l’application entière pour interrompre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="eadd1-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="eadd1-107">`End`Ferme tous les fichiers ouverts avec un `Open` instruction et efface toutes les variables de l’application.</span><span class="sxs-lookup"><span data-stu-id="eadd1-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="eadd1-108">L’application se ferme dès qu’il n’y aucun programme contenant des références à ses objets et son code est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="eadd1-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eadd1-109">Le `End` instruction met immédiatement fin à l’exécution de code et n’appelle pas la `Dispose` ou `Finalize` (méthode), ou tout autre code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eadd1-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="eadd1-110">Références d’objet détenus par d’autres programmes sont invalidés.</span><span class="sxs-lookup"><span data-stu-id="eadd1-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="eadd1-111">Si un `End` est rencontrée dans une `Try` ou `Catch` bloc, le contrôle ne passe pas correspondant `Finally` bloc.</span><span class="sxs-lookup"><span data-stu-id="eadd1-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="eadd1-112">Le `Stop` instruction interrompt l’exécution, mais contrairement à `End`, il ne pas fermer tous les fichiers ou effacer toutes les variables, sauf si elle est placée dans un fichier exécutable compilé (.exe).</span><span class="sxs-lookup"><span data-stu-id="eadd1-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="eadd1-113">Étant donné que `End` met fin à votre application sans se préoccuper des ressources qui peuvent être ouverts, vous devez tenter de fermer correctement avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="eadd1-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="eadd1-114">Par exemple, si votre application comporte des formulaires ouverts, vous devez les fermer avant de contrôle atteint la `End` instruction.</span><span class="sxs-lookup"><span data-stu-id="eadd1-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="eadd1-115">Vous devez utiliser `End` avec parcimonie et uniquement lorsque vous devez arrêter immédiatement.</span><span class="sxs-lookup"><span data-stu-id="eadd1-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="eadd1-116">Les méthodes normales pour mettre fin à une procédure ([instruction Return](../../../visual-basic/language-reference/statements/return-statement.md) et [instruction Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) permettent de fermer correctement la procédure, mais également le code appelant.</span><span class="sxs-lookup"><span data-stu-id="eadd1-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="eadd1-117">Par exemple, une application console, peut simplement `Return` à partir de la `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="eadd1-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eadd1-118">Le `End` instruction appelle la <xref:System.Environment.Exit%2A> méthode de la <xref:System.Environment> classe dans le <xref:System> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="eadd1-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="eadd1-119"><xref:System.Environment.Exit%2A>exige que vous disposiez `UnmanagedCode` autorisation.</span><span class="sxs-lookup"><span data-stu-id="eadd1-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="eadd1-120">Si vous ne le faites pas, un <xref:System.Security.SecurityException> erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="eadd1-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="eadd1-121">Lorsqu’il est suivi par un mot clé supplémentaire, [fin \<mot clé > instruction](../../../visual-basic/language-reference/statements/end-keyword-statement.md) délimite la fin de la définition de la procédure appropriée ou le bloc.</span><span class="sxs-lookup"><span data-stu-id="eadd1-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="eadd1-122">Par exemple, `End Function` termine la définition d’un `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="eadd1-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eadd1-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="eadd1-123">Example</span></span>  
 <span data-ttu-id="eadd1-124">L’exemple suivant utilise la `End` instruction pour mettre fin à l’exécution de code si l’utilisateur le demande.</span><span class="sxs-lookup"><span data-stu-id="eadd1-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="eadd1-125">Remarques sur le développement Smart Device</span><span class="sxs-lookup"><span data-stu-id="eadd1-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="eadd1-126">Cette instruction n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="eadd1-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eadd1-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eadd1-127">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [<span data-ttu-id="eadd1-128">Stop (instruction)</span><span class="sxs-lookup"><span data-stu-id="eadd1-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [<span data-ttu-id="eadd1-129">Fin \<mot clé > instruction</span><span class="sxs-lookup"><span data-stu-id="eadd1-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
