---
title: "How to: Move Data Into and Out of a Variable (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], retrieving values"
  - "variables [Visual Basic], storing data"
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Move Data Into and Out of a Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez stocker une valeur dans une variable en plaçant le nom de la variable sur le côté gauche d'une instruction d'assignation.  
  
## Placement de données dans une variable  
  
#### Pour stocker une valeur dans une variable  
  
-   Spécifiez le nom de variable sur le côté gauche d'une instruction d'assignation.  
  
     L'exemple suivant définit la valeur de la variable `alpha`.  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     La valeur générée du côté droit de l'instruction d'assignation est stockée dans la variable.  
  
## Obtention de données à partir d'une variable  
 Vous pouvez récupérer la valeur d'une variable en incluant le nom de variable dans une expression.  
  
#### Pour récupérer une valeur à partir d'une variable  
  
-   Spécifiez le nom de variable dans une expression.  Vous pouvez utiliser une variable aux mêmes emplacements qu'une constante ou un littéral, sauf dans une expression qui définit la valeur d'une constante.  
  
     ou  
  
-   Spécifiez le nom de variable après le signe égal \(`=`\) dans une instruction d'assignation.  
  
     L'exemple suivant lit la valeur de la variable `startValue`, puis utilise la valeur de la variable `counter` dans une expression.  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     La valeur de la variable participe à l'expression comme le ferait une constante, puis elle est stockée dans la variable ou la propriété située sur le côté gauche de l'instruction d'assignation.  
  
## Voir aussi  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)