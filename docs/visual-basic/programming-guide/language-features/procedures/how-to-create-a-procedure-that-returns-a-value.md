---
title: "Comment : créer une procédure qui retourne une valeur (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 787eddc1fd1cdb9dd6b655a8556b75044b2a49dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Comment : créer une procédure qui retourne une valeur (Visual Basic)
Vous utilisez un `Function` procédure pour retourner une valeur au code appelant.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Pour créer une procédure qui retourne une valeur  
  
1.  En dehors de toute autre procédure, utilisez un `Function` instruction, suivie d’une `End Function` instruction.  
  
2.  Dans le `Function` instruction, suivez le `Function` mot clé avec le nom de la procédure, puis la liste de paramètres entre parenthèses.  
  
3.  Suivez les parenthèses d’une `As` clause pour spécifier le type de données de la valeur retournée.  
  
4.  Placez les instructions de code de la procédure entre le `Function` et `End Function` instructions.  
  
5.  Utilisez un `Return` instruction pour retourner la valeur au code appelant.  
  
     Les éléments suivants `Function` procédure calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, selon les valeurs des deux autres côtés.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     L’exemple suivant montre un appel typique à `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Procédures Sub](./sub-procedures.md)  
 [Procédures de propriété](./property-procedures.md)  
 [Procédures d’opérateur](./operator-procedures.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Guide pratique : retourner une valeur d’une procédure](./how-to-return-a-value-from-a-procedure.md)  
 [Guide pratique : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)
