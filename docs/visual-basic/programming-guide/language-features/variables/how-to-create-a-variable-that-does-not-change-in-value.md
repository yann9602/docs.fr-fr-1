---
title: "Comment : créer une variable qui ne change pas de valeur (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1475553e64fef92ec3f3bb7e1b4fbfb357dbec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Comment : créer une variable qui ne change pas de valeur (Visual Basic)
La notion d’une variable qui ne modifie pas sa valeur peut sembler être contradictoires. Mais il existe des situations lorsqu’une constante n’est pas possible et il est utile de disposer d’une variable avec une valeur fixe. Dans ce cas, vous pouvez définir une variable membre avec le [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) (mot clé).  
  
 Vous ne pouvez pas utiliser le [instruction Const](../../../../visual-basic/language-reference/statements/const-statement.md) pour déclarer et assigner une valeur de constante dans les circonstances suivantes :  
  
-   La `Const` instruction n’accepte pas le type de données que vous souhaitez utiliser  
  
-   Vous ne connaissez pas la valeur au moment de la compilation  
  
-   Vous ne parvenez pas à calculer la valeur constante au moment de la compilation  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Pour créer une variable qui ne change pas de valeur  
  
1.  Au niveau du module, déclarez une variable membre avec le [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md)et incluent le [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) (mot clé).  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     Vous pouvez spécifier `ReadOnly` uniquement sur une variable membre. Cela signifie que vous devez définir la variable au niveau du module, en dehors de toute procédure.  
  
2.  Si vous pouvez calculer la valeur dans une seule instruction au moment de la compilation, utilisez une clause d’initialisation dans le `Dim` instruction. Suivez les [en tant que](../../../../visual-basic/language-reference/statements/as-clause.md) clause avec un signe égal (`=`), suivi d’une expression. Assurez-vous que le compilateur peut évaluer cette expression à une valeur constante.  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     Vous pouvez affecter une valeur à une `ReadOnly` variable une seule fois. Une fois que vous procédez ainsi, aucun code n’est susceptible de changer sa valeur.  
  
     Si vous ne connaissez pas la valeur au moment de la compilation, ou ne peut pas calculer au moment de la compilation dans une seule instruction, vous pouvez l’affecter au moment de l’exécution dans un constructeur. Pour ce faire, vous devez déclarer le `ReadOnly` variable au niveau de la classe ou structure. Dans le constructeur de cette classe ou structure, calculer la valeur fixe de la variable et affecter à la variable avant de retourner à partir du constructeur.  
  
## <a name="see-also"></a>Voir aussi  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Const (instruction)](../../../../visual-basic/language-reference/statements/const-statement.md)
