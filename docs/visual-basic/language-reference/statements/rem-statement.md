---
title: REM, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d64ce970e3e74437f5e8c63c8a4d578900902192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="rem-statement-visual-basic"></a>REM, instruction (Visual Basic)
Permet d’inclure des notes explicatives dans le code source d’un programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Composants  
 `comment`  
 Facultatif. Le texte des commentaires que vous souhaitez inclure. Un espace est requis entre le `REM` (mot clé) et `comment`.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez placer un `REM` instruction seule sur une ligne, ou vous pouvez le placer sur une ligne qui suit une autre instruction. La `REM` instruction doit être la dernière instruction de la ligne. Si elle suit une autre instruction, la `REM` doit être séparée de cette instruction par un espace.  
  
 Vous pouvez utiliser un guillemet simple (`'`) au lieu de `REM`. Cela est vrai si votre commentaire suit une autre instruction sur la même ligne ou se situe seul sur une ligne.  
  
> [!NOTE]
>  Vous ne pouvez pas continuer une `REM` instruction à l’aide d’une séquence de continuation de ligne (`_`). Une fois qu’un commentaire commencé, le compilateur n’examine pas les caractères pour une signification particulière. Un commentaire de plusieurs lignes, utilisez un autre `REM` instruction ou un symbole de commentaire (`'`) sur chaque ligne.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la `REM` instruction, qui est utilisée pour inclure des notes explicatives dans un programme. Il montre également d’utiliser le guillemet simple (`'`) au lieu de `REM`.  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Commentaires dans le code](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [Guide pratique : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
