---
title: "Comment : retourner une valeur d'une procédure (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ce7aa0942be413986cb010963753447ea18cdf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Comment : retourner une valeur d'une procédure (Visual Basic)
A `Function` procédure retourne une valeur au code appelant soit en exécutant une `Return` instruction ou en utilisant un `Exit Function` ou `End Function` instruction.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Pour retourner une valeur à l’aide de l’instruction Return  
  
1.  Placer un `Return` instruction au point où la procédure est terminée.  
  
2.  Suivez le `Return` mot clé avec une expression qui génère la valeur que vous souhaitez retourner au code appelant.  
  
3.  Vous pouvez utiliser plusieurs instructions `Return` dans la même procédure.  
  
     Les éléments suivants `Function` procédure calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle et le retourne au code appelant.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     L’exemple suivant montre un appel typique à `hypotenuse`, qui stocke la valeur retournée.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Pour retourner une valeur à l’aide de la fonction de sortie ou fin  
  
1.  Au moins un endroit dans le `Function` procédure, assignez une valeur au nom de la procédure.  
  
2.  Lorsque vous exécutez un `Exit Function` ou `End Function` instruction, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] retourne la valeur la plus récemment assignée au nom de la procédure.  
  
3.  Vous pouvez utiliser plusieurs instructions `Exit Function` dans la même procédure et combiner des instructions `Return` et `Exit Function` dans la même procédure.  
  
4.  Vous pouvez avoir qu’un seul `End Function` instruction dans un `Function` procédure.  
  
     Pour plus d’informations et un exemple, consultez « Valeur de retour » dans [Function, instruction](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Procédures Sub](./sub-procedures.md)  
 [Procédures de propriété](./property-procedures.md)  
 [Procédures d’opérateur](./operator-procedures.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Return (instruction)](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [Guide pratique : créer une procédure qui retourne une valeur](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Guide pratique : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)
