---
title: "Évaluation de la fonction est désactivée, car une évaluation de fonction précédente a expiré | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
dev_langs:
- VB
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 127f89f4c7ddaf794f58707d8925731a511f3740
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="0ee58-102">L'évaluation de la fonction est désactivée, car une évaluation de fonction précédente a expiré</span><span class="sxs-lookup"><span data-stu-id="0ee58-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="0ee58-103">Évaluation de la fonction est désactivée, car une évaluation de fonction précédente a expiré.</span><span class="sxs-lookup"><span data-stu-id="0ee58-103">Function evaluation is disabled because a previous function evaluation timed out.</span></span> <span data-ttu-id="0ee58-104">Pour réactiver l’évaluation de fonction, pas à pas, ou redémarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="0ee58-104">To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="0ee58-105">Dans le débogueur Visual Studio, une expression spécifie un appel de procédure, mais une autre version d’évaluation a expiré.</span><span class="sxs-lookup"><span data-stu-id="0ee58-105">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="0ee58-106">Causes possibles d’un appel de procédure pour le délai d’attente sont une boucle infinie ou *boucle sans fin*.</span><span class="sxs-lookup"><span data-stu-id="0ee58-106">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="0ee58-107">Pour plus d’informations, consultez la page [pour... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0ee58-107">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="0ee58-108">Un cas particulier d’une boucle infinie est *récursivité*.</span><span class="sxs-lookup"><span data-stu-id="0ee58-108">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="0ee58-109">Pour plus d’informations, consultez [procédures récursives](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0ee58-109">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="0ee58-110">**ID d’erreur :** BC30957</span><span class="sxs-lookup"><span data-stu-id="0ee58-110">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0ee58-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="0ee58-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="0ee58-112">Si possible, déterminez ce que l’évaluation de fonction précédente a été et à cause de son délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="0ee58-112">If possible, determine what the previous function evaluation was and what caused it to time out.</span></span> <span data-ttu-id="0ee58-113">Sinon, vous pouvez rencontrer cette erreur à nouveau.</span><span class="sxs-lookup"><span data-stu-id="0ee58-113">Otherwise, you might encounter this error again.</span></span>  
  
2.  <span data-ttu-id="0ee58-114">Soit à nouveau, l’étape du débogueur ou arrêter et redémarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="0ee58-114">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ee58-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ee58-115">See Also</span></span>  
 <span data-ttu-id="0ee58-116">[Débogage dans Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="0ee58-116">[Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span></span>  
<span data-ttu-id="0ee58-117"> [Naviguer dans le code avec le débogueur](https://docs.microsoft.com/visualstudio/debugger/navigating-through-code-with-the-debugger)</span><span class="sxs-lookup"><span data-stu-id="0ee58-117"> [Navigating through Code with the Debugger](https://docs.microsoft.com/visualstudio/debugger/navigating-through-code-with-the-debugger)</span></span>
