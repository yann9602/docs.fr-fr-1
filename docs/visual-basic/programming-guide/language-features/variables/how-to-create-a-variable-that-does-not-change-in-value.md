---
title: "How to: Create a Variable that Does Not Change in Value (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], read-only"
  - "variables [Visual Basic], constant value"
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create a Variable that Does Not Change in Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

La notion de variable qui ne change pas de valeur peut sembler contradictoire.  Toutefois, il peut arriver qu'une constante ne soit pas possible et il est alors utile d'avoir une variable avec une valeur fixe.  Dans une telle situation, vous pouvez définir une variable membre avec le mot clé [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Vous ne pouvez pas utiliser [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) pour déclarer et assigner une valeur de constante dans les circonstances suivantes :  
  
-   L'instruction `Const` n'accepte pas le type de données que vous souhaitez utiliser.  
  
-   Vous ne connaissez pas la valeur au moment de la compilation.  
  
-   Vous êtes incapable de calculer la valeur de constante au moment de la compilation.  
  
### Pour créer une variable qui ne change pas de valeur  
  
1.  Au niveau du module, déclarez une variable membre avec [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) et incluez le mot clé [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md).  
  
    ```  
  
    Dim ReadOnly timeStarted  
    ```  
  
     Vous pouvez spécifier `ReadOnly` uniquement sur une variable membre.  Cela signifie que vous devez définir la variable au niveau du module, en dehors de toute procédure.  
  
2.  Si vous pouvez calculer la valeur dans une seule instruction au moment de la compilation, utilisez une clause d'initialisation dans l'instruction `Dim`.  Faites suivre la clause [As](../../../../visual-basic/language-reference/statements/as-clause.md) d'un signe égal \(`=`\), suivi d'une expression.  Assurez\-vous que le compilateur peut évaluer cette expression à une valeur de constante.  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     Vous pouvez assigner une valeur à une variable `ReadOnly` une seule fois.  Après cette opération, aucun code ne peut jamais modifier sa valeur.  
  
     Si vous ne connaissez pas la valeur au moment de la compilation ou si vous ne pouvez pas la calculer au moment de la compilation dans une seule instruction, vous pouvez toujours l'assigner au moment de l'exécution dans un constructeur.  Pour ce faire, vous devez déclarer la variable `ReadOnly` au niveau de la classe ou de la structure.  Dans le constructeur pour cette classe ou cette structure, calculez la valeur fixe de la variable et assignez\-la à la variable avant de quitter le constructeur.  
  
## Voir aussi  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)