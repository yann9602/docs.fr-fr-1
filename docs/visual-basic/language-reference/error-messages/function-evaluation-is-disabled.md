---
title: "L'évaluation de la fonction est désactivée, car une évaluation de fonction précédente a expiré"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords: BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05067e730486b443b7a508adb499f34c060d5093
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="8d439-102">L'évaluation de la fonction est désactivée, car une évaluation de fonction précédente a expiré</span><span class="sxs-lookup"><span data-stu-id="8d439-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="8d439-103">L’évaluation de fonction est désactivée, car une évaluation de fonction précédente a expiré. Pour réactiver l’évaluation de fonction, pas à pas, ou redémarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="8d439-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="8d439-104">Dans le débogueur Visual Studio, une expression spécifie un appel de procédure, mais une autre évaluation a expiré.</span><span class="sxs-lookup"><span data-stu-id="8d439-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="8d439-105">Causes possibles d’un appel de procédure pour le délai d’attente une boucle infinie ou *boucle sans fin*.</span><span class="sxs-lookup"><span data-stu-id="8d439-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="8d439-106">Pour plus d’informations, consultez [pour... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8d439-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="8d439-107">Est un cas particulier d’une boucle infinie *récursivité*.</span><span class="sxs-lookup"><span data-stu-id="8d439-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="8d439-108">Pour plus d’informations, consultez [procédures récursives](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8d439-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="8d439-109">**ID d’erreur :** BC30957</span><span class="sxs-lookup"><span data-stu-id="8d439-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8d439-110">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="8d439-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="8d439-111">Si possible, déterminez ce que l’évaluation de fonction précédente a été et la cause de son délai d’attente. Sinon, vous pouvez rencontrer cette erreur, à nouveau.</span><span class="sxs-lookup"><span data-stu-id="8d439-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2.  <span data-ttu-id="8d439-112">Soit à nouveau, l’étape du débogueur ou arrêter et redémarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="8d439-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d439-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d439-113">See Also</span></span>  
 [<span data-ttu-id="8d439-114">Débogage dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8d439-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="8d439-115">Naviguer dans le code avec le débogueur</span><span class="sxs-lookup"><span data-stu-id="8d439-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
