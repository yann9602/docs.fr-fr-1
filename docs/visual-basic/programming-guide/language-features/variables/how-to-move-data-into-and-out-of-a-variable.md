---
title: "Comment : placer des données dans et en dehors d'une variable (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fefb1979e35cd7b5fa1917f8f1a57af575e51234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Comment : placer des données dans et en dehors d'une variable (Visual Basic)
Vous stockez une valeur dans une variable en plaçant le nom de variable sur le côté gauche d’une instruction d’assignation.  
  
## <a name="putting-data-in-a-variable"></a>Placer des données dans une Variable  
  
#### <a name="to-store-a-value-in-a-variable"></a>Pour stocker une valeur dans une variable  
  
-   Utilisez le nom de variable sur le côté gauche d’une instruction d’assignation.  
  
     L’exemple suivant définit la valeur de la variable `alpha`.  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     La valeur générée sur le côté droit de l’instruction d’assignation est stockée dans la variable.  
  
## <a name="getting-data-from-a-variable"></a>Obtention de données à partir d’une Variable  
 Vous récupérez la valeur d’une variable en incluant le nom de variable dans une expression.  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>Pour récupérer une valeur d’une variable  
  
-   Utilisez le nom de variable dans une expression. Vous pouvez utiliser une variable de n’importe où vous pouvez utiliser une constante ou un littéral, sauf dans une expression qui définit la valeur d’une constante.  
  
     ou  
  
-   Utilisez le nom de variable suivant égaux (`=`) connectez-vous à une instruction d’assignation.  
  
     L’exemple suivant lit la valeur de la variable `startValue` , puis utilise la valeur de la variable `counter` dans une expression.  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     La valeur de la variable participe à l’expression comme une constante serait, puis il est stocké dans la variable ou propriété sur le côté gauche de l’instruction d’assignation.  
  
## <a name="see-also"></a>Voir aussi  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
