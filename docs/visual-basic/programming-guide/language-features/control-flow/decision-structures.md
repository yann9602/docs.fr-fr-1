---
title: "Structures de décision (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38820b6ca0a8f716dcaa28644bb25eb4899bd511
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="b61df-102">Structures de décision (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b61df-102">Decision Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="b61df-103">vous permet de tester des conditions et d’effectuer diverses opérations selon les résultats de ce test.</span><span class="sxs-lookup"><span data-stu-id="b61df-103"> lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="b61df-104">Vous pouvez tester une condition vraie ou fausse, plusieurs valeurs d’une expression ou plusieurs exceptions générées lorsque vous exécutez une série d’instructions.</span><span class="sxs-lookup"><span data-stu-id="b61df-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="b61df-105">L’illustration suivante montre une structure de décision qui teste une condition est true et prend des mesures différentes selon qu’il soit true ou false.</span><span class="sxs-lookup"><span data-stu-id="b61df-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 <span data-ttu-id="b61df-106">![Organigramme d’une instruction If... Puis... Construction Else](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span><span class="sxs-lookup"><span data-stu-id="b61df-106">![Flow chart of an If...Then...Else construction](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span></span>  
<span data-ttu-id="b61df-107">Effectuer différentes actions lorsqu’une condition est true et false</span><span class="sxs-lookup"><span data-stu-id="b61df-107">Taking different actions when a condition is true and when it is false</span></span>  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="b61df-108">If... Puis... Construction Else</span><span class="sxs-lookup"><span data-stu-id="b61df-108">If...Then...Else Construction</span></span>  
 <span data-ttu-id="b61df-109">`If...Then...Else`constructions vous permettent de tester pour une ou plusieurs conditions et d’exécuter une ou plusieurs instructions selon chaque condition.</span><span class="sxs-lookup"><span data-stu-id="b61df-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="b61df-110">Vous pouvez tester des conditions et prendre des mesures de plusieurs manières :</span><span class="sxs-lookup"><span data-stu-id="b61df-110">You can test conditions and take actions in the following ways:</span></span>  
  
-   <span data-ttu-id="b61df-111">Exécuter une ou plusieurs instructions si une condition est`True`</span><span class="sxs-lookup"><span data-stu-id="b61df-111">Run one or more statements if a condition is `True`</span></span>  
  
-   <span data-ttu-id="b61df-112">Exécuter une ou plusieurs instructions si une condition est`False`</span><span class="sxs-lookup"><span data-stu-id="b61df-112">Run one or more statements if a condition is `False`</span></span>  
  
-   <span data-ttu-id="b61df-113">Exécutez des instructions si une condition est `True` et d’autres si elle est`False`</span><span class="sxs-lookup"><span data-stu-id="b61df-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
-   <span data-ttu-id="b61df-114">Tester une condition supplémentaire si une condition antérieure est`False`</span><span class="sxs-lookup"><span data-stu-id="b61df-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="b61df-115">La structure de contrôle qui offre toutes ces possibilités est le [si... Puis... Else, instruction](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b61df-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="b61df-116">Vous pouvez utiliser une version de ligne si vous avez qu’un test et une instruction à exécuter.</span><span class="sxs-lookup"><span data-stu-id="b61df-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="b61df-117">Si vous avez un ensemble plus complexe de conditions et les actions, vous pouvez utiliser la version de plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="b61df-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="b61df-118">Sélectionnez... Construction de cas</span><span class="sxs-lookup"><span data-stu-id="b61df-118">Select...Case Construction</span></span>  
 <span data-ttu-id="b61df-119">Le `Select...Case` construction vous permet d’évaluer une expression une fois et d’exécuter différents jeux d’instructions selon différentes valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="b61df-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="b61df-120">Pour plus d’informations, consultez [sélectionnez... Cas d’instruction](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b61df-120">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="b61df-121">Try... Catch... Pour finir de Construction</span><span class="sxs-lookup"><span data-stu-id="b61df-121">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="b61df-122">`Try...Catch...Finally`constructions vous permettent d’exécuter un ensemble d’instructions sous un environnement qui conserve le contrôle si l’une de vos instructions entraîne une exception.</span><span class="sxs-lookup"><span data-stu-id="b61df-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="b61df-123">Vous pouvez prendre des mesures différentes pour différentes exceptions.</span><span class="sxs-lookup"><span data-stu-id="b61df-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="b61df-124">Vous pouvez éventuellement spécifier un bloc de code qui s’exécute avant de quitter l’ensemble `Try...Catch...Finally` construction, indépendamment de ce qui se produit.</span><span class="sxs-lookup"><span data-stu-id="b61df-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="b61df-125">Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b61df-125">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b61df-126">Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="b61df-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="b61df-127">Par exemple, lorsque vous cliquez sur `If` dans un `If...Then...Else` construction, toutes les instances de `If`, `Then`, `ElseIf`, `Else`, et `End If` dans la construction sont mises en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="b61df-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="b61df-128">Pour déplacer vers le mot clé en surbrillance suivant ou précédent, appuyez sur CTRL + MAJ + flèche bas ou CTRL + MAJ + flèche haut.</span><span class="sxs-lookup"><span data-stu-id="b61df-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b61df-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b61df-129">See Also</span></span>  
 [<span data-ttu-id="b61df-130">Flux de contrôle</span><span class="sxs-lookup"><span data-stu-id="b61df-130">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="b61df-131">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="b61df-131">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="b61df-132">Autres structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="b61df-132">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="b61df-133">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="b61df-133">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="b61df-134">If (opérateur)</span><span class="sxs-lookup"><span data-stu-id="b61df-134">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
