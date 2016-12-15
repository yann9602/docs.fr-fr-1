---
title: "First operand in a binary &#39;If&#39; expression must be nullable or a reference type | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33107"
  - "vbc33107"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC33107"
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# First operand in a binary &#39;If&#39; expression must be nullable or a reference type
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une expression `If` peut accepter soit deux soit trois arguments.  Lorsque vous envoyez uniquement deux arguments, le premier argument doit être un type référence ou un type Nullable.  Si le premier argument est évalué à une valeur autre que `Nothing`, sa valeur est retournée.  Si le premier argument est évalué à la valeur `Nothing`, la valeur du deuxième argument est évaluée et retournée.  
  
 Par exemple, le code suivant contient deux expressions `If`, l'une avec trois arguments et l'autre avec deux arguments.  Les expressions sont calculées et retournent la même valeur.  
  
```vb#  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 Les expressions suivantes provoquent cette erreur :  
  
```vb#  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **ID d'erreur :** BC33107  
  
### Pour corriger cette erreur  
  
-   Si vous ne pouvez pas modifier le code afin que le premier argument soit un type Nullable ou un type référence, envisagez la conversion en une expression `If` à trois arguments, ou en une instruction `If...Then...Else`.  
  
    ```vb#  
    Console.WriteLine(If(choice1 < choice2, 1, 2))  
    Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
    ```  
  
## Voir aussi  
 [If Operator](../../../visual-basic/language-reference/operators/if-operator.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)