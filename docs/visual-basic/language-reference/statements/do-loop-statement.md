---
title: Do...Loop, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- "conditional statements [Visual Basic], Do�Loop"
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- "loop structures [Visual Basic], Do�Loop statements"
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79d25dce963f383a84b56ce2c9b600fc2d5a7937
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop, instruction (Visual Basic)
Répète un bloc d’instructions tant qu’une `Boolean` condition est `True` ou jusqu'à ce que la condition devienne `True`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`Do`|Obligatoire. Démarre la définition de la `Do` boucle.|  
|`While`|Requis, sauf si l'option `Until` est utilisée. Répétez la boucle jusqu'à ce que `condition` est `False`.|  
|`Until`|Requis, sauf si l'option `While` est utilisée. Répétez la boucle jusqu'à ce que `condition` est `True`.|  
|`condition`|Facultatif. `Boolean`expression. Si `condition` est `Nothing`, Visual Basic traite en tant que `False`.|  
|`statements`|Facultatif. Une ou plusieurs instructions répétées lors, ou en tant que `condition` est `True`.|  
|`Continue Do`|Facultatif. Transfère le contrôle à l’itération suivante de la `Do` boucle.|  
|`Exit Do`|Facultatif. Transfère le contrôle de le `Do` boucle.|  
|`Loop`|Obligatoire. Termine la définition de la `Do` boucle.|  
  
## <a name="remarks"></a>Remarques  
 Utilisez un `Do...Loop` structure lorsque vous souhaitez répéter un ensemble d’instructions un nombre indéfini de fois, jusqu'à ce qu’une condition est satisfaite. Si vous souhaitez répéter les instructions un nombre défini de fois, le [pour... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) est généralement un meilleur choix.  
  
 Vous pouvez utiliser `While` ou `Until` pour spécifier `condition`, mais pas les deux.  
  
 Vous pouvez tester `condition` qu’une seule fois, au début ou à la fin de la boucle. Si vous testez `condition` au début de la boucle (dans la `Do` instruction), la boucle ne peut pas s’exécuter même une seule fois. Si vous testez à la fin de la boucle (dans la `Loop` instruction), la boucle s’exécute toujours au moins une fois.  
  
 La condition généralement le résultat d’une comparaison de deux valeurs, mais il peut être toute expression qui correspond à un [Type de données booléen](../../../visual-basic/language-reference/data-types/boolean-data-type.md) valeur (`True` ou `False`). Cela inclut les valeurs des autres types de données, tels que des types numériques, qui ont été convertis en `Boolean`.  
  
 Vous pouvez imbriquer `Do` boucles en plaçant une boucle à l’intérieur d’une autre. Vous pouvez également imbriquer des différents types de structures de contrôle dans d’autres. Pour plus d’informations, consultez [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  Le `Do...Loop` structure vous donne davantage de flexibilité que la [tandis que... Alors que l’instruction End](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , car il vous permet de décider s’il faut mettre fin à la boucle lorsque `condition` cesse d’être `True` ou lorsqu’il redevient `True`. Il vous permet également de tester `condition` au début ou à la fin de la boucle.  
  
## <a name="exit-do"></a>Exit Do  
 Le [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) instruction peut fournir une autre façon de quitter une `Do…Loop`. `Exit Do`transfère le contrôle à l’instruction qui suit immédiatement la `Loop` instruction.  
  
 `Exit Do`est souvent utilisé après une condition est évaluée, par exemple dans un `If...Then...Else` structure. Vous souhaiterez peut-être quitter une boucle si vous détectez une condition qui rend inutile ou impossible pour poursuivre l’itération, telle qu’une valeur erronée ou une demande d’arrêt. Une des utilisations de `Exit Do` pour tester une condition qui provoquerait une *boucle sans fin*, qui est une boucle qui pourrait exécuter un importantes ou infini même le nombre de fois. Vous pouvez utiliser `Exit Do` pour abandonner la boucle.  
  
 Vous pouvez inclure un nombre quelconque de `Exit Do` instructions n’importe où dans un `Do…Loop`.  
  
 Lorsqu’il est utilisé dans imbriqués `Do` boucles, `Exit Do` transfère le contrôle hors de la boucle la plus profonde et dans le niveau d’imbrication supérieur suivant.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les instructions de la boucle continuent à s’exécuter jusqu'à ce que le `index` variable est supérieure à 10. Le `Until` clause est à la fin de la boucle.  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un `While` clause au lieu d’un `Until` clause, et `condition` est testée au début de la boucle plutôt qu’à la fin.  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, `condition` interrompt la boucle lorsque la `index` variable est supérieure à 100. Le `If` instruction dans la boucle, toutefois, provoque la `Exit Do` instruction pour arrêter la boucle lorsque la variable d’index est supérieure à 10.  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant lit toutes les lignes dans un fichier texte. Le <xref:System.IO.File.OpenText%2A> méthode ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères. Dans le `Do...Loop` condition, le <xref:System.IO.StreamReader.Peek%2A> méthode de la `StreamReader` détermine s’il existe des caractères supplémentaires.  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de boucle](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Booléen (type de données)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
