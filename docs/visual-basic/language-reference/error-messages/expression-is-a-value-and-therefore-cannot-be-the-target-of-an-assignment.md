---
title: "Expression is a value and therefore cannot be the target of an assignment | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30068"
  - "vbc30068"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30068"
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Expression is a value and therefore cannot be the target of an assignment
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une instruction tente d'assigner une valeur à une expression.  Vous ne pouvez assigner une valeur à une variable, une propriété ou un élément de tableau accessible en écriture qu'au moment de l'exécution .  L'exemple suivant montre comment une telle erreur peut se produire.  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 Des exemples semblables pourraient s'appliquer à des propriétés et à des éléments de tableau.  
  
 **Accès indirect.** Un accès indirect via un type valeur peut également générer cette erreur.  Prenez l'exemple de code suivant qui tente de définir la valeur de <xref:System.Drawing.Point> en y accédant indirectement par le biais de <xref:System.Windows.Forms.Control.Location%2A>.  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 La dernière instruction de l'exemple précédent échoue, car elle ne fournit qu'une allocation temporaire pour la structure <xref:System.Drawing.Point> retournée par la propriété <xref:System.Windows.Forms.Control.Location%2A>.  Une structure est un type valeur, et la structure temporaire n'est pas conservée après l'exécution de l'instruction.  Le problème est résolu en déclarant et en utilisant une variable pour <xref:System.Windows.Forms.Control.Location%2A>, ce qui a pour effet de créer une allocation plus permanente pour la structure <xref:System.Drawing.Point>.  L'exemple de code suivant remplace la dernière instruction de l'exemple précédent.  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **ID d'erreur :** BC30068  
  
### Pour corriger cette erreur  
  
-   Si l'instruction assigne une valeur à une expression, remplacez l'expression par une variable, une propriété ou un élément de tableau unique accessible en écriture.  
  
-   Si l'instruction effectue un accès indirect par le biais d'un type valeur \(généralement une structure\), créez une variable pour contenir le type valeur.  
  
-   Assignez la structure appropriée \(ou autre type valeur\) à la variable.  
  
-   Utilisez la variable pour accéder à la propriété pour lui assigner une valeur.  
  
## Voir aussi  
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Troubleshooting Procedures](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)