---
title: Types d'erreurs (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e01ed588d284a475a537a5fcf5ca506d25ca69f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="a05e3-102">Types d'erreurs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a05e3-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="a05e3-103">Dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], les erreurs (également appelé *exceptions*) se répartissent en trois catégories : erreurs de syntaxe, les erreurs d’exécution et les erreurs de logique.</span><span class="sxs-lookup"><span data-stu-id="a05e3-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="a05e3-104">Erreurs de syntaxe</span><span class="sxs-lookup"><span data-stu-id="a05e3-104">Syntax Errors</span></span>  
 <span data-ttu-id="a05e3-105">*Erreurs de syntaxe* sont celles qui s’affichent lorsque vous écrivez du code.</span><span class="sxs-lookup"><span data-stu-id="a05e3-105">*Syntax errors* are those that appear while you write code.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="a05e3-106">vérifie votre code en cours de frappe dans le **éditeur de Code** fenêtre et vous avertit si vous commettez une erreur, comme un mot mal orthographié ou l’utilisation incorrecte d’un élément de langage.</span><span class="sxs-lookup"><span data-stu-id="a05e3-106"> checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="a05e3-107">Erreurs de syntaxe sont le type d’erreurs le plus courant.</span><span class="sxs-lookup"><span data-stu-id="a05e3-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="a05e3-108">Vous pouvez les résoudre facilement dans l’environnement de codage dès qu’elles se produisent.</span><span class="sxs-lookup"><span data-stu-id="a05e3-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a05e3-109">La `Option Explicit` instruction est un des moyens d’éviter les erreurs de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="a05e3-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="a05e3-110">Il vous oblige à déclarer à l’avance, toutes les variables à utiliser dans l’application.</span><span class="sxs-lookup"><span data-stu-id="a05e3-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="a05e3-111">Par conséquent, lorsque ces variables sont utilisées dans le code, les erreurs typographiques sont interceptées immédiatement et peuvent être corrigés.</span><span class="sxs-lookup"><span data-stu-id="a05e3-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="a05e3-112">Erreurs d’exécution</span><span class="sxs-lookup"><span data-stu-id="a05e3-112">Run-Time Errors</span></span>  
 <span data-ttu-id="a05e3-113">*Erreurs d’exécution* sont celles qui apparaissent uniquement une fois que vous compilez et exécutez votre code.</span><span class="sxs-lookup"><span data-stu-id="a05e3-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="a05e3-114">Elles peuvent donner lieu code semble être correcte dans la mesure où il ne comporte aucune erreur de syntaxe, mais qui ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="a05e3-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="a05e3-115">Par exemple, vous pouvez correctement écrire une ligne de code pour ouvrir un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="a05e3-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="a05e3-116">Mais si le fichier est endommagé, l’application ne peut pas mener à bien la `Open` et cesse de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="a05e3-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="a05e3-117">Vous pouvez résoudre la plupart des erreurs d’exécution en réécrivant le code erroné, puis recompiler et exécuter à nouveau.</span><span class="sxs-lookup"><span data-stu-id="a05e3-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="a05e3-118">Erreurs de logique</span><span class="sxs-lookup"><span data-stu-id="a05e3-118">Logic Errors</span></span>  
 <span data-ttu-id="a05e3-119">*Erreurs de logique* sont celles qui apparaissent lorsque l’application est en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="a05e3-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="a05e3-120">Elles sont la plupart des résultats souvent indésirables ou inattendus en réponse aux actions de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a05e3-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="a05e3-121">Par exemple, une mauvaise touche ou influence extérieure risque de votre application pour cesser de fonctionner dans les paramètres prévus ou complètement.</span><span class="sxs-lookup"><span data-stu-id="a05e3-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="a05e3-122">Erreurs de logique sont les plus difficiles à résoudre, car il n’est pas toujours évident de déterminer leur origine.</span><span class="sxs-lookup"><span data-stu-id="a05e3-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a05e3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a05e3-123">See Also</span></span>  
 [<span data-ttu-id="a05e3-124">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="a05e3-124">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="a05e3-125">Principes de base du débogueur</span><span class="sxs-lookup"><span data-stu-id="a05e3-125">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
