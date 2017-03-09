---
title: "Decision Structures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "statements [Visual Basic], control flow"
  - "If statement, decision structures"
  - "If statement, If...Then...Else"
  - "control flow, decision structures"
  - "decision structures"
  - "conditional statements, decision structures"
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# Decision Structures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] vous permet de tester des conditions et d'effectuer diverses opérations selon les résultats de ce test.  Vous pouvez tester une condition vraie ou fausse, plusieurs valeurs d'une expression ou plusieurs exceptions générées lors de l'exécution d'un ensemble d'instructions.  
  
 L'illustration suivante représente une structure de décision qui recherche une condition ayant la valeur true et exécute différentes actions selon qu'elle a la valeur true ou false.  
  
 ![Organigramme d'une construction If...Then...Else](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")  
Exécution d'actions différentes selon qu'une condition a la valeur true ou false  
  
## If...Then...Else, construction  
 Les constructions `If...Then...Else` vous permettent de tester une ou plusieurs conditions et d'exécuter une ou plusieurs instructions selon chaque condition.  Vous pouvez tester des conditions et prendre des mesures de la manière suivante :  
  
-   Exécutez une ou plusieurs instructions si une condition est `True`  
  
-   Exécutez une ou plusieurs instructions si une condition est `False`  
  
-   Exécutez des instructions si une condition est `True` et d'autres si elle est `False`  
  
-   Testez une condition supplémentaire si une condition antérieure est `False`  
  
 La structure de contrôle qui offre toutes ces possibilités est [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).  Vous pouvez utiliser une version sur une ligne si vous n'avez qu'un test et qu'une instruction à exécuter.  Si vous avez un jeu plus complexe de conditions et d'actions, vous pouvez utiliser la version multiligne.  
  
## Select...Case, construction  
 La construction `Select...Case` vous permet d'évaluer une expression une fois et d'exécuter différents jeux d'instructions selon différentes valeurs possibles.  Pour plus d’informations, consultez [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## Try...Catch...Finally, construction  
 Les constructions `Try...Catch...Finally` vous permettent d'exécuter un jeu d'instructions sous un environnement qui conserve le contrôle si l'une de vos instructions entraîne une exception.  Vous pouvez prendre des mesures différentes pour des exceptions différentes.  Vous pouvez spécifier facultativement un bloc de code qui s'exécute avant de sortir la construction `Try...Catch...Finally` entière, indépendamment de ce qui se produit.  Pour plus d’informations, consultez [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance.  Par exemple, lorsque vous cliquez sur `If` dans une construction `If...Then...Else`, toutes les instances des mots clés `If`, `Then`, `ElseIf`, `Else` et  `End If` de la construction sont mises en surbrillance.  Pour passer au mot clé en surbrillance suivant ou revenir au précédent, appuyez sur CTRL\+MAJ\+FLÈCHE BAS ou CTRL\+MAJ\+FLÈCHE HAUT.  
  
## Voir aussi  
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [If Operator](../../../../visual-basic/language-reference/operators/if-operator.md)