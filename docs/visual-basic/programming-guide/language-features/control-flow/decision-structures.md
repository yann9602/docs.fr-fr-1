---
title: "La décision de Structures (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement, decision structures
- If statement, If...Then...Else
- control flow, decision structures
- decision structures
- conditional statements, decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: 29
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c69b487322dc75ae8d54f42c1c62f8f5cc35757d
ms.lasthandoff: 03/13/2017

---
# <a name="decision-structures-visual-basic"></a>Structures de décision (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]vous permet de tester des conditions et d’effectuer diverses opérations selon les résultats de ce test. Vous pouvez tester une condition vraie ou fausse, plusieurs valeurs d’une expression ou plusieurs exceptions générées lorsque vous exécutez une série d’instructions.  
  
 L’illustration suivante montre une structure de décision qui teste une condition est true et exécute différentes actions selon qu’il est true ou false.  
  
 ![Organigramme d’une instruction If... Puis... Construction Else](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")  
Prendre des mesures différentes lorsqu’une condition est true et false  
  
## <a name="ifthenelse-construction"></a>If... Puis... Construction Else  
 `If...Then...Else`constructions vous permettent de tester une ou plusieurs conditions et d’exécuter une ou plusieurs instructions selon chaque condition. Vous pouvez tester des conditions et prendre des mesures de plusieurs façons :  
  
-   Exécuter une ou plusieurs instructions si une condition est`True`  
  
-   Exécuter une ou plusieurs instructions si une condition est`False`  
  
-   Exécutez des instructions si une condition est `True` et d’autres s’il s’agit`False`  
  
-   Tester une condition supplémentaire si une condition préalable`False`  
  
 La structure de contrôle qui offre toutes ces possibilités est le [si... Puis... Else, instruction](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Vous pouvez utiliser une version de ligne si vous avez qu’un test et une instruction à exécuter. Si vous avez un ensemble de conditions et actions plus complexe, vous pouvez utiliser la version multiligne.  
  
## <a name="selectcase-construction"></a>Sélectionnez... Construction de cas  
 Le `Select...Case` construction vous permet d’évaluer une expression une fois et d’exécuter différents jeux d’instructions selon différentes valeurs possibles. Pour plus d’informations, consultez [sélectionner... Instruction case](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try... Catch... Pour finir de Construction  
 `Try...Catch...Finally`constructions vous permettent d’exécuter un ensemble d’instructions sous un environnement qui conserve le contrôle si l’une de vos instructions entraîne une exception. Vous pouvez prendre des mesures différentes pour des exceptions différentes. Vous pouvez éventuellement spécifier un bloc de code qui s’exécute avant de quitter l’ensemble `Try...Catch...Finally` construction, quel que soit ce qui se produit. Pour plus d’informations, consultez [essayez... Catch... Instruction finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance. Par exemple, lorsque vous cliquez sur `If` dans un `If...Then...Else` construction, toutes les instances de `If`, `Then`, `ElseIf`, `Else`, et `End If` dans la construction sont mises en surbrillance. Pour passer au mot clé en surbrillance suivant ou précédent, appuyez sur CTRL + MAJ + BAS ou CTRL + MAJ + flèche haut.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Autres Structures de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [Structures de contrôle imbriquées](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [If (opérateur)](../../../../visual-basic/language-reference/operators/if-operator.md)
