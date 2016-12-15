---
title: "Proc&#233;dures Function (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "procédures Function"
  - "valeurs de retour, procédures function"
  - "code Visual Basic, procédures"
  - "procédures, appeler"
  - "procédures, procédures Function"
  - "syntaxe, procédures Function"
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Proc&#233;dures Function (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Une procédure `Function` est une série d'instructions [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] délimitées par les instructions `Function` et `End Function`.  La procédure `Function` effectue une tâche puis retourne le contrôle au code appelant.  Lorsqu'elle retourne le contrôle, elle retourne également une valeur au code appelant.  
  
 Chaque fois que la procédure est appelée, ses instructions sont exécutées à partir de la première instruction exécutable située après l'instruction `Function` jusqu'à la première instruction `End Function`, `Exit Function` ou `Return` rencontrée.  
  
 Vous pouvez définir une procédure `Function` dans un module, une classe ou une structure.  La valeur par défaut est `Public`, ce qui signifie que vous pouvez l'appeler de n'importe où dans une application qui a accès au module, à la classe ou à la structure dans laquelle vous l'avez définie.  
  
 Une procédure `Function` peut accepter des arguments tels que les constantes, les variables ou les expressions qui sont passées à la procédure par le code appelant.  
  
## Syntaxe de déclaration  
 La syntaxe de déclaration d'une procédure `Function` est la suivante :  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 Les *modificateurs* peuvent spécifier un niveau d'accès et des informations relatives à la surcharge, la substitution, le partage et l'occultation.  Pour plus d'informations, consultez [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Vous déclarez chaque paramètre de la même façon que pour [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md).  
  
### Type de données  
 Chaque procédure `Function` possède un type de données, comme n'importe quelle variable.  Ce type de données est spécifié par la clause `As` dans l'instruction `Function` et il détermine le type de données de la valeur que la fonction retourne au code appelant.  Les exemples de déclarations suivants illustrent ce principe.  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 Pour plus d'informations, consultez « Éléments » dans [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## Retour de valeurs  
 La valeur qu'une procédure d' `Function` envoie vers le code appelant est appelée sa valeur de retour.  La procédure retourne cette valeur selon l'une des deux méthodes suivantes :  
  
-   Il utilise l'instruction `Return` pour spécifier la valeur de retour et retourne immédiatement le contrôle au programme appelant.  L'exemple suivant illustre ce comportement.  
  
    ```vb  
    Function FunctionName [(ParameterList)] As ReturnType  
        ' The following statement immediately transfers control back  
        ' to the calling code and returns the value of Expression.  
        Return Expression  
    End Function  
    ```  
  
-   Elle assigne une valeur à son nom de fonction dans une ou plusieurs instructions de la procédure.  Le contrôle ne retourne pas au programme appelant tant qu'une instruction `Exit Function` ou `End Function` n'a pas été exécutée.  L'exemple suivant illustre ce comportement.  
  
    ```vb  
    Function FunctionName [(ParameterList)] As ReturnType  
        ‘ The following statement does not transfer control back to the calling code.  
        FunctionName = Expression  
        ' When control returns to the calling code, Expression is the return value.  
    End Function  
    ```  
  
 L'assignation de la valeur de retour au nom de la fonction permet à la procédure de conserver le contrôle jusqu'à ce que celui\-ci rencontre une instruction `Exit Function` ou `End Function`.  Vous pouvez ainsi assigner une valeur préliminaire et l'ajuster ultérieurement si nécessaire.  
  
 Pour plus d'informations sur le retour des valeurs, consultez [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).  Pour plus d'informations sur le retour des tableaux, consultez l' [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## Syntaxe d'appel  
 Vous appelez une procédure `Function` en incluant son nom et ses arguments soit à droite d'une instruction d'assignation soit dans une expression.  Vous devez fournir les valeurs de tous les arguments qui ne sont pas facultatifs et mettre la liste des arguments entre parenthèses.  Si aucun argument n'est spécifié, vous pouvez ne pas mettre les parenthèses.  
  
 La syntaxe d'appel à une procédure `Function` est la suivante :  
  
 *l\-value*  `=` *functionname* `[(` *argumentlist* `)]`  
  
 `If ((` *functionname* `[(` *argumentlist* `)] / 3) <=` *expression* `) Then`  
  
 Lorsque vous appelez une procédure `Function`, vous n'avez pas besoin d'utiliser sa valeur de retour.  Si vous ne l'utilisez pas, toutes les actions de la fonction sont exécutées, mais la valeur de retour est ignorée.  La méthode <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> est souvent appelée de cette manière.  
  
### Illustration de déclaration et d'appel  
 La procédure `Function` suivante calcule le côté le plus long, ou hypoténuse, d'un triangle rectangle, d'après les valeurs des deux autres côtés.  
  
 [!code-vb[VbVbcnProcedures#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 L'exemple suivant montre un appel typique à `hypotenuse`.  
  
 [!code-vb[VbVbcnProcedures#6](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [How to: Create a Procedure that Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure-that-returns-a-value.md)   
 [How to: Return a Value from a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-return-a-value-from-a-procedure.md)   
 [How to: Call a Procedure That Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)