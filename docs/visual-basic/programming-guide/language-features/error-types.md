---
title: "Types d’erreurs (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors, Visual Basic
- run-time errors, types of errors
- syntax errors, Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: 13
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
ms.openlocfilehash: 51cf5820e79ff9467357619d4f5b067bc4168bfb
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="error-types-visual-basic"></a><span data-ttu-id="7f141-102">Types d'erreurs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f141-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="7f141-103">Dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], les erreurs (également appelé *exceptions*) se répartissent en trois catégories : erreurs de syntaxe, erreurs d’exécution et erreurs de logique.</span><span class="sxs-lookup"><span data-stu-id="7f141-103">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="7f141-104">Erreurs de syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f141-104">Syntax Errors</span></span>  
 <span data-ttu-id="7f141-105">*Erreurs de syntaxe* sont celles qui apparaissent lorsque vous écrivez du code.</span><span class="sxs-lookup"><span data-stu-id="7f141-105">*Syntax errors* are those that appear while you write code.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="7f141-106">vérifie votre code en cours de frappe dans les **éditeur de Code** fenêtre et vous avertit si vous commettez une erreur, comme un mot mal orthographié ou l’utilisation incorrecte d’un élément de langage.</span><span class="sxs-lookup"><span data-stu-id="7f141-106"> checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="7f141-107">Erreurs de syntaxe sont le type le plus courant d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="7f141-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="7f141-108">Vous pouvez les résoudre facilement dans l’environnement de codage dès qu’elles se produisent.</span><span class="sxs-lookup"><span data-stu-id="7f141-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f141-109">La `Option Explicit` instruction est d’éviter les erreurs de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="7f141-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="7f141-110">Il vous oblige à déclarer à l’avance toutes les variables à utiliser dans l’application.</span><span class="sxs-lookup"><span data-stu-id="7f141-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="7f141-111">Par conséquent, lorsque ces variables sont utilisées dans le code, les erreurs typographiques sont décelées immédiatement et peuvent être résolus.</span><span class="sxs-lookup"><span data-stu-id="7f141-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="7f141-112">Erreurs d’exécution</span><span class="sxs-lookup"><span data-stu-id="7f141-112">Run-Time Errors</span></span>  
 <span data-ttu-id="7f141-113">*Erreurs d’exécution* sont celles qui apparaissent uniquement lorsque vous compilez et exécutez votre code.</span><span class="sxs-lookup"><span data-stu-id="7f141-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="7f141-114">Ces impliquent du code qui semble être correct dans la mesure où il ne comporte aucune erreur de syntaxe, mais qui ne s’exécutera pas.</span><span class="sxs-lookup"><span data-stu-id="7f141-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="7f141-115">Par exemple, vous pouvez écrire correctement une ligne de code pour ouvrir un fichier.</span><span class="sxs-lookup"><span data-stu-id="7f141-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="7f141-116">Mais si le fichier est endommagé, l’application ne peut pas exécuter la `Open` et s’arrête en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7f141-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="7f141-117">Vous pouvez résoudre la plupart des erreurs d’exécution en réécrivant le code erroné, puis recompiler et exécuter à nouveau.</span><span class="sxs-lookup"><span data-stu-id="7f141-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="7f141-118">Erreurs de logique</span><span class="sxs-lookup"><span data-stu-id="7f141-118">Logic Errors</span></span>  
 <span data-ttu-id="7f141-119">*Erreurs de logique* sont celles qui apparaissent lorsque l’application est en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="7f141-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="7f141-120">Il s’agit de la plupart des résultats souvent indésirables ou inattendus en réponse aux actions de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7f141-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="7f141-121">Par exemple, une mauvaise touche ou une influence extérieure risque de votre application pour cesser de fonctionner dans les paramètres prévus ou complètement.</span><span class="sxs-lookup"><span data-stu-id="7f141-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="7f141-122">Erreurs de logique sont les plus difficiles à résoudre, car il n’est pas toujours évident de déterminer leur origine.</span><span class="sxs-lookup"><span data-stu-id="7f141-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f141-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f141-123">See Also</span></span>  
 <span data-ttu-id="7f141-124">[Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7f141-124">[Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span></span>  
<span data-ttu-id="7f141-125"> [Principes de base du débogueur](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)</span><span class="sxs-lookup"><span data-stu-id="7f141-125"> [Debugger Basics](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)</span></span>
