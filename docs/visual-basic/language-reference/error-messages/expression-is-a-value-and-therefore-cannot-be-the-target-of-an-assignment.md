---
title: "Cette expression est une valeur et ne peut donc pas être la cible d'une assignation"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords: BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bec3e2d298160bd0b459dc3b7ef93b94648e439a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Cette expression est une valeur et ne peut donc pas être la cible d'une assignation
Une instruction tente d’assigner une valeur à une expression. Vous pouvez affecter une valeur uniquement à une variable accessible en écriture, une propriété ou un élément de tableau en cours d’exécution. L’exemple suivant illustre la manière dont cette erreur peut se produire.  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 Des exemples similaires pourraient s’appliquent aux propriétés et aux éléments du tableau.  
  
 **Accès indirect.** Un accès indirect via un type valeur peut également générer cette erreur. Prenons l’exemple de code suivant, qui tente de définir la valeur de <xref:System.Drawing.Point> en accédant à indirectement via <xref:System.Windows.Forms.Control.Location%2A>.  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 La dernière instruction de l’exemple précédent échoue, car elle crée uniquement une allocation temporaire pour la <xref:System.Drawing.Point> structure retournée par le <xref:System.Windows.Forms.Control.Location%2A> propriété. Une structure est un type valeur, et la structure temporaire n’est pas conservée après l’exécution de l’instruction. Le problème est résolu en déclarant et en utilisant une variable pour <xref:System.Windows.Forms.Control.Location%2A>, ce qui crée une allocation plus permanente pour le <xref:System.Drawing.Point> structure. L’exemple suivant montre le code de remplace la dernière instruction de l’exemple précédent.  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **ID d’erreur :** BC30068  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si l’instruction assigne une valeur à une expression, remplacez l’expression par une variable accessible en écriture seule, une propriété ou un élément de tableau.  
  
-   Si l’instruction effectue un accès indirect via un type valeur (généralement une structure), créez une variable pour stocker le type de valeur.  
  
-   Affecter la structure appropriée (ou autre type de valeur) à la variable.  
  
-   Utilisez la variable pour accéder à la propriété pour lui attribuer une valeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Procédures de dépannage](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
