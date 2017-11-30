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
# <a name="decision-structures-visual-basic"></a>Structures de décision (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]vous permet de tester des conditions et d’effectuer diverses opérations selon les résultats de ce test. Vous pouvez tester une condition vraie ou fausse, plusieurs valeurs d’une expression ou plusieurs exceptions générées lorsque vous exécutez une série d’instructions.  
  
 L’illustration suivante montre une structure de décision qui teste une condition est true et prend des mesures différentes selon qu’il soit true ou false.  
  
 ![Organigramme d’une instruction If... Puis... Construction Else](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")  
Effectuer différentes actions lorsqu’une condition est true et false  
  
## <a name="ifthenelse-construction"></a>If... Puis... Construction Else  
 `If...Then...Else`constructions vous permettent de tester pour une ou plusieurs conditions et d’exécuter une ou plusieurs instructions selon chaque condition. Vous pouvez tester des conditions et prendre des mesures de plusieurs manières :  
  
-   Exécuter une ou plusieurs instructions si une condition est`True`  
  
-   Exécuter une ou plusieurs instructions si une condition est`False`  
  
-   Exécutez des instructions si une condition est `True` et d’autres si elle est`False`  
  
-   Tester une condition supplémentaire si une condition antérieure est`False`  
  
 La structure de contrôle qui offre toutes ces possibilités est le [si... Puis... Else, instruction](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Vous pouvez utiliser une version de ligne si vous avez qu’un test et une instruction à exécuter. Si vous avez un ensemble plus complexe de conditions et les actions, vous pouvez utiliser la version de plusieurs lignes.  
  
## <a name="selectcase-construction"></a>Sélectionnez... Construction de cas  
 Le `Select...Case` construction vous permet d’évaluer une expression une fois et d’exécuter différents jeux d’instructions selon différentes valeurs possibles. Pour plus d’informations, consultez [sélectionnez... Cas d’instruction](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try... Catch... Pour finir de Construction  
 `Try...Catch...Finally`constructions vous permettent d’exécuter un ensemble d’instructions sous un environnement qui conserve le contrôle si l’une de vos instructions entraîne une exception. Vous pouvez prendre des mesures différentes pour différentes exceptions. Vous pouvez éventuellement spécifier un bloc de code qui s’exécute avant de quitter l’ensemble `Try...Catch...Finally` construction, indépendamment de ce qui se produit. Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance. Par exemple, lorsque vous cliquez sur `If` dans un `If...Then...Else` construction, toutes les instances de `If`, `Then`, `ElseIf`, `Else`, et `End If` dans la construction sont mises en surbrillance. Pour déplacer vers le mot clé en surbrillance suivant ou précédent, appuyez sur CTRL + MAJ + flèche bas ou CTRL + MAJ + flèche haut.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Autres structures de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [Structures de contrôle imbriquées](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [If (opérateur)](../../../../visual-basic/language-reference/operators/if-operator.md)
