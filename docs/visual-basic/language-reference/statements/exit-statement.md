---
title: Exit, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2df63ecbf0605d07296e1692f18b1b015e27cd03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="exit-statement-visual-basic"></a>Exit, instruction (Visual Basic)
Quitte une procédure ou un bloc et transfère immédiatement le contrôle à l’instruction qui suit l’appel de procédure ou la définition de bloc.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>Instructions  
 `Exit Do`  
 Quitte immédiatement la `Do` boucle dans laquelle elle apparaît. L’exécution se poursuit avec l’instruction qui suit la `Loop` instruction. `Exit Do`peut être utilisé uniquement à l’intérieur d’un `Do` boucle. Lorsqu’il est utilisé dans imbriqués `Do` boucles, `Exit Do` quitte la boucle la plus profonde et transfère le contrôle au niveau d’imbrication supérieur suivant.  
  
 `Exit For`  
 Quitte immédiatement la `For` boucle dans laquelle elle apparaît. L’exécution se poursuit avec l’instruction qui suit la `Next` instruction. `Exit For`peut être utilisé uniquement à l’intérieur d’un `For`... `Next` ou `For Each`... `Next` boucle. Lorsqu’il est utilisé dans imbriqués `For` boucles, `Exit For` quitte la boucle la plus profonde et transfère le contrôle au niveau d’imbrication supérieur suivant.  
  
 `Exit Function`  
 Quitte immédiatement la `Function` procédure dans laquelle elle apparaît. L’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé le `Function` procédure. `Exit Function`peut être utilisé uniquement à l’intérieur d’un `Function` procédure.  
  
 Pour spécifier une valeur de retour, vous pouvez affecter la valeur pour le nom de fonction sur une ligne avant le `Exit Function` instruction. Pour affecter la valeur de retour et quitter la fonction en une seule instruction, vous pouvez utiliser la [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Exit Property`  
 Quitte immédiatement la `Property` procédure dans laquelle elle apparaît. L’exécution se poursuit avec l’instruction qui a appelé le `Property` procédure, autrement dit, avec l’instruction qui demande ou définit la valeur de propriété. `Exit Property`peut être utilisé uniquement à l’intérieur d’une propriété `Get` ou `Set` procédure.  
  
 Pour spécifier une valeur de retour dans une `Get` procédure, vous pouvez affecter la valeur pour le nom de fonction sur une ligne avant le `Exit Property` instruction. Pour affecter la valeur de retour et quitter le `Get` procédure dans une instruction, vous pouvez utiliser la `Return` instruction.  
  
 Dans un `Set` procédure, le `Exit Property` instruction est équivalente à la `Return` instruction.  
  
 `Exit Select`  
 Quitte immédiatement la `Select Case` bloc dans lequel elle apparaît. L’exécution se poursuit avec l’instruction qui suit la `End Select` instruction. `Exit Select`peut être utilisé uniquement à l’intérieur d’un `Select Case` instruction.  
  
 `Exit Sub`  
 Quitte immédiatement la `Sub` procédure dans laquelle elle apparaît. L’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé le `Sub` procédure. `Exit Sub`peut être utilisé uniquement à l’intérieur d’un `Sub` procédure.  
  
 Dans un `Sub` procédure, le `Exit Sub` instruction est équivalente à la `Return` instruction.  
  
 `Exit Try`  
 Quitte immédiatement la `Try` ou `Catch` bloc dans lequel elle apparaît. L’exécution se poursuit avec le `Finally` bloquer si elle existe, ou avec l’instruction qui suit la `End Try` instruction sinon. `Exit Try`peut être utilisé uniquement à l’intérieur d’un `Try` ou `Catch` bloc et pas à l’intérieur un `Finally` bloc.  
  
 `Exit While`  
 Quitte immédiatement la `While` boucle dans laquelle elle apparaît. L’exécution se poursuit avec l’instruction qui suit la `End While` instruction. `Exit While`peut être utilisé uniquement à l’intérieur d’un `While` boucle. Lorsqu’il est utilisé dans imbriqués `While` boucles, `Exit While` transfère le contrôle à la boucle qui est un niveau au-dessus de la boucle où `Exit While` se produit.  
  
## <a name="remarks"></a>Remarques  
 Ne confondez pas `Exit` instructions avec `End` instructions. `Exit`ne définit pas la fin d’une instruction.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la condition de boucle s’arrête la boucle lorsque la `index` variable est supérieure à 100. Le `If` instruction dans la boucle, toutefois, provoque la `Exit Do` instruction pour arrêter la boucle lorsque la variable d’index est supérieure à 10.  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant affecte la valeur de retour pour le nom de fonction `myFunction`, puis utilise `Exit Function` à retourner à partir de la fonction.  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md) pour affecter la valeur de retour et de quitter la fonction.  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Continue (instruction)](../../../visual-basic/language-reference/statements/continue-statement.md)  
 [Do...Loop (instruction)](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [End (instruction)](../../../visual-basic/language-reference/statements/end-statement.md)  
 [For Each...Next (instruction)](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Return (instruction)](../../../visual-basic/language-reference/statements/return-statement.md)  
 [Stop (instruction)](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
