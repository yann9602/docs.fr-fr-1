---
title: "Comment : retourner une valeur d’une procédure (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- procedures, returning from
- procedures, returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 98f0fb0740a021a16e87454bfaebbfad7858477c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Comment : retourner une valeur d'une procédure (Visual Basic)
A `Function` procédure retourne une valeur au code appelant soit en exécutant une `Return` instruction ou en utilisant un `Exit Function` ou `End Function` instruction.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Pour retourner une valeur à l’aide de l’instruction Return  
  
1.  Placer un `Return` instruction au point où la tâche de la procédure est terminée.  
  
2.  Suivez le `Return` mot clé avec une expression qui retourne la valeur que vous souhaitez retourner au code appelant.  
  
3.  Vous pouvez avoir plusieurs `Return` instruction dans la même procédure.  
  
     Les éléments suivants `Function` procédure calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle et le retourne au code appelant.  
  
     [!code-vb[VbVbcnProcedures n °&1;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     L’exemple suivant montre un appel typique à `hypotenuse`, qui stocke la valeur retournée.  
  
     [!code-vb[VbVbcnProcedures n °&6;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Pour retourner une valeur à l’aide de la fonction de sortie ou fin  
  
1.  Au moins un endroit dans le `Function` procédure, assignez une valeur au nom de la procédure.  
  
2.  Lorsque vous exécutez un `Exit Function` ou `End Function` instruction, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] renvoie la valeur la plus récemment assignée au nom de la procédure.  
  
3.  Vous pouvez avoir plusieurs `Exit Function` instruction dans la même procédure et vous pouvez mélanger `Return` et `Exit Function` instructions dans la même procédure.  
  
4.  Vous pouvez avoir un seul `End Function` instruction dans un `Function` procédure.  
  
     Pour plus d’informations et un exemple, consultez « Valeur de retour » dans [Function, instruction](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Procédures Sub](./sub-procedures.md)   
 [Procédures de propriété](./property-procedures.md)   
 [Procédures d’opérateur](./operator-procedures.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Return (instruction)](../../../../visual-basic/language-reference/statements/return-statement.md)   
 [Comment : créer une procédure qui retourne une valeur](./how-to-create-a-procedure-that-returns-a-value.md)   
 [Guide pratique : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)
