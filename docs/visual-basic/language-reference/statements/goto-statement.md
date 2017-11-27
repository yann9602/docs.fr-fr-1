---
title: GoTo, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22a6315e69cd6c797d462d0835e85bb1dde67dcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="goto-statement"></a>GoTo, instruction
Crée une branche inconditionnelle vers une ligne spécifiée d’une procédure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Élément  
 `line`  
 Obligatoire. Toute étiquette de ligne.  
  
## <a name="remarks"></a>Remarques  
 La `GoTo` instruction peut créer une branche que vers des lignes dans la procédure dans laquelle elle apparaît. La ligne doit avoir une ligne d’étiquette qui `GoTo` peuvent faire référence. Pour plus d’informations, consultez [Comment : instructions de l’étiquette](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
>  `GoTo`instructions peuvent rendre le code difficile à lire et mettre à jour. Si possible, utilisez une structure de contrôle à la place. Pour plus d’informations, consultez [flux de contrôle](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Vous ne pouvez pas utiliser un `GoTo` instruction branchement depuis l’extérieur un `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, ou `Using`... `End Using` vers une étiquette à l’intérieur.  
  
## <a name="branching-and-try-constructions"></a>Création de branche et Constructions Try  
 Dans un `Try`... `Catch`... `Finally` construction, les règles suivantes s’appliquent à la création de branche avec la `GoTo` instruction.  
  
|Bloc ou région|Création de branche à partir d’à l’extérieur|Création de branche à partir d’à l’intérieur|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`bloc|Uniquement à partir d’un `Catch` bloc de la même construction <sup>1</sup>|Uniquement en dehors de la construction entière|  
|`Catch`bloc|Jamais autorisé|Uniquement en dehors de la construction entière, ou à la `Try` bloc de la même construction <sup>1</sup>|  
|`Finally`bloc|Jamais autorisé|Jamais autorisé|  
  
 <sup>1</sup> si un `Try`... `Catch`... `Finally` est imbriquée dans une autre, un `Catch` bloc peut créer de branche dans le `Try` bloc à son propre niveau d’imbrication, mais pas vers un autre `Try` bloc. Imbriquée `Try`... `Catch`... `Finally` construction doit être entièrement contenue dans un `Try` ou `Catch` bloc de la construction dans laquelle elle est imbriquée.  
  
 L’illustration suivante montre une `Try` imbriquée dans une autre. Les diverses branches entre les blocs des deux constructions sont indiquées comme valide ou non valide.  
  
 ![Diagramme graphique de branchement dans des constructions Try](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")  
Branches correctes et incorrectes dans les constructions Try  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `GoTo` instruction pour les étiquettes de ligne dans une procédure.  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Do...Loop (instruction)](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [For Each...Next (instruction)](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [If...Then...Else (instruction)](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Select...Case (instruction)](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [With...End With (instruction)](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
